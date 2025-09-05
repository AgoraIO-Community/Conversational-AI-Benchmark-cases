# 对话式AI基准测试用例

一个全面的基准测试用例集合，用于评估多语言和多种场景下的文本转语音（TTS）系统和对话式AI模型。

## 概述

本仓库包含精心策划的测试用例，旨在评估TTS系统和对话式AI模型在各种语言挑战上的性能，包括发音准确性、标点符号处理、技术术语和多语言处理。

## 仓库结构

```
├── TTS_AP/                    # 文本转语音准确性与发音
│   └── en/                    # 英文测试用例
│       ├── abbreviations_acronyms.csv
│       ├── complex_combinations.csv
│       ├── punctuation_formatting.csv
│       └── special_cases.csv
├── TTS_WER/                   # 词错误率评估
│   └── general_en.csv
└── LICENSE
```

## 测试用例类别

### TTS_AP（文本转语音准确性与发音）

#### 英文测试用例（`TTS_AP/en/`）
- **abbreviations_acronyms.csv**: 技术缩写、首字母缩略词和单位（如："3.7 m/s²" → "three point seven meters per second squared"）
- **complex_combinations.csv**: 复杂语言组合，包括法律引用、医疗数据、技术规格和科学公式
- **punctuation_formatting.csv**: URL格式化、特殊字符、标点符号处理和文件扩展名
- **special_cases.csv**: 特殊发音情况，包括文件路径、化学公式、数学表达式和技术符号

### TTS_WER（词错误率）

- **general_en.csv**: 用于WER评估的通用英文对话文本

## 数据格式

所有CSV文件遵循一致的格式：
- **第1列**: `Sample Text` - TTS处理的输入文本
- **第2列**: `Expected Output` - 期望的发音输出

## 使用方法

### TTS系统评估

1. **发音准确性测试**:
   ```python
   import pandas as pd

   # 加载测试用例
   test_cases = pd.read_csv('TTS_AP/en/abbreviations_acronyms.csv')

   # 使用你的TTS系统处理
   for _, row in test_cases.iterrows():
       input_text = row['Sample Text']
       expected = row['Expected Output']
       actual = your_tts_system.synthesize(input_text)
       # 比较实际输出与期望输出
   ```

2. **词错误率计算**:
   ```python
   # 加载WER测试用例
   wer_cases = pd.read_csv('TTS_WER/general_en.csv')

   # 计算对话文本的WER
   for _, row in wer_cases.iterrows():
       reference = row['Expected Output']
       hypothesis = your_tts_system.synthesize(row['Sample Text'])
       wer = calculate_wer(reference, hypothesis)
   ```

### 模型基准测试

使用这些测试用例来：
- 评估不同语言领域的发音准确性
- 测试技术术语和缩写的处理能力
- 评估多语言能力
- 测量对话语境中的词错误率
- 比较不同的TTS模型和配置

## 主要特性

- **英文语言重点**: 针对英文TTS系统的全面测试用例
- **领域覆盖**: 技术、对话和专业词汇
- **真实场景**: 来自各个领域的实际例子，包括医疗、法律、科学和技术语境
- **标准化格式**: 易于集成的统一CSV格式
- **全面覆盖**: 边缘情况、缩写、数字、特殊字符、URL和数学表达式

## 测试用例示例

### 英文示例
- 技术缩写: "TLS 1.3" → "TLS one point three"
- 单位转换: "42 km/h" → "forty two kilometers per hour"
- URL处理: "http://example.com" → "HTTP colon slash slash example dot com"

### 更多英文示例
- 化学公式: "H₂O" → "H two O"
- 数学表达式: "F = ma" → "F equals ma"
- 文件路径: "/usr/local/bin" → "slash usr slash local slash bin"

## 贡献指南

本基准测试集合由AgoraIO社区维护。欢迎以下方面的贡献：
- 额外的测试用例
- 新语言支持
- 改进测试覆盖范围
- 错误修复和更正

## 许可证

本项目采用LICENSE文件中指定的许可证条款。

## 引用

如果您在研究或开发中使用此基准测试，请引用：

```bibtex
@misc{conversational_ai_benchmark,
  title={对话式AI基准测试用例},
  author={AgoraIO Community},
  year={2025},
  url={https://github.com/AgoraIO-Community/Conversational-AI-Benchmark-cases}
}
```

## 联系方式

如有问题、建议或贡献，请在此仓库中提交issue或联系AgoraIO社区。
