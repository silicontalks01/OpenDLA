# 有关NVDLA的一些FAQ

如何贡献：欢迎直接PR问题到这个FAQ，或者提交PR回答这个FAQ中没有回答的问题。

## 文档类

### nvdla/doc 中的 `stripe_length` 是什么意思？

https://github.com/nvdla/doc/blob/35056106d8a13f7783ccae024710f6eec2c82b44/doc/hwarch.rst

搜索 `stripe_` 关键字。

### nvdla/doc 中的 WMB 是什么意思？

https://github.com/nvdla/doc/blob/35056106d8a13f7783ccae024710f6eec2c82b44/doc/hwarch.rst

搜索 `WMB` 关键字。

### DLA sub-unit 中的 MCIF 是什么的缩写？

memory xx interface？

### DLA sub-unit 中的 CVIF 是什么的缩写？

convolution interface？

### BDMA中的 CFG_LINE_REPEAT 字段解释中的 surface 是指什么？

### RAM Type of weights 有几种 type？

## 硬件实现类


## 深度学习

### 为什么 zero pad 了，硬件里面还有个 zero pad value？难道不是0么？

真不是。因为做了量化？
