# JeremyAnsel.HLSL.Targets[^note]

1、在您的项目中安装 [JeremyAnsel.HLSL.Targets]() NuGet 包。

2、修改项目文件，添加如下：
```diff
+ <ItemGroup>
+    <HLSLShader Include="YourEffect.hlsl">
+        <ShaderProfile>ps_3_0</ShaderProfile>
+    </HLSLShader>
+ </ItemGroup>
```
YourEffect.hlsl 为您的 HLSL 文件路径。

3、编译后会生成名为 ```YourEffect.cso``` 的文件，等价于前面三节的 .ps 文件。

[^note]：本章节是翻译版额外添加