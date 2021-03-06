
<!--type=misc-->

在整个文档中都有关于章节稳定性的指数。 
有些 API 已经被验证、被依赖，且几乎不可能再改变。
有些则是全新的且实验性的、或者已知有危险的。

稳定性指数如下：

> 稳定性: 0 - 弃用。
> 此特性可能会触发警告。
> 不保证向后兼容性。

<!-- separator -->

> 稳定性: 1 - 实验。
> 此特性不受[语义化版本控制][Semantic Versioning]规范的约束。
> 在任何的未来版本中可能发生不向后兼容的更改或移除。
> 建议不要在生产环境中使用该特性。

<!-- separator -->

> 稳定性: 2 - 稳定。
> 与 npm 生态系统的兼容性是最高的优先级。

在使用实验的特性时必须谨慎，特别是在模块中。
用户可能不知道正在使用实验的特性。
当实验的 API 发生修改时，可能会出现意外的故障或行为的改变。
为了避免此类意外，使用实验的特性可能需要命令行标志。
实验的特性也可能触发[警告][warning]。

