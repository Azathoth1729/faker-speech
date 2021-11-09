# Faker

[offical doc](https://faker.readthedocs.io/en/master/)

## Introcution

Faker是一个提供生成各种假数据的Python包.

## Overview

The faker.Faker() creates and initializes a faker generator, which can generate data by accessing properties named after the type of data.
Faker() 通过接受一个 `locale` 作为参数, 返回一个被本地化的生成器.

Faker delegates the data generation to providers. The default provider uses the English locale. Faker supports other locales; they differ in level of completion.

## Installation

```shell
pip install Faker
conda install Faker
```

## Why Faker

尽管我们有很多生成随机数据的方法，但这些方法不够系统也不够强大:

+ 语言局限
+ 种类不丰富
+ 不能够自定义

## Basic Usage

The faker.Faker() 创建并生成一个faker生成器, which can generate data by
accessing properties named after the type of data.

```python
from faker import Faker
fake = Faker()

fake.name()
# Zachary Mcdonald
# Edward Potter

fake.address()
# 9344 Sherry Loop Apt. 236

fake.text()
# Administration seem fight person politics.
# Drug that very view sister federal ask.
# Picture option probably increase check.
# Likely smile him young. Bill such owner hear likely sell late.
```

## Localization

Faker 能够生成不同语言的假数据.

通过接受一个 `locale` 作为参数, `Faker()` 能够返回一个被本地化的生成器.如果没有
指定 `locale` , `locale=DEFAULT_LOCALE=en_US`

```python
fake = Faker('zh_CN')
```

```python
from faker import Faker

fake = Faker(['zh_CN', "ja_JP", "en_US"])
[print(fake.name()) for _ in range(10)];
# Caitlin White
# 全春梅
# Deborah Kelley
# 田中 美加子
# 袁斌
```

## Providers

### standard providers

### unoffical

```python
from faker import Faker
from faker_music import MusicProvider
fake = Faker()
fake.add_provider(MusicProvider)

fake.music_genre()
# Progressive

fake.music_subgenre()
# College Rock

fake.music_instrument()
# Triccaballacca

fake.music_instrument_category()
# strings
```

### How to create a Provider

```python
from faker import Faker
fake = Faker()

# first, import a similar Provider or use the default one
from faker.providers import BaseProvider

# create new provider class
class MyProvider(BaseProvider):
    def foo(self) -> str:
        return 'bar'

# then add new provider to faker instance
fake.add_provider(MyProvider)

# now you can use:
fake.foo()
# 'bar'
```

### create a Dynamic provider

```python
from faker import Faker
from faker.providers import DynamicProvider

medical_professions_provider = DynamicProvider(
     provider_name="medical_profession",
     elements=["dr.", "doctor", "nurse", "surgeon", "clerk"],
)

fake = Faker()

# then add new provider to faker instance
fake.add_provider(medical_professions_provider)

# now you can use:
fake.medical_profession()
# 'dr.'
```

## Command line usage

```shell
faker [-h] [--version] [-o output]
      [-l {bg_BG,cs_CZ,...,zh_CN,zh_TW}]
      [-r REPEAT] [-s SEP]
      [-i {package.containing.custom_provider otherpkg.containing.custom_provider}]
      [fake] [fake argument [fake argument ...]]
```

```shell
$ faker address
968 Bahringer Garden Apt. 722
Kristinaland, NJ 09890

$ faker -l de_DE address
Samira-Niemeier-Allee 56
94812 Biedenkopf

$ faker profile ssn,birthdate
{'ssn': '628-10-1085', 'birthdate': '2008-03-29'}

$ faker -r=3 -s=";" name
Willam Kertzmann;
Josiah Maggio;
Gayla Schmitt;
```

## Seeding the Generator

When using Faker for unit testing, you will often want to generate the same data set. For convenience, the generator also provide a seed() method, which seeds the shared random number generator. Calling the same methods with the same version of faker and seed produces the same results.

```python
from faker import Faker
fake = Faker()
Faker.seed(4321)

print(fake.name())
# 'Margaret Boehm'
```

Each generator can also be switched to its own instance of random.Random, separate to the shared one, by using the seed_instance() method, which acts the same way.
For example:

```python
from faker import Faker
fake = Faker()
fake.seed_instance(4321)

print(fake.name())
# 'Margaret Boehm'
## accessing the random instance
```

## Examples
