# WPF 构建任务

WPF 团队里有一些好人开源了一些项目在 Codeplex（<http://wpf.codeplex.com>[^note]） 上。
如果您瞄一下他们的 Codeplex 的这个站点，您会找到一个着色器构建任务却不需要安装 DirectX SDK（<http://wpf.codeplex.com/releases/view/14962/>）。
这里说一下它做了什么。
如果它安装成功的话，在执行 MSBuild 构建的过程中，它会查找您 WPF 项目中以 .fx 结尾的所有文件。
它会编译这些 .fx 文件到二进制文件（*.ps）。
然而，它有两个令人气愤的限制，一是它不适用于 Silverlight 项目，二是它不能编译到更新的 PS_3_0 标准。

[^note]：Codeplex 已关站。