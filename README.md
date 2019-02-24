# bocfx
An package for getting foreign exchange rate from Bank of China.


## Installation

```
### Required packages
# pip3 install -U requests scrapy tqdm prettytable numpy matplotlib

pip3 install bocfx
```

## Basic Usage
#### As stand-alone	 application

```
~
❯ bocfx                        
100%|████████████████████████████████████████████| 5/5 [00:00<00:00, 471.66it/s]


+-----+--------+--------+--------+--------+---------------------+
|  5  | SE_BID | BN_BID | SE_ASK | BN_ASK |         Time        |
+-----+--------+--------+--------+--------+---------------------+
| GBP | 873.83 | 846.68 | 880.27 | 882.41 | 2019-02-24 10:30:00 |
| EUR | 758.58 | 735.01 | 764.18 | 765.87 | 2019-02-24 10:30:00 |
| USD | 670.24 | 664.79 | 673.08 | 673.08 | 2019-02-24 10:30:00 |
| CAD | 508.86 | 492.79 | 512.61 | 513.85 | 2019-02-24 10:30:00 |
| AUD | 477.14 | 462.31 | 480.65 | 481.82 | 2019-02-24 10:30:00 |
+-----+--------+--------+--------+--------+---------------------+
(SE = Spot Exchange, BN = Banknote)

~
❯ 
```

#### As module

```python
>>> from bocfx import bocfx

>>> output = bocfx()
100%|████████████████████████████████████████████| 5/5 [00:00<00:00, 532.87it/s]

>>> output
[[5, 'SE_BID', 'BN_BID', 'SE_ASK', 'BN_ASK', 'Time'], ['GBP', '873.83', '846.68', '880.27', '882.41', '2019-02-24 10:30:00'], ['EUR', '758.58', '735.01', '764.18', '765.87', '2019-02-24 10:30:00'], ['USD', '670.24', '664.79', '673.08', '673.08', '2019-02-24 10:30:00'], ['CAD', '508.86', '492.79', '512.61', '513.85', '2019-02-24 10:30:00'], ['AUD', '477.14', '462.31', '480.65', '481.82', '2019-02-24 10:30:00']]
```

## Advanced Usage
#### As stand-alone	 application

```Bash
bocfx {-f|--fx} {-s|--sort} {-t|--time} {-p|--plot} {-c|--csv} {-o|--op}
```

###### Example 01:

```Bash
❯ bocfx -f GBP,USD,AUD -s ASK -t 30 -p -c -o '~/desktop/output'
100%|█████████████████████████████████████████████| 3/3 [00:03<00:00,  1.08s/it]
100%|████████████████████████████████████████| 199/199 [00:00<00:00, 422.62it/s]

+-----+--------+--------+---------------------+
|  3  | SE_ASK | BN_ASK |         Time        |
+-----+--------+--------+---------------------+
| GBP | 880.27 | 882.41 | 2019-02-24 10:30:00 |
| USD | 673.08 | 673.08 | 2019-02-24 10:30:00 |
| AUD | 480.65 | 481.82 | 2019-02-24 10:30:00 |
| GBP | 880.27 | 882.41 | 2019-02-24 05:30:00 |
| USD | 673.08 | 673.08 | 2019-02-24 05:30:00 |
| AUD | 480.65 | 481.82 | 2019-02-24 05:30:00 |
...
| GBP | 889.64 | 891.8  | 2019-01-25 00:00:05 |
| USD | 680.4  | 680.4  | 2019-01-25 00:00:05 |
| AUD | 484.37 | 485.56 | 2019-01-25 00:00:05 |
+-----+--------+--------+---------------------+
(SE = Spot Exchange, BN = Banknote)

.csv has already saved to /Users/bob/desktop/output/[GBP+USD+AUD]SE_ASK+BN_ASK_2019-01-25_2019-02-24.csv

Plot has already saved to /Users/bob/desktop/output/[GBP+USD+AUD]SE_ASK+BN_ASK_2019-01-25_2019-02-24.png
```
![](https://github.com/bobleer/bocfx/raw/master/images/%5BGBP%2BUSD%2BAUD%5DSE_ASK%2BBN_ASK_2019-01-25_2019-02-24.png)

#### As module

```python
from bocfx import bocfx

bocfx(FX=0, sort=0, time=-1, plot=0, csv=0, pt=0, op='~/bocfx_output')
```

## MIT Licence

Copyright (c) 2018 The Python Packaging Authority

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

