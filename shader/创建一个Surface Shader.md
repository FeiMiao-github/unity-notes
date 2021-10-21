# 创建一个Surface Shader

1. It's begins with the `Shader` keyword followed by a string defining a menu item for the shader.

2. Shader can have multiple sub-shader(s), each defined by the `SubShader` keyword followed by a code block.

3. Below the sub-shader, we also want to add a `Fallback` to the standard diffuse shader, by writing `FallBack "Diffuse"`

4. The sub-shader of a surface shader needs a code section written in a hybrid of `CG` and `HLSL`,

   two shader languages. This code must be enclosed by the `CGPROGRAM` and `ENDCG` Keywords.

5. `Albedo` means whiteness in Latin. It's means a measure of how much light is diffusely reflected by a surface. If albedo isn't fully white then part of the light energy gets absorbed instead of reflected.

```hlsl

Shader "Graph/Point Surface" {
	Properties {
		_Smoothness ("Smoothness", Range(0, 1)) = 0.5
	}
	SubShader {
		CGPROGRAM
		
		#pragma surface ConfigureSurface Standard fullforwardshadows
		#pragma target 3.0
		
		struct Input
		{
			float3 worldPos;
		};
		
		float _Smoothness;
		
		void ConfigureSurface(Input input, inout SurfaceOutputStandard surface)
		{
			surface.Smoothness = _Smoothness;
			surface.Albedo = input.worldPos;
		}
		
		ENDCG
	}
	
	FallBack "Diffuse"
}
```



