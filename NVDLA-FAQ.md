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

### support "locally connect conv"? (nvdla/hw issue 14)

question could be found from
https://github.com/nvdla/hw/issues/14

asked by apolonic:
> It means the weight of the convolution is loacal and not shared.
> Could you enlight me how it could be supported?

nvdsmith replied:
> This isn't one of the hardware layers targeted by the NVDLA core. Locally connected convolution can be mapped to the NVDLA, but given the large number of weights needed, bandwidth would limit MAC utilization. This might be fine in an IoT device depending on the network size. Is this something that's important to your application?
> Also, with batching I'd expect MAC utilization would be good with current weight bandwidth. Will need to map this out in more detail at some point though if it's important.

### support dilate conv? (nvdla/hw issue 13)

question could be found from
https://github.com/nvdla/hw/issues/13

asked by apolonic:
> Could you enlight me about how the dilate converlution is supported ?
> ps. CSC reguster D_DILATION_EXT takes the parameters.

nvdsmith replied:
> The convolution sequence the hardware follows is updated based on this parameter. Basically, the sequencer fetches the activations corresponding to the dialation setting.

### Q of SDP (nvdla/hw issue 11)

question could be found from
https://github.com/nvdla/hw/issues/11

asked by apolonic:
> PDP has a dedicated memory interface to fecth input map from memory and output map directly to memory.
> Does this "memory" means the memory outside of DLA? If it does, Is it CPU to reshape the data?
> Why not to fetch the input map from the conv buffer? What would be the cost by implementing this design?

nvdsmith replied:
> The SDP block has a number of operations arranged in a pipeline. So multiple operations can be chained together within the SDP block without affecting the throughput.

### Q of PDP design (nvdla/hw issue 10)

question could be found from
https://github.com/nvdla/hw/issues/10

nvdsmith replied:
> PDP will get the output from the accumulator directly without needing to first travel through memory. It's memory interface would be used for other data like bias. This data could be stored on an on-chip SRAM or in DRAM.

### 为什么 zero pad 了，硬件里面还有个 zero pad value？难道不是0么？

真不是。因为做了量化？

## 深度学习
