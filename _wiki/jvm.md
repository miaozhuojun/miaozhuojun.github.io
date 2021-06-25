---
layout: wiki
title: JVM
categories: JVM
description: JVM 相关
keywords: JVM，jtreg, 调测，选项
---

## 运行时选项

### 纯解释执行

```
-Xint
```

### `PrintCompilation`选项

请参考 [About PrintComiplation](https://link.zhihu.com/?target=https%3A//gist.github.com/rednaxelafx/1165804%23file-notes-md)

### `PrintAssembly`选项

请参考 [PrintAssembly](https://wiki.openjdk.java.net/display/HotSpot/PrintAssembly)

### `CompileCommand`选项

可以控制JVM编译指定的函数：
```
-XX:CompileCommand=compileonly,<ClassName>.<function|*>
```

### `PrintInlining`选项

查看函数 inline 情况

### `PrintIntrinsics`选项

打印调用 intrinsic 情况

### `TieredStopAtLevel=1`选项

不开启C2编译

## 编译 JDK

- 构建可调试版本

  ```shell
  bash ./configure --with-debug-level=fastdebug --with-native-debug-symbols=internal
  make images CONF=fastdebug
  ```

- 指定安装目录

  ```shell
  ./configure --prefix=<path to install>
  make install
  ```

- 编译时忽略告警错误

  `--disable-warnings-as-errors`

## 基本测试

- 在 configure 前指 jtreg

  设置环境变量 JT_HOME 为 jtreg 的安装路径

- 执行测试

  ```shell
  make test TEST="tier1"
  ```

## JVM 字节码

- 字节码指令手册

  [Chapter 6. The Java Virtual Machine Instruction Set](https://docs.oracle.com/javase/specs/jvms/se8/html/jvms-6.html)

## JVM 内存相关选项

- -Xms<xxxk/m/g>
  表示 JVM 初始化时堆的大小。

- -Xmx<xxxk/m/g>
  表示 JVM 堆可以分配到的最大值。

- -Xmn<xxxk/m/g>
  表示 JVM 堆区新生代的大小

## Jtreg 选项参考

[jtreg: Command Line Options](http://openjdk.java.net/jtreg/command-help.html)

## 打印JIT生成汇编指令

- 使用hsdis解析机器指令到汇编指令

  `cp ~/share/hsdis/hsdis-aarch64.so ../jdk/build/linux-aarch64-server-fastdebug/images/jdk/lib/server/`
  
- 开启JVM选项打印汇编指令

  `-XX:CompileCommand=print,java/lang/String.equals` or `-XX:+UnlockDiagnosticVMOptions -XX:+PrintAssembly -XX:+PrintOptoAssembly`
  
## Java字符串

Java 9 的 String，引入了类似 Python str 的压缩功能。原理很简单，如果 String 只包含 Latin1 字符，1 字节存一个字符够用了，如果 String 含有中文，那么就换一种编码方式存储，一般一个字符存储两个字节。定义如下：

```java
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {

    /**
     * The value is used for character storage.
     *
     * @implNote This field is trusted by the VM, and is a subject to
     * constant folding if String instance is constant. Overwriting this
     * field after construction will cause problems.
     *
     * Additionally, it is marked with {@link Stable} to trust the contents
     * of the array. No other facility in JDK provides this functionality (yet).
     * {@link Stable} is safe here, because value is never null.
     */
    @Stable
    private final byte[] value;

    /**
     * The identifier of the encoding used to encode the bytes in
     * {@code value}. The supported values in this implementation are
     *
     * LATIN1
     * UTF16
     *
     * @implNote This field is trusted by the VM, and is a subject to
     * constant folding if String instance is constant. Overwriting this
     * field after construction will cause problems.
     */
    private final byte coder;

    /** Cache the hash code for the string */
    private int hash; // Default to 0
}

final class StringLatin1 {
}

final class StringUTF16 {
}
```

字符序列存储在字节数组 value 中，然后用一个字节的 coder 表示编码，这是 String 的基本构成。然后 StringLatin1 提供一组静态方法，用来处理只含有 Latin1 字符时的情况。相应的 StringUTF16 提供另一组静态方法，处理包含 Latin1 以外字符时的情况。

注意类的定义，三个类都是 final，且只有 String 有 public 修饰，所以我们作为 JDK 的用户，只能使用 String，而不能使用 StringLatin1 或者 StringUTF16，这两个类不属于 API，属于实现细节，我们既不能使用，也不能依赖其内部实现。但是我们应该理解它，顺从它，避免做出违背它的事情来。

该特性由 +XX:-CompactStrings 提供。

## IGV

为了方便查看字节码编译到本地指令过程中程序的中间表示（IR），使用JDK官方的可视化工具 IdealGraph 可以展示每一步优化后的 IR。使用下面命令生成 IGV 数据：

`build/linux-aarch64-server-slowdebug/images/jdk/bin/java --add-modules=jdk.incubator.vector -XX:PrintIdealGraphLevel=1 -XX:PrintIdealGraphFile=b2i.xml -XX:CompileCommand=compileonly,TestCastB2XNode.* TestCastB2XNode`

## 更新针对新指令的 gtest 测试用例

`python test/hotspot/gtest/aarch64/aarch64-asmtest.py | expand > test/hotspot/gtest/aarch64/asmtest.out.h`

## 新的 instanceOf 操作符

传统上，我们用 Java 写程序判断一个对象是否属于某个类，如果是的话就做 cast 转换会写如下代码：

```java
if (animal instanceof Cat) {
    Cat cat = (Cat) animal;
    cat.meow();
   // other cat operations
} else if (animal instanceof Dog) {
    Dog dog = (Dog) animal;
    dog.woof();
    // other dog operations
}
```

这样的代码冗长且容易出错。在 Java 14 中引入了一种新的语法解决了这个问题：

```java
if (animal instanceof Cat cat) {
    cat.meow();
} else if(animal instanceof Dog dog) {
    dog.woof();
}
```

