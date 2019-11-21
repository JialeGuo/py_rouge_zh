# Py-rouge
A full Python implementation of the ROUGE metric, especially for Chinese texts processing. Mainly based on https://github.com/Diego999/py-rouge 
中文文本Rouge值相关计算的python实现

欢迎Star :grin:

# Important remarks
- Diego的实现主要适用于英文文本，主要调整的地方是其代码内的正则表达式部分以及针对英文处理的部分(如 .lower()等)
- 输入分词后或按字隔开的中文文本
- 注意输入输出的形式(hypothesis: hypothesis summary, string; references: reference summary/ies, either string or list of strings (if multiple))


# Installation


```shell
git clone https://github.com/JialeGuo/py_rouge_zh
cd py-rouge-zh
python setup.py install
```


# Example 
```python
import rouge_zh

evaluator = rouge_zh.Rouge(metrics=['rouge-n'],
                           max_n=4,
                           limit_length=True,
                           length_limit=100,
                           length_limit_type='words',
                           alpha=0.5, # Default F1_score
                           weight_factor=1.2,
                           stemming=True)

all_hypothesis = ["哈 尔 滨 是 黑 龙 江 的 省 会"]
all_references = [["哈 工 大 在 哈 尔 滨", "黑 龙 江 太 冷 了"]]

scores = evaluator.get_scores(all_hypothesis, all_references)
print(scores)

```
It produces the following output:

{'rouge-2': {'r': 0.1, 'p': 0.1, 'f': 0.10000000000000002}, 'rouge-3': {'r': 0.0, 'p': 0.0, 'f': 0.0}, 'rouge-4': {'r': 0.0, 'p': 0.0, 'f': 0.0}, 'rouge-1': {'r': 0.5, 'p': 0.5, 'f': 0.5}}
```    
