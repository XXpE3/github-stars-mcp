---
project: Chinese-Llama-2-7b
stars: 2232
description: |-
    开源社区第一个能下载、能运行的中文 LLaMA2 模型！
url: https://github.com/LinkSoul-AI/Chinese-Llama-2-7b
---

# Chinese Llama 2 7B

[![](https://img.shields.io/badge/LLaMA2-Chinese-blue)](https://github.com/LinkSoul-AI/Chinese-Llama-2-7b) [![](https://img.shields.io/badge/Commercial-Support-blue)](https://github.com/LinkSoul-AI/Chinese-Llama-2-7b) [![](https://img.shields.io/badge/License-Apache_v2-blue)](https://github.com/LinkSoul-AI/Chinese-Llama-2-7b/blob/main/LICENSE) [![](https://img.shields.io/badge/HuggingFace-Live_Demo-green)](https://huggingface.co/spaces/LinkSoul/Chinese-Llama-2-7b) [![](https://img.shields.io/badge/Datasets-instruction_merge_set-blue)](https://huggingface.co/datasets/LinkSoul/instruction_merge_set)

全部开源，完全可商用的**中文版 Llama2 模型及中英文 SFT 数据集**，输入格式严格遵循 *llama-2-chat* 格式，兼容适配所有针对原版 *llama-2-chat* 模型的优化。

![Chinese LLaMA2 7B](.github/preview.jpg)

## 基础演示

![Base Demo](.github/demo.gif)

## 在线试玩

> Talk is cheap, Show you the Demo.
- [Demo 地址 / HuggingFace Spaces](https://huggingface.co/spaces/LinkSoul/Chinese-Llama-2-7b)
- [Colab (FP16/需要开启高RAM,免费版无法使用)](https://colab.research.google.com/github/LinkSoul-AI/Chinese-Llama-2-7b/blob/main/chinese-llama-2-7b.ipynb) 
- [Colab (INT4/需要开启高RAM,免费版无法使用)](https://colab.research.google.com/github/LinkSoul-AI/Chinese-Llama-2-7b/blob/main/chinese-llama-2-7b-4bit.ipynb) 

## 最新更新
- 10月26日 提供始智AI链接[Chinese Llama2 Chat Model](https://www.wisemodel.cn/models/LinkSoul/Chinese-Llama-2-7b/intro) 🔥🔥🔥
- 8月24日 新加ModelScope链接[Chinese Llama2 Chat Model](https://www.modelscope.cn/linksoul/Chinese-Llama-2-7b) 🔥🔥🔥
- 7月31号 基于 Chinese-llama2-7b 的中英双语语音-文本 [LLaSM](https://github.com/LinkSoul-AI/LLaSM) 多模态模型开源 🔥🔥🔥
- 7月31号 基于 Chinese-llama2-7b 的中英双语视觉-文本 [Chinese-LLaVA](https://github.com/LinkSoul-AI/Chinese-LLaVA) 多模态模型开源 🔥🔥🔥
- 7月26号 Chinese-llama2-7b-ggml 模型开源🔥🔥
- 7月23日 更新7b模型，添加API，提供4bit量化模型🔥🔥
- 7月22号 SFT训练/推理代码上线 🔥
- 7月21号 docker 一键部署上线 🔥
- 7月21号 demo上线 🔥
- 7月21号 中英双语 SFT 数据开源 🔥🔥
- 7月21号 Chinese-llama2-7b 模型开源 🔥🔥


## 资源下载

- 模型下载
  - 始智AI: [Chinese Llama2 Chat Model](https://www.wisemodel.cn/models/LinkSoul/Chinese-Llama-2-7b/intro)
  - ModelScope: [Chinese Llama2 Chat Model](https://www.modelscope.cn/linksoul/Chinese-Llama-2-7b)
  - HuggingFace: [Chinese Llama2 Chat Model](https://huggingface.co/LinkSoul/Chinese-Llama-2-7b)
  - 百度网盘: [1.0 正式版](https://pan.baidu.com/s/1GQ9S0szo7LCJIkGoAHciDg?pwd=zusq)
  - 百度网盘: [1.1 加强火力版](https://pan.baidu.com/s/1RFp3rUKsn5oTYE6rignIGA?pwd=qyrh)

- 4bit量化
  - HuggingFace：[Chinese Llama2 4bit Chat Model](https://huggingface.co/LinkSoul/Chinese-Llama-2-7b-4bit)
  - 百度网盘: [Chinese Llama2 4bit Chat Model](https://pan.baidu.com/s/17Llr3rIGF5AviT_l4DN_YA?pwd=ug13)

- GGML Q4 模型：
  - [https://huggingface.co/LinkSoul/Chinese-Llama-2-7b-ggml](https://huggingface.co/LinkSoul/Chinese-Llama-2-7b-ggml)
  - [https://huggingface.co/rffx0/Chinese-Llama-2-7b-ggml-model-q4_0](https://huggingface.co/rffx0/Chinese-Llama-2-7b-ggml-model-q4_0)
  - [https://huggingface.co/soulteary/Chinese-Llama-2-7b-ggml-q4](https://huggingface.co/soulteary/Chinese-Llama-2-7b-ggml-q4)
  - 百度网盘: [Chinese-Llama-2-7b-ggml](https://pan.baidu.com/s/1yfTeBgkqZ4DV00Q-XrLq2Q?pwd=bwvd)

> 我们使用了中英文 SFT 数据集，数据量 1000 万。

- 数据集：[https://huggingface.co/datasets/LinkSoul/instruction_merge_set](https://huggingface.co/datasets/LinkSoul/instruction_merge_set)

## 快速测试

```python
from transformers import AutoTokenizer, AutoModelForCausalLM, TextStreamer

model_path = "LinkSoul/Chinese-Llama-2-7b"

tokenizer = AutoTokenizer.from_pretrained(model_path, use_fast=False)
model = AutoModelForCausalLM.from_pretrained(model_path).half().cuda()
streamer = TextStreamer(tokenizer, skip_prompt=True, skip_special_tokens=True)

instruction = """[INST] <<SYS>>\nYou are a helpful, respectful and honest assistant. Always answer as helpfully as possible, while being safe.  Your answers should not include any harmful, unethical, racist, sexist, toxic, dangerous, or illegal content. Please ensure that your responses are socially unbiased and positive in nature.

            If a question does not make any sense, or is not factually coherent, explain why instead of answering something not correct. If you don't know the answer to a question, please don't share false information.\n<</SYS>>\n\n{} [/INST]"""

prompt = instruction.format("用中文回答，When is the best time to visit Beijing, and do you have any suggestions for me?")
generate_ids = model.generate(tokenizer(prompt, return_tensors='pt').input_ids.cuda(), max_new_tokens=4096, streamer=streamer)
```

## Docker

你可以使用仓库中的 Dockerfile，来快速制作基于 Nvidia 最新版本的 `nvcr.io/nvidia/pytorch:23.06-py3` 基础镜像，在任何地方使用容器来运行中文的 LLaMA2 模型应用。

```bash
docker build -t linksoul/chinese-llama2-chat .
```

镜像构建完毕，使用命令运行镜像即可：

```bash
docker run --gpus all --ipc=host --ulimit memlock=-1 --ulimit stack=67108864 --rm -it -v `pwd`/LinkSoul:/app/LinkSoul -p 7860:7860 linksoul/chinese-llama2-chat
```

## GGML / Llama.cpp

想要在 CPU 环境运行 LLaMA2 模型么？使用下面的方法吧。

- 使用 `ggml/convert_to_ggml.py` 进行转换操作，详见脚本支持的 CLI 参数。
- 或使用 `docker pull soulteary/llama2:converter` 下载模型格式转换工具镜像，在 Docker 容器中使用下面的两条命令完成操作（教程 [构建能够使用 CPU 运行的 MetaAI LLaMA2 中文大模型
](https://zhuanlan.zhihu.com/p/645426799)）：

```bash
python3 convert.py /app/LinkSoul/Chinese-Llama-2-7b/ --outfile /app/LinkSoul/Chinese-Llama-2-7b-ggml.bin
./quantize /app/LinkSoul/Chinese-Llama-2-7b-ggml.bin /app/LinkSoul/Chinese-Llama-2-7b-ggml-q4.bin q4_0
```

量化配置的定义:

转自: <https://www.reddit.com/r/LocalLLaMA/comments/139yt87/notable_differences_between_q4_2_and_q5_1/>

  * q4_0 = 32 numbers in chunk, 4 bits per weight, 1 scale value at 32-bit float (5 bits per value in average), each weight is given by the common scale * quantized value.

  * q4_1 = 32 numbers in chunk, 4 bits per weight, 1 scale value and 1 bias value at 32-bit float (6 bits per value in average), each weight is given by the common scale * quantized value + common bias.

  * q4_2 = same as q4_0, but 16 numbers in chunk, 4 bits per weight, 1 scale value that is 16-bit float, same size as q4_0 but better because chunks are smaller.

  * q4_3 = already dead, but analogous: q4_1 but 16 numbers in chunk, 4 bits per weight, scale value that is 16 bit and bias also 16 bits, same size as q4_1 but better because chunks are smaller.

  * q5_0 = 32 numbers in chunk, 5 bits per weight, 1 scale value at 16-bit float, size is 5.5 bits per weight

  * q5_1 = 32 numbers in a chunk, 5 bits per weight, 1 scale value at 16 bit float and 1 bias value at 16 bit, size is 6 bits per weight.

  * q8_0 = same as q4_0, except 8 bits per weight, 1 scale value at 32 bits, making total of 9 bits per weight.


## API部署
首先需要安装额外的依赖 `pip install fastapi uvicorn`，然后运行仓库中的 [api.py](api.py)：
```shell
python api.py
```
默认部署在本地的 8000 端口，通过 POST 方法进行调用
```shell
curl -X POST "http://127.0.0.1:8000" \
     -H 'Content-Type: application/json' \
     -d '{"prompt": "你好", "history": []}'
```
得到的返回值为
```shell
{
  "response":" 你好！我是一个人工智能语言模型，可以回答你的问题和进行对话。请问你有什么需要帮助的吗？ ",
  "history":[["<<SYS>>\nYou are a helpful, respectful and honest assistant. Always answer as helpfully as possible, while being safe.  Your answers should not include any harmful, unethical, racist, sexist, toxic, dangerous, or illegal content. Please ensure that your responses are socially unbiased and positive in nature.\n\n            If a question does not make any sense, or is not factually coherent, explain why instead of answering something not correct. If you don't know the answer to a question, please don't share false information.\n<</SYS>>\n\n你好"," 你好！我是一个人工智能语言模型，可以回答你的问题和进行对话。请问你有什么需要帮助的吗？ "]],
  "status":200,
  "time":"2023-08-01 09:22:16"
}
```


## 如何训练

```bash
DATASET="LinkSoul/instruction_merge_set"

DATA_CACHE_PATH="hf_datasets_cache"
MODEL_PATH="/PATH/TO/TRANSFORMERS/VERSION/LLAMA2"

output_dir="./checkpoints_llama2"

torchrun --nnodes=1 --node_rank=0 --nproc_per_node=8 \
    --master_port=25003 \
        train.py \
        --model_name_or_path ${MODEL_PATH} \
        --data_path ${DATASET} \
        --data_cache_path ${DATA_CACHE_PATH} \
        --bf16 True \
        --output_dir ${output_dir} \
        --num_train_epochs 1 \
        --per_device_train_batch_size 4 \
        --per_device_eval_batch_size 4 \
        --gradient_accumulation_steps 1 \
        --evaluation_strategy 'no' \
        --save_strategy 'steps' \
        --save_steps 1200 \
        --save_total_limit 5 \
        --learning_rate 2e-5 \
        --weight_decay 0. \
        --warmup_ratio 0.03 \
        --lr_scheduler_type cosine \
        --logging_steps 1 \
        --fsdp 'full_shard auto_wrap' \
        --fsdp_transformer_layer_cls_to_wrap 'LlamaDecoderLayer' \
        --tf32 True \
        --model_max_length 4096 \
        --gradient_checkpointing True
```

## 相关项目

- [Llama2](https://ai.meta.com/llama/)
- [soulteary/docker-llama2-chat](https://github.com/soulteary/docker-llama2-chat)


## 项目协议

[Apache-2.0 license](https://github.com/LinkSoul-AI/Chinese-Llama-2-7b/blob/main/LICENSE)

## 微信交流群

<img src=".github/QRcode.jpg" alt="微信交流群" width="300"/>

