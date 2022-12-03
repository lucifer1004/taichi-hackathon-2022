# Taichi Hackathon 2022

- 团队名：`Steins; Gate`
- 项目名：`TaichiMakie`
- 项目介绍：利用 `Taichi` 的 `GGUI` 实现 [`Makie.jl`](https://docs.makie.org/) 新后端
- 项目指路：https://github.com/lucifer1004/TaichiMakie.jl

[`Makie.jl`](https://docs.makie.org/) 是一个 Julia 语言的绘图库，对绘图进行了很好的抽象，因此可以支持不同的后端。官方实现的后端有 `GLMakie.jl`、`CairoMakie.jl`、`WGLMakie.jl` 等。我们队伍在本次 Taichi Hackathon 的项目，就是要利用 Taichi GGUI 来实现一个新的后端。

项目架构主要参考了 `CairoMakie.jl`。一个重要的优化点是将同类的绘制合并，批量处理。

目前实现了一个 `Makie.jl` 后端所需要具备的绝大部分功能，可以参见项目仓库中的有关示例。

目前的缺陷：

- 由于 `Taichi GGUI` 没有抗锯齿功能，线条边缘往往存在明显的毛刺。
- 由于 `Taichi GGUI` 没有原生的 `text` 功能，对文字的处理比较 Hacky，显示效果不够理想。
- 目前还没有正确处理 `Makie.jl` 中 `Mesh` 坐标与 `Taichi GGUI` 中坐标的转换关系，因此相关的绘图功能暂时存在问题。
