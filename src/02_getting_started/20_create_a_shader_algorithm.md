# 创建一个着色器算法

要制作一个自定义着色器首先要创建一个文本文件并添加一些 HLSL 代码到里面。
[例子 2-8]() 展示了如何编写一个 ```InvertColor``` 着色器。

*例子 2-8。InvertColor 着色器的 HLSL 代码*

```hlsl
sampler2D InputTexture;

float4 main(float2 uv : TEXCOORD) : COLOR {
    float4 color = tex2D(InputTexture, uv);
    float4 invertedColor = float4(color.a - color.rgb, color.a);

    return invertedColor;
}
```

例子中的代码不多，但足以将输入流中的每个像素的颜色反转。

代码的第一行声明了着色器的输入数据源 ```InputTexture```。

```sampler2D InputTexture;```

在您的例子程序中，```InputTexture``` 映射到 Image 元素中的像素。
接下来是函数声明。

```
float4 main(float2 uv : TEXCOORD) : COLOR {
```

如您所见，这个函数的名字叫 ```main``` 并返回一个类型为 ```float4``` 的值。
这个 ```float4``` 代表了修改后的像素的颜色值，它最终会被显示到电脑屏幕上。
您可以认为 float4 包含了 4 个值，分别对应颜色值中的红色、绿色、蓝色和透明度。
接下来两行从数据源采样一个像素并计算新的输出颜色存储到 ```invertedColor``` 变量中，

```
float4 color = tex2D(InputTexture, uv);
float4 invertedColor = float4(color.a - color.rgb, color.a);
```

最后，返回反转的颜色。

```
return invertedColor;
```