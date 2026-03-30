---
title: "SNN 架构的初步探索与公式渲染测试"
description: "这是一篇测试文章，用于检验 Stack 主题的 LaTeX 公式与多语言代码高亮渲染效果。"
date: 2026-03-29T12:00:00+08:00  # 把时间改到昨天，避开系统的“未来”时间检测
draft: false                       # 强制明确告诉 Hugo：这不是草稿！立即发布！
image: "img/background.jpg" # Stack主题特色：自动将你的背景图设为文章头图
categories:
    - "研究笔记"
tags:
    - "SNN"
    - "深度学习"
    - "Python"
---

欢迎来到我的全新极客博客！这不仅是一个展示技术的平台，更是我记录底层硬件开发与前沿算法推导的数字花园。

## 1. 核心公式测试 (LaTeX 渲染)

在探索脉冲神经网络（SNNs）时，神经元动力学通常使用 Leaky Integrate-and-Fire (LIF) 模型来描述。膜电位 $U(t)$ 的微分方程可以极其优雅地表示为：

$$
\tau_m \frac{dU(t)}{dt} = - (U(t) - U_{rest}) + R I(t)
$$

当膜电位超过阈值 $V_{th}$ 时，神经元会发放一个脉冲（Spike），并迅速重置为 $U_{rest}$。

## 2. 代码高亮测试 (Python)

下面是一段基于 PyTorch 的 LIF 神经元前向传播伪代码，主要用于测试 Stack 主题的暗色模式代码高亮效果：

```python
import torch
import torch.nn as nn

class LIFNeuron(nn.Module):
    def __init__(self, tau_m=20.0, v_threshold=1.0, v_reset=0.0):
        super().__init__()
        self.tau_m = tau_m
        self.v_th = v_threshold
        self.v_reset = v_reset
        self.v = v_reset

    def forward(self, current_input, dt=1.0):
        # 膜电位更新逻辑 (简化的欧拉法)
        dv = (-(self.v - self.v_reset) + current_input) * (dt / self.tau_m)
        self.v += dv
        
        # 脉冲发放与重置 (Heaviside 阶跃函数)
        spike = (self.v >= self.v_th).float()
        self.v = torch.where(spike > 0, torch.tensor(self.v_reset), self.v)
        
        return spike     