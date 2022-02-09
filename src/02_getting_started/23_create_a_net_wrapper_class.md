# 创建一个 .NET 的包装类

要使用一个像素着色器，您需要一个能让 .NET 代码与它交互的方式。
实现这一点规定的方式是编写一个```包装```类。
这个类派生自 ```ShaderEffect``` 基类，并公开依赖属性以操作着色器的属性。
因为这个简单的 ```InvertColor``` 着色器不提供任何着色器属性，所以例子的包装类会很小。

添加一个类到项目中并插入以下的代码（[例子 2-9]）。

*例子 2-9。InvertColorEffect 包装类*

```csharp
public class InvertColorEffect : ShaderEffect
{
    private PixelShader pixelShader = new PixelShader();

    public InvertColorEffect()
    {
        pixelShader.UriSource = 
            new Uri("/Ch02_CustomEffect;component/output.ps", UriKind.Relative);
        this.PixelShader = pixelShader;

        this.UpdateShaderValue(InputProperty);
    }

    public static readonly DependencyProperty InputProperty =
        ShaderEffect.RegisterPixelShaderSamplerProperty("Input",
            typeof(InvertColorEffect), 0);

    // 表示着色器的 InputSource
    public Brush Input
    {
        get
        {
            return ((Brush)(this.GetValue(InputProperty)));
        }
        set
        {
            this.SetValue(InputProperty, value);
        }
    }
}
```

您可能还记得 .NET 包装类必须指示 Silverlight 或者 WPF 加载这个二进制资源。
在 WPF 里，会被加载到 GPU 中，而在 Silverlight，则会被加载到虚拟化 GPU 中。
您可以在构造函数中看到加载的代码。

```
pixelShader.UriSource = new Uri("/Ch02_CustomEffect;component/output.ps", UriKind.Relative);
```

这里还有单个名字叫 ```InputProperty```的依赖属性。
这个属性表示着色器的输入。
换句话说，它的数据是由光栅化器提供的。
依赖属性遵守 XAML 的约定，看上去跟您预期的一样，只是有一点点不同。

```
public static readonly DependencyProperty InputProperty =
    ShaderEffect.RegisterPixelShaderSamplerProperty("Input",
        typeof(InvertColorEffect), 0);
```

```ShaderEffect.RegisterPixelShaderSamplerProperty``` 属性是依赖属性与着色器中注册的采样器关联的方式。
现在不需要过多担心这个类的这些细节。
是时候准备编译了。