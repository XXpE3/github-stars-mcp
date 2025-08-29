---
project: bob-plugin-claude-translator
stars: 95
description: |-
    一个让 Bob 翻译可以使用 Anthropic Claude API 的插件
url: https://github.com/jtsang4/bob-plugin-claude-translator
---

<h4 align="right">
  <strong>简体中文</strong> | <a href="https://github.com/jtsang4/bob-plugin-claude-translator/blob/main/docs/README_EN.md">English</a>
</h4>

<div>
  <h1 align="center">Claude Translator Bob Plugin</h1>
  <p align="center">
    <a href="https://github.com/jtsang4/bob-plugin-claude-translator/releases" target="_blank">
        <img src="https://github.com/jtsang4/bob-plugin-claude-translator/actions/workflows/release.yaml/badge.svg" alt="release">
    </a>
    <a href="https://github.com/jtsang4/bob-plugin-claude-translator/releases">
        <img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/jtsang4/bob-plugin-claude-translator?style=flat">
    </a>
    <a href="https://github.com/jtsang4/bob-plugin-claude-translator/releases">
        <img alt="GitHub Repo stars" src="https://img.shields.io/badge/claude-bob-orange?style=flat">
    </a>
    <a href="https://github.com/jtsang4/bob-plugin-claude-translator/releases">
        <img alt="GitHub Repo stars" src="https://img.shields.io/badge/langurage-JavaScript-brightgreen?style=flat&color=blue">
    </a>
  </p>
</div>

## 简介

基于 [Anthropic Complete API](https://console.anthropic.com/docs/api/reference) 实现的 [Bob](https://bobtranslate.com/) 插件。拥有翻译、润色的功能。

### 润色功能

支持使用 Claude API 对句子进行润色和语法修改，只需要把目标语言设置为与源语言一样即可。

### 语言模型

[官网模型对比](https://docs.anthropic.com/en/docs/about-claude/models#model-comparison)
* `Claude 3 Haiku` (默认使用): 最快最紧凑的型号,可实现近乎即时的响应
* `Claude 3 Sonnet`: 智能和速度的平衡
* `Claude 3 Opus`: 用于高度复杂任务的强大模型
* `Claude 3.5 Sonnet`: 最智能的模型

## 使用方法

1. 安装 [Bob](https://bobtranslate.com/guide/#%E5%AE%89%E8%A3%85) (版本 >= 0.50)，一款 macOS 平台的翻译和 OCR 软件

2. 下载此插件: [claude-translator.bobplugin](https://github.com/jtsang4/bob-plugin-claude-translator/releases/latest)

3. 安装此插件

4. 去 [Claude](https://console.anthropic.com/account/keys) 获取你的 API KEY

5. 把 API KEY 填入 Bob 偏好设置 > 服务 > 此插件配置界面的 API KEY 的输入框中

6. (可选) 安装 [PopClip](https://bobtranslate.com/guide/integration/popclip.html) 实现划词后鼠标附近出现悬浮图标

## 感谢

本仓库是在 [yetone](https://github.com/yetone) 优秀的 [bob-plugin-openai-translator](https://github.com/yetone/bob-plugin-openai-translator) 源码基础上对 Claude API 所做的适配，感谢原作者的卓越贡献。

