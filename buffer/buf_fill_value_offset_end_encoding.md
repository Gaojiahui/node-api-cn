<!-- YAML
added: v0.5.0
changes:
  - version: v11.0.0
    pr-url: https://github.com/nodejs/node/pull/22969
    description: Throws `ERR_OUT_OF_RANGE` instead of `ERR_INDEX_OUT_OF_RANGE`.
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/18790
    description: Negative `end` values throw an `ERR_INDEX_OUT_OF_RANGE` error.
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/18129
    description: 尝试用零长度的 buffer 填充非零长度的 buffer 会触发抛出异常。
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/17427
    description: Specifying an invalid string for `value` triggers a thrown
                 exception.
  - version: v5.7.0
    pr-url: https://github.com/nodejs/node/pull/4935
    description: The `encoding` parameter is supported now.
-->

* `value` {string|Buffer|Uint8Array|integer} 用来填充 `buf` 的值。
* `offset` {integer} 开始填充 `buf` 的偏移量。**默认值:** `0`。
* `end` {integer} 结束填充 `buf` 的偏移量（不包含）。**默认值:** [`buf.length`]。
* `encoding` {string} 如果 `value` 是字符串，则指定 `value` 的字符编码。**默认值:** `'utf8'`。
* 返回: {Buffer} `buf` 的引用。

用指定的 `value` 填充 `buf`。
如果没有指定 `offset` 与 `end`，则填充整个 `buf`：

```js
// 用 ASCII 字符 'h' 填充 `Buffer`。

const b = Buffer.allocUnsafe(50).fill('h');

console.log(b.toString());
// 打印: hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
```

如果 `value` 不是字符串、`Buffer`、或整数，则会被转换为 `uint32` 值。
如果得到的整数大于 `255`（十进制），则 `buf` 将会使用 `value & 255` 填充。

如果 `fill()` 最后写入的是一个多字节字符，则只写入适合 `buf` 的字节：

```js
// 使用在 UTF-8 中占用两个字节的字符来填充 `Buffer`。

console.log(Buffer.allocUnsafe(5).fill('\u0222'));
// 打印: <Buffer c8 a2 c8 a2 c8>
```

如果 `value` 包含无效的字符，则截掉无效的字符。
如果截掉后没有数据，则不填充：

```js
const buf = Buffer.allocUnsafe(5);

console.log(buf.fill('a'));
// 打印: <Buffer 61 61 61 61 61>
console.log(buf.fill('aazz', 'hex'));
// 打印: <Buffer aa aa aa aa aa>
console.log(buf.fill('zz', 'hex'));
// 抛出异常。
```
