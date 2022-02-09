# 关于伪代码的说明

在深入了解着色器之前先说几句话。
考虑到当前还在本书靠前面的篇章并且您还没有看过很多 HLSL 的语法。
所以这一章列出的大部分代码都是伪代码，这有助于解析着色器实现的一般想法，而不是使用官方的 HLSL 语法。
这里是一个简单的例子。

*例子 3-1。伪代码和 HLSL 对比*

```
// 伪代码
originalColor = color.r
average = (color.r + color.b + color.g) / 3
```

```hlsl
// HLSL 语法
float4 originalColor = tex2D(InputTexture, uv);
originalColor = color.r;

float average;
average = color.rgb / 3;
```

在这个例子中，HLSL 比起同样的伪代码更为精确。
首先，它使用 ```tex2D``` 函数获取了颜色。
然后，它分别通过 ```float4``` 和 ```float``` 关键字定义了变量。
在最后一行，通过 *swizzle* 语法计算了平均值。

> Swizzling 是 HLSL 中访问向量变量的一种独特方式。
> 虽然这个单词会让人联想到热带地区的水果味饮料，但它只是操作向量中的成员的任意组合的一种方式。