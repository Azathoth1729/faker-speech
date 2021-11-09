# Faker

第十五小组

金可成 杨旭建 匡科帆

<!-- .slide: data-background="#81ceff" -->

---

## Introduction

Faker 是一个生成各种假数据的 Python 包

<!-- .slide: data-background="#81ceff" -->

---

## Why Faker

尽管我们有很多生成随机数据的方法，但这些方法不够系统也不够强大:

- 语言局限
- 种类不丰富
- 不能够自定义

<!-- .slide: data-background="#81ceff" -->

---

## Installation

```bash
pip install Faker
conda install Faker
```

Notes: Remmeber to say something funny here...

---

## Basic Usage

<!-- .slide: data-background="#81ceff" -->

---

`faker.Faker()` 创建一个 faker 生成器, 通过访问相应属性来获得不同类型的数据
<!-- .slide: data-background="#81ceff" -->

---

```python
from faker import Faker
fake = Faker()
```

```python [1-3|5-6|8-13]
fake.name()
# Zachary Mcdonald
# Edward Potter

fake.address()
# 9344 Sherry Loop Apt. 236

fake.text()
# Administration seem fight person politics.
# Drug that very view sister federal ask.
# Picture option probably increase check.
# Likely smile him young. Bill such owner hear likely 
# sell late.
```

---

## Localization

Faker 能够生成不同语言的假数据

<!-- .slide: data-background="#81ceff" -->

---

```python [1|3-4|5-10]
fake = Faker('zh_CN')

fake = Faker(['zh_CN', "ja_JP", "en_US"])
[print(fake.name()) for _ in range(10)]
# Caitlin White
# 全春梅
# Deborah Kelley
# 田中 美加子
# 袁斌
# ...
```

---

## Providers

- Standard Providers <!-- .element: class="fragment" data-fragment-index="1" -->

- Community Providers <!-- .element: class="fragment" data-fragment-index="2" -->
  
- Localized Providers <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-background="#81ceff" -->

---

## 感谢观看
<!-- .slide: data-background="#81ceff" -->
