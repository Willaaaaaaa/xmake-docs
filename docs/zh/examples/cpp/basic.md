
下面我们简单介绍一些常用的工程例子，更多更全的examples工程可以到[project examples](https://github.com/xmake-io/xmake/tree/master/tests/projects)中查看。

我们也可以通过：`xmake create`命令创建各种常用的空工程来快速开始，具体对于这个命令的介绍以及支持的工程模板，可以敲下面的命令查看：

```bash
xmake create --help
```

## 可执行程序 {#executable}

```lua
target("test")
    set_kind("binary")
    add_files("src/*cpp")
```

完整例子请执行下面的命令来创建：

```bash
xmake create test
```

如果我们想创建 C 语言程序，只需要添加 `-l c` 命令行参数，例如：

```bash
xmake create -l c test
```

## 静态库程序 {#static-library}

```lua
target("foo")
    set_kind("static")
    add_files("src/foo/*.cpp")

target("test")
    set_kind("binary")
    add_files("src/*.cpp")
    add_deps("foo")
```

通过`add_deps`将一个静态库自动链接到test可执行程序。

完整例子请执行下面的命令来创建：

```bash
xmake create -t static test
```

如果我们想创建 C 语言程序，只需要添加 `-l c` 命令行参数，例如：

```bash
xmake create -l c -t static test
```

## 动态库程序 {#shared-library}

```lua
target("foo")
    set_kind("shared")
    add_files("src/foo/*.cpp")

target("test")
    set_kind("binary")
    add_files("src/*.cpp")
    add_deps("foo")
```

通过`add_deps`将一个动态库自动链接到test可执行程序。

完整例子请执行下面的命令来创建：

```bash
xmake create -t shared test
```

如果我们想创建 C 语言程序，只需要添加 `-l c` 命令行参数，例如：

```bash
xmake create -l c -t shared test
```
