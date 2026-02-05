---
title:       "基于HuggingFace的开发栈"
subtitle:    ""
description: "基于HuggingFace的开发栈，包括模型微调、数据合成、模型评测等"
date:        2025-11-07
image:       ""
tags:        ["AI", "HuggingFace"]
categories:  ["AI" ]
---

## trl 模型微调

- [GitHub - huggingface/trl: Train transformer language models with reinforcement learning.](https://github.com/huggingface/trl)
- [Command Line Interfaces (CLIs)](https://huggingface.co/docs/trl/main/en/clis)
You can use the TRL Command Line Interface (CLI) to quickly get started with Supervised Fine-tuning (SFT) and Direct Preference Optimization (DPO), or vibe check your model with the chat CLI:

**SFT:**

```shell
trl sft --model_name_or_path Qwen/Qwen2.5-0.5B \
    --dataset_name trl-lib/Capybara \
    --output_dir Qwen2.5-0.5B-SFT
```

**DPO:**

```shell
trl dpo --model_name_or_path Qwen/Qwen2.5-0.5B-Instruct \
    --dataset_name argilla/Capybara-Preferences \
    --output_dir Qwen2.5-0.5B-DPO 
```

**Chat:**

```shell
trl chat --model_name_or_path Qwen/Qwen2.5-0.5B-Instruct
```

Read more about CLI in the [relevant documentation section](https://huggingface.co/docs/trl/main/en/clis) or use `--help` for more details.

## peft LORA

- [GitHub - huggingface/peft: 🤗 PEFT: State-of-the-art Parameter-Efficient Fine-Tuning.](https://github.com/huggingface/peft)
- [PEFT](https://huggingface.co/docs/peft/index)
- 大模型微调，适配不同现存GPU

## distilabel 数据合成

- [GitHub - argilla-io/distilabel: Distilabel is a framework for synthetic data and AI feedback for engineers who need fast, reliable and scalable pipelines based on verified research papers.](https://github.com/argilla-io/distilabel?tab=readme-ov-file)
- [Quickstart - Distilabel Docs](https://distilabel.argilla.io/latest/sections/getting_started/quickstart/)
- 功能小结：
  - 支持多种LLM模型导入方式
  - `TextGeneration`完成基础的文本补全功能
  - `SelfInstruct`用于更新种子prompt
  - `EvolInstruct`更新prompt
  - `EvolQuality` , 同上
  - `UltraFeedback` 对生成结果的评价打分

## datatrove

- [GitHub - huggingface/datatrove: Freeing data processing from scripting madness by providing a set of platform-agnostic customizable pipeline processing blocks.](https://github.com/huggingface/datatrove)
- LLM数据处理包
- Types of pipeline blocks：Each pipeline block takes a generator of `Document` as input and returns another generator of `Document`.：
  - **[readers](https://github.com/huggingface/datatrove/blob/main/src/datatrove/pipeline/readers)** read data from different formats and yield `Document`
  - **[writers](https://github.com/huggingface/datatrove/blob/main/src/datatrove/pipeline/writers)** save `Document` to disk/cloud in different formats
  - **[extractors](https://github.com/huggingface/datatrove/blob/main/src/datatrove/pipeline/extractors)** extract text content from raw formats (such as webpage html)
  - **[filters](https://github.com/huggingface/datatrove/blob/main/src/datatrove/pipeline/filters)** filter out (remove) some `Document`s based on specific rules/criteria
  - **[stats](https://github.com/huggingface/datatrove/blob/main/src/datatrove/pipeline/stats)** blocks to collect statistics on the dataset
  - **[tokens](https://github.com/huggingface/datatrove/blob/main/src/datatrove/pipeline/tokens)** blocks to tokenize data or count tokens
  - **[dedup](https://github.com/huggingface/datatrove/blob/main/src/datatrove/pipeline/dedup)** blocks for deduplication
- 实践
  - [[数据构建#Base#HuggingFaceTB/cosmopedia]]的github code

## TextClustering

- [GitHub - huggingface/text-clustering: Easily embed, cluster and semantically label text datasets](https://github.com/huggingface/text-clustering)
- The Text Clustering repository contains tools to easily embed and cluster texts as well as label clusters semantically. This repository is a work in progress and serves as a minimal codebase that can be modified and adapted to other use cases.

## argilla 数据标注

- [Argilla Docs](https://docs.argilla.io/latest/)
- [GitHub - argilla-io/argilla: Argilla is a collaboration tool for AI engineers and domain experts to build high-quality datasets](https://github.com/argilla-io/argilla/)

## lighteval 模型/数据集评测

- [GitHub - huggingface/lighteval: Lighteval is your all-in-one toolkit for evaluating LLMs across multiple backends](https://github.com/huggingface/lighteval?tab=readme-ov-file)
- [Home · huggingface/lighteval Wiki · GitHub](https://github.com/huggingface/lighteval/wiki)
- [Adding a New Metric · huggingface/lighteval Wiki · GitHub](https://github.com/huggingface/lighteval/wiki/Adding-a-New-Metric)
- 功能小结：
  - 定义LLM在特定数据集上的性能评测接口
  - 包含常见评测函数

## llm-swarm

- [GitHub - huggingface/llm-swarm: Manage scalable open LLM inference endpoints in Slurm clusters](https://github.com/huggingface/llm-swarm)
- Generate synthetic datasets for pretraining or fine-tuning using either local LLMs or [Inference Endpoints](https://huggingface.co/inference-endpoints/dedicated) on the Hugging Face Hub.
- Integrations with [huggingface/text-generation-inference](https://github.com/huggingface/text-generation-inference) and [vLLM](https://github.com/vllm-project/vllm) to generate text at scale.
- A Slurm cluster with Docker support, 
- or access to Inference Endpoints