<!-- YAML
added: v0.0.1
-->

* `callback` {Function} 当定时器到点时调用的函数。
* `delay` {number} 调用 `callback` 之前等待的毫秒数。**默认值**: `1`。
* `...args` {any} 当调用 `callback` 时传入的可选参数。
* 返回: {Timeout} 用于 [`clearInterval()`]。

安排每隔 `delay` 毫秒重复执行 `callback`。

当 `delay` 大于 `2147483647` 或小于 `1` 时，则 `delay` 将会被设置为 `1`。
非整数的 delay 会被截断为整数。

如果 `callback` 不是函数，则抛出 [`TypeError`]。

