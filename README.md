## Mimesis

[![Build Status](https://travis-ci.org/lk-geimfari/mimesis.svg?branch=master)](https://travis-ci.org/lk-geimfari/mimesis)
[![Build status on Windows](https://ci.appveyor.com/api/projects/status/chj8huslvn6vde18?svg=true)](https://ci.appveyor.com/project/lk-geimfari/mimesis)
[![codecov](https://codecov.io/gh/lk-geimfari/mimesis/branch/master/graph/badge.svg)](https://codecov.io/gh/lk-geimfari/mimesis)
[![PyPI version](https://badge.fury.io/py/mimesis.svg)](https://badge.fury.io/py/mimesis)
[![Python](https://img.shields.io/badge/python-3.5%2C%203.6-brightgreen.svg)](https://badge.fury.io/py/mimesis)


<p align="center">
    <a href="https://github.com/lk-geimfari/mimesis">
        <img src="/media/logo-nodescr.png">
    </a>
</p>

**Mimesis** is a fast and easy to use library for Python programming language, which helps generate synthetic data for a variety of purposes (see «[Data providers](#data-providers)») in a variety of languages (see «[Locales](#locales)»). This data can be particularly useful during software development and testing. For example, it could be used to populate a testing database for a web application with user information such as email addresses, usernames, first names, last names, etc.

Mimesis offers a number of advantages over other similar libraries, such as Faker:

* Performance. Mimesis is significantly [faster](http://i.imgur.com/pCo6yPA.png) than other similar libraries.
* Completeness. Mimesis strives to provide many detailed providers that offer a variety of data generators.
* Simplicity. Mimesis does not require any modules other than the Python standard library.

See [here](https://gist.github.com/lk-geimfari/461ce92fd32379d7b73c9e12164a9154) for an example of how we compare
performance with other libraries.

## Documentation
Mimesis is very simple to use, and the below examples should help you get started. Complete documentation for Mimesis is available on [Read the Docs](http://mimesis.readthedocs.io/).

## Installation
To install mimesis, simply use pip (or [pipenv](https://docs.pipenv.org)):

```zsh
➜  ~ pip install mimesis
```

Also you can install it manually, using [make](https://www.gnu.org/software/make/):

```zsh
(env) ➜ git clone git@github.com:lk-geimfari/mimesis.git
(env) ➜ cd mimesis/
(env) ➜ make install
```

## Getting started

As we said above, this library is really easy to use. A simple usage example is given below:

```python
>>> from mimesis import Personal
>>> from mimesis.enums import Gender
>>> person = Personal('en')

>>> person.full_name(gender=Gender.FEMALE)
'Antonetta Garrison'

>>> person.occupation()
'Backend Developer'

>>> templates = ('UU.d', 'UU_d', 'UU-d',
...              'U_d', 'U-d', 'l_d', 'l-d')
>>> for template in templates:
...     person.username(template=template)

'GuernseyBuccan.1906'
'ScarpedErbach_2055'
'BathedAnthonin-1824'
'Adders_1893'
'Abdel-1888'
'constructor_1884'
'chegre-2051'
```

## Locales

You can specify a locale when creating providers and they will return data that is appropriate for the language or country associated with that locale:

```python
>>> from mimesis import Personal

>>> de = Personal('de')
>>> fr = Personal('fr')
>>> pl = Personal('pl')

>>> de.full_name()
'Sabrina Gutermuth'

>>> fr.full_name()
'César Bélair

>>> pl.full_name()
'Światosław Tomankiewicz'
```

Mimesis currently includes support for 33 different locales. See details for more information.

<details>
<!-- toc -->

| №  | Flag  | Code       | Name                 | Native name |
|--- |---   |---       |---                 |---         |
| 1  | 🇨🇿   |  `cs`      | Czech                | Česky       |
| 2  | 🇩🇰   |  `da`      | Danish               | Dansk       |
| 3  | 🇩🇪   |  `de`      | German               | Deutsch     |
| 4  | 🇦🇹   |  `de-at`   | Austrian German      | Deutsch     |
| 5  | 🇨🇭   |  `de-ch`   | Swiss German         | Deutsch     |
| 6  | 🇬🇷   |  `el`      | Greek                | Ελληνικά    |
| 7  | 🇺🇸   |  `en`      | English              | English     |
| 8  | 🇦🇺   |  `en-au`   | Australian English   | English     |
| 9  | 🇨🇦   |  `en-ca`   | Canadian English     | English     |
| 10 | 🇬🇧   |  `en-gb`   | British English      | English     |
| 11 | 🇪🇸   |  `es`      | Spanish              | Español     |
| 12 | 🇲🇽   |  `es-mx`   | Mexican Spanish      | Español     |
| 13 | 🇪🇪   |  `et`      | Estonian             | Eesti       |
| 14 | 🇮🇷   |  `fa`      | Farsi                | فارسی       |
| 15 | 🇫🇮   |  `fi`      | Finnish              | Suomi       |
| 16 | 🇫🇷   |  `fr`      | French               | Français    |
| 17 | 🇭🇺   |  `hu`      | Hungarian            | Magyar      |
| 18 | 🇮🇸   |  `is`      | Icelandic            | Íslenska    |
| 19 | 🇮🇹   |  `it`      | Italian              | Italiano    |
| 20 | 🇯🇵   |  `ja`      | Japanese             | 日本語       |
| 21 | 🇰🇿   |  `kk`      | Kazakh               | Қазақша     |
| 22 | 🇰🇷   |  `ko`      | Korean               | 한국어       |
| 23 | 🇳🇱   |  `nl`      | Dutch                | Nederlands  |
| 24 | 🇧🇪   |  `nl-be`   | Belgium Dutch        | Nederlands  |
| 25 | 🇳🇴   |  `no`      | Norwegian            | Norsk       |
| 26 | 🇵🇱   |  `pl`      | Polish               | Polski      |
| 27 | 🇵🇹   |  `pt`      | Portuguese           | Português   |
| 28 | 🇧🇷   |  `pt-br`   | Brazilian Portuguese | Português Brasileiro |
| 29 | 🇷🇺   |  `ru`      | Russian              | Русский     |
| 30 | 🇸🇪   |  `sv`      | Swedish              | Svenska     |
| 31 | 🇹🇷   |  `tr`      | Turkish              | Türkçe      |
| 32 | 🇺🇦   |  `uk`      | Ukrainian            | Український |
| 33 | 🇨🇳   |  `zh`      | Chinese              | 汉语         |

<!-- tocstop -->
</details>

<br>

## Data providers

Mimesis support over twenty different data providers available, which can produce data related to food, people, computer hardware, transportation, addresses, and more. See details for more information.

| №   | Provider       | Description                                                  |
|---  | ------------- |:-------------                                                  |
| 1   | `Address(*args, **kwargs)`         | Address data (street name, street suffix etc.)               |
| 2   | `Business(*args, **kwargs)`        | Business data (company, company_type, copyright etc.)        |
| 3   | `Code(*args, **kwargs)`            | Codes (ISBN, EAN, IMEI etc.)                                 |
| 4   | `ClothingSizes(*args, **kwargs)`   | Clothing sizes (international sizes, european etc.)          |
| 5   | `Cryptographic(*args, **kwargs)`   | Cryptographic data                                           |
| 6   | `Datetime(*args, **kwargs)`        | Datetime (day_of_week, month, year etc.)                     |
| 7   | `Development(*args, **kwargs)`     | Data for developers (version, programming language etc.)     |
| 8   | `File(*args, **kwargs)`            | File data (extension etc.)                                   |
| 9   | `Food(*args, **kwargs)`            | Information on food (vegetables, fruits, measurements etc.)  |
| 10  | `Games(*args, **kwargs)`           | Games data (game, score, pegi_rating etc.)                   |
| 11  | `Payment(*args, **kwargs)`         | Payment data (credit_card, credit_card_network etc.)         |
| 12  | `Personal(*args, **kwargs)`        | Personal data (name, surname, age, email etc.)               |
| 13  | `Text(*args, **kwargs)`            | Text data (sentence, title etc.)                             |
| 14  | `Transport(*args, **kwargs)`       | Dummy data about transport (truck model, car etc.)           |
| 15  | `Science(*args, **kwargs)`         | Scientific data (math_formula, rna, dna etc.)                |
| 16  | `Structured(*args, **kwargs)`      | Structured data (html, css etc.)                             |
| 17  | `Internet(*args, **kwargs)`        | Internet data (facebook, twitter etc.)                       |
| 18  | `Hardware(*args, **kwargs)`        | The data about the hardware (resolution, cpu, graphics etc.) |
| 19  | `Numbers(*args, **kwargs)`         | Numerical data (floats, primes, digit etc.)                  |
| 20  | `Path(*args, **kwargs)`            | Provides methods and property for generate paths             |
| 21  | `UnitSytem(*args, **kwargs)`       | Provides names of unit systems in international format       |
| 22  | `Generic(*args, **kwargs)`         | All at once                                                  |

When you only need to generate data for a single locale, use the `Generic()` provider, and you can access all providers of Mimesis from one object.

```python
>>> from mimesis import Generic
>>> from mimesis.enums import TLDType
>>> g = Generic('es')

>>> g.datetime.month()
'Agosto'

>>> g.food.fruit()
'Limón'

>>> g.internet.top_level_domain(TLDType.GEOTLD)
'.moscow'
```

## Custom Providers
You also can add custom provider to `Generic()`, using `add_provider()` method:

```python
>>> from mimesis import Generic
>>> from mimesis.providers import BaseProvider
>>> generic = Generic('en')

>>> class SomeProvider(BaseProvider):
...     class Meta:
...         name = "some_provider"
...
...     def hello(self):
...         return "Hello!"

>>> class Another(BaseProvider):
...     def bye(self):
...         return "Bye!"

>>> generic.add_provider(SomeProvider)
>>> generic.add_provider(Another)

>>> generic.some_provider.hello()
'Hello!'

>>> generic.another.bye()
'Bye!'
```

or multiple custom providers using method `add_providers()`:

```python
>>> generic.add_providers(SomeProvider, Another)
```

Too lazy to search for data? No problem, we found them for you and collected them [here](https://github.com/mimesis-lab/mimesis-extra-data).


## Builtins specific data providers

Some countries have data types specific to that country. For example «[Social Security Number](https://en.wikipedia.org/wiki/Social_Security_number)» (SSN) in the United States of America (`en`), and «[Cadastro de Pessoas Físicas](https://en.wikipedia.org/wiki/Cadastro_de_Pessoas_Físicas)» (CPF) in Brazil (`pt-br`).
If you would like to use these country-specific providers, then you must import them explicitly:

```python
>>> from mimesis import Generic
>>> from mimesis.builtins import BrazilSpecProvider

>>> generic = Generic('pt-br')
>>> generic.add_provider(BrazilSpecProvider)
>>> generic.brazil_provider.cpf()
'696.441.186-00'
```

You can use specific-provider without adding it to `Generic()`:

```python
>>> BrazilSpecProvider().cpf()
'712.455.163-37'
```

## Generating data by schema
For generating data by schema, just create instance of  `Field` object, which take any string which represents name of the any method of any supported data provider (see «[API reference](http://mimesis.readthedocs.io/#contents)») and the `**kwargs` of the method, after that you should describe the schema in lambda function and pass it to object `Schema` and call method `create()`:

```python
>>> from mimesis.schema import Field, Schema
>>> from mimesis.enums import Gender
>>> _ = Field('en')
>>> description = (
...     lambda: {
...         'id': _('uuid'),
...         'name': _('word'),
...         'version': _('version', pre_release=True),
...         'timestamp': _('timestamp', posix=False),
...         'owner': {
...             'email': _('email', key=str.lower),
...             'token': _('token'),
...             'creator': _('full_name', gender=Gender.FEMALE),
...         },
...     }
... )
>>> schema = Schema(schema=description)
>>> schema.create(iterations=1)
```

Output:

```python
[
  {
    "owner": {
      "email": "aisling2032@yahoo.com",
      "token": "cc8450298958f8b95891d90200f189ef591cf2c27e66e5c8f362f839fcc01370",
      "creator": "Veronika Dyer"
    },
    "version": "4.3.1-rc.5",
    "name": "pleasure",
    "id": "33abf08a-77fd-1d78-86ae-04d88443d0e0",
    "timestamp": "2018-07-29T15:25:02Z"
  }
]
```

Mimesis support generating data by schema only starting from version `1.0.0`.

## How to Contribute

1. Take a look at [contributing guidelines](https://github.com/lk-geimfari/mimesis/blob/master/CONTRIBUTING.md).
2. Check for open issues or open a fresh issue to start a discussion around a feature idea or a bug.
3. Fork the repository on GitHub to start making your changes to the **your_branch** branch.
4. Add yourself to the list of [CONTRIBUTORS](https://github.com/lk-geimfari/mimesis/blob/master/CONTRIBUTORS.md).
5. Send a pull request and bug the maintainer until it gets merged and published.


## License
Mimesis is licensed under the MIT License. See [LICENSE](https://github.com/lk-geimfari/mimesis/blob/master/LICENSE) for more information.

## Disclaimer
The authors assume no responsibility for how you use this library data generated by it. This library is designed only for developers with good intentions. Do not use the data generated with Mimesis for illegal purposes.
