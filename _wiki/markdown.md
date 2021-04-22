---
layout: wiki
title: markdown
categories: markdown
description: markdown
keywords: markdown
mathjax: true
mermaid: true
---

## 代码插入

- 单行代码

  ```markdown
  `code`
  ```

- 多行代码

  ~~~markdown
  ```『支持的语言』
  code
  ```
  ~~~

  ~~~markdown
  ``` "支持的语言"
  code
  ```
  ~~~
- 如果代码块中出现、`字符，可以使用、~代替

- 支持的语言

  1c, abnf, accesslog, actionscript, ada, apache, applescript, arduino, armasm, asciidoc, aspectj, autohotkey, autoit, avrasm, awk, axapta, bash, basic, bnf, brainfuck, cal, capnproto, ceylon, clean, clojure, clojure-repl, cmake, coffeescript, coq, cos, cpp, crmsh, crystal, cs, csp, css, d, dart, delphi, diff, django, dns, dockerfile, dos, dsconfig, dts, dust, ebnf, elixir, elm, erb, erlang, erlang-repl, excel, fix, flix, fortran, fsharp, gams, gauss, gcode, gherkin, glsl, go, golo, gradle, groovy, haml, handlebars, haskell, haxe, hsp, htmlbars, http, hy, inform7, ini, irpf90, java, javascript, json, julia, kotlin, lasso, ldif, leaf, less, lisp, livecodeserver, livescript, llvm, lsl, lua, makefile, markdown, mathematica, matlab, maxima, mel, mercury, mipsasm, mizar, mojolicious, monkey, moonscript, n1ql, nginx, nimrod, nix, nsis, objectivec, ocaml, openscad, oxygene, parser3, perl, pf, php, pony, powershell, processing, profile, prolog, protobuf, puppet, purebasic, python, q, qml, r, rib, roboconf, rsl, ruby, ruleslanguage, rust, scala, scheme, scilab, scss, smali, smalltalk, sml, sqf, sql, stan, stata, step21, stylus, subunit, swift, taggerscript, tap, tcl, tex, thrift, tp, twig, typescript, vala, vbnet, vbscript, vbscript-html, verilog, vhdl, vim, x86asm, xl, xml, xquery, yaml, zephir

## 数学符号表示

使用 MathJax 解析 LaTeX 数学符号表示，LaTaX 符号表示可以参考：

- [http://mirror.lzu.edu.cn/CTAN/info/symbols/math/maths-symbols.pdf](http://mirror.lzu.edu.cn/CTAN/info/symbols/math/maths-symbols.pdf)

## 如何在博客中使用 mermaid 功能

- 在文章头声明开启 mermaid：`mermaid: true`
- 关闭 html 压缩功能，防止 mermaid 语法被破坏
  - 删除 `_layouts/default.html` 的头四行
- 使用较新的 mermaid 版本
  - 修改 `_includes/footer.html` 文件第 51 行为 `<script src="https://cdn.jsdelivr.net/npm/mermaid@8.5.0/dist/mermaid.min.js"></script>`

## 添加状态转换图

```markdown
<div class="mermaid">
stateDiagram
  [*] --> S0
  S0 --> S0 : B,C
  S0 --> S1 : A
  S1 --> S1 : A
  S1 --> S0 : C
  S1 --> S2 : B
  S2 --> S0 : B,C
  S2 --> S3 : A
  S3 --> S1 : A
  S3 --> S0 : C
  S3 --> S4 : B
  S4 --> S0 : B,C
  S4 --> S5 : A
  S5 --> S1 : A
  S5 --> S4 : B
  S5 --> S6 : C
  S6 --> [*]
</div>
```

这里需要格外注意的是，状态名词不能以数字开头！

<div class="mermaid">
stateDiagram
  [*] --> S0
  S0 --> S0 : B,C
  S0 --> S1 : A
  S1 --> S1 : A
  S1 --> S0 : C
  S1 --> S2 : B
  S2 --> S0 : B,C
  S2 --> S3 : A
  S3 --> S1 : A
  S3 --> S0 : C
  S3 --> S4 : B
  S4 --> S0 : B,C
  S4 --> S5 : A
  S5 --> S1 : A
  S5 --> S4 : B
  S5 --> S6 : C
  S6 --> [*]
</div>

