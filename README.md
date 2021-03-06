# Jiagu自然语言处理工具
>>> Jiagu以BiLSTM等模型为基础，使用大规模语料训练而成。将提供中文分词、词性标注、命名实体识别、关键词抽取、文本摘要、新词发现等常用自然语言处理功能。参考了各大工具优缺点制作，将Jiagu回馈给大家。

提供的功能有：
* 中文分词        ok
* 词性标注        ok
* 命名实体识别     ok
* 关键词提取       ok
* 文本摘要
* 新词发现
* 等等。。。。



### 安装方式
pip安装（版本稳定了才会更新，如果需要使用新版本可以选择源码安装）
```shell
pip install jiagu
```
源码安装
```shell
git clone https://github.com/ownthink/Jiagu
cd Jiagu
python3 setup.py install
```

### 使用方式
1. 词法分析：分词、词性标注、命名实体识别
```python3
import jiagu

#jiagu.init() # 可手动初始化，也可以动态初始化

text = '厦门明天会不会下雨'

words = jiagu.seg(text) # 分词
print(words)

pos = jiagu.pos(words) # 词性标注
print(pos)

ner = jiagu.ner(text) # 命名实体识别
print(ner)
```

2. 关键词抽取
```python3
import jiagu

text = '携手推动民族复兴，实现和平统一目标；探索“两制”台湾方案，丰富和平统一实践；坚持一个中国原则，维护和平统一前景；深化两岸融合发展，夯实和平统一基础；实现同胞心灵契合，增进和平统一认同。在《告台湾同胞书》发表40周年纪念会上，习近平总书记提出的这五个方面重大政策主张，系统阐释了实现国家统一的目标内涵、基本方针、路径模式，深刻指明了今后一个时期对台工作的基本思路、重点任务和前进方向，既有坚定的原则性又有极强的针对性和极大的包容性，展现了非凡的政治勇气和政治智慧。'
words = jiagu.seg(text)

stop_words = ['的', '，', '；', '、']
words = [w for w in words if w not in stop_words] # 去除停用词，符号等

keywords = jiagu.keywords(words) # 关键词抽取

print(keywords)
```


### 附录
1. 词性标注说明
```text
n　　　普通名词
nt　 　时间名词
nd　 　方位名词
nl　 　处所名词
nh　 　人名
nhf　　姓
nhs　　名
ns　 　地名
nn 　　族名
ni 　　机构名
nz 　　其他专名
v　　 动词
vd　　趋向动词
vl　　联系动词
vu　　能愿动词
a　 　形容词
f　 　区别词
m　 　数词　　
q　 　量词
d　 　副词
r　 　代词
p　　 介词
c　 　连词
u　　 助词
e　 　叹词
o　 　拟声词
i　 　习用语
j　　 缩略语
h　　 前接成分
k　　 后接成分
g　 　语素字
x　 　非语素字
w　 　标点符号
ws　　非汉字字符串
wu　　其他未知的符号
```

2. 命名实体说明（采用BIO标记方式）
```text
人名
地名
机构名
时间
```

### 作者：
1. [Yener](https://github.com/ownthink)
2. [zengbin93](https://github.com/zengbin93)
3. [dirtdust](https://github.com/dirtdust)


