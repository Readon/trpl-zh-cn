# 使用模块组织和复用代码

> [ch07-00-modules.md](https://github.com/rust-lang/book/blob/master/second-edition/src/ch07-00-modules.md)
> <br>
> commit a0b6dd108ac3896a771c1f6d74b2cd906b8bce19

在你刚开始编写 Rust 程序时，代码可能仅仅位于 `main` 函数中。随着代码量的增长，为了复用和更好地组织代码，最终你会将功能移动到其他函数中。通过将代码分隔成更小的块，每一个块代码自身就更易于理解。不过当你发现自己有太多的函数了该怎么办呢？Rust 有一个模块系统可以有组织地复用代码。

就跟你将代码行提取到一个函数中一样，也可以将函数（和其他类似结构体和枚举的代码）提取到不同模块中。**模块**（*module*）是一个包含函数或类型定义的命名空间，你可以选择这些定义能（公有）或不能（私有）在其模块外可见。下面是一个模块如何工作的梗概：

* 使用 `mod` 关键字声明新模块。此模块中的代码要么直接位于声明之后的大括号中，要么位于另一个文件。
* 函数、类型、常量和模块默认都是私有的。可以使用 `pub` 关键字将其变成公有并在其命名空间之外可见。
* `use` 关键字将模块或模块中的定义引入到作用域中以便于引用它们。

我们会逐一了解这每一部分并学习如何将它们结合在一起。