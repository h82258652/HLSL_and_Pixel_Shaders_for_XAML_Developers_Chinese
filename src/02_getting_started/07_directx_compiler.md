# DirectX 编译器

Visual Studio 是如此的强大以至于许多人都认为它包含了任何编程语言的编译器，但是在 Visual Studio 2010 和 Expression Blend 4 中都不包含着色器编译器。
不过，好消息即将到来，下一个版本的 Visual Studio 会有出色的 3D 编辑器，以及它还会有一个着色器编辑器。
但在此时此刻，如果您想要继续向前，必须要先找到一个编译器。

自从 HLSL 是 DirectX 的一部分，您可以使用 DirectX SDK 中的 FXC.exe 编译器。
FXC.exe 是一个很小的文件，大小不足 200KB。
遗憾的是，这个 FXC 编译器仅作为 SDK 的一部分，而这个 SDK 就是一个庞然巨物，它会用掉您 1GB 的磁盘空间。

我会在本书的一些例子中用到 FXC 编译器。如果您也想这么做，您可以在这里找到 DirectX SDK。<http://msdn.microsoft.com/directx/>[^note]

[^note]：此链接可能已失效