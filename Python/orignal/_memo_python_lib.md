# pip
## 목적
* 쉬운 파이썬 라이브러리 설치

## 설치
```
sudo yum install epel-release
yum -y install python-pip
```

# by Category
## WebService
### Requests
* Example from : https://gosmcom.tistory.com/130

#### Request
```
import requests
r = requests.get('https://api.github.com/events')
r = requests.post('https://httpbin.org/post', data = {'key':'value'})
r = requests.put('https://httpbin.org/put', data = {'key':'value'})
r = requests.delete('https://httpbin.org/delete')
r = requests.head('https://httpbin.org/get')
r = requests.options('https://httpbin.org/get')
print(r.json())
```

#### Request with Header
```
import requests
url = 'http://www.ichangtou.com/#company:data_000008.html'
headers = {'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.95 Safari/537.36'}
response = requests.get(url, headers=headers)
print(response.content)

```

#### Request with Post(file)
```
import requests
url = 'https://httpbin.org/post'
files = {'file': open('f.png', 'rb')}
r = requests.post(url, files=files)
```


### web.py
#### 목적
###### web servivce구현을 위한
#### 설치
* by pip
```
pip install web.py
```

* by git
```
git clone git://github.com/webpy/webpy.git
mv webpy/web .
rm -rf webpy
python -c "import web;print(dir(web))"
```

* git 없으면
```
wget https://github.com/webpy/webpy/archive/master.zip
unzip master.zip
mv webpy-master/web .
rm -rf webpy-master/

python -c "import web;print(dir(web))"
```

* cf) 다 실패하면 실행하는 폴더에 web 폴더만 가져도 놓고 사용.

# by Name
## Pandas
* [_memo_python_pandas.md](./_memo_python_pandas.md)

## numpy
* [_memo_python_np.md](./_memo_python_np.md)


## Scikit-learn
### Warning for : warnings.warn(msg, category=FutureWarning)
```
import warnings
warnings.simplefilter(action='ignore', category=FutureWarning)
```

## matplotlib
* Wikidocs Matplotlib : https://wikidocs.net/book/1634
- Usage1

```
import matplotlib.pyplot as plt
import numpy
train_X = numpy.asarray([3.3,4.4,5.5,6.71,6.93,4.168,9.779,6.182,7.59,2.167,
                         7.042,10.791,5.313,7.997,5.654,9.27,3.1])
train_Y = numpy.asarray([1.7,2.76,2.09,3.19,1.694,1.573,3.366,2.596,2.53,1.221,
                         2.827,3.465,1.65,2.904,2.42,2.94,1.3])
plt.plot(train_X, train_Y, 'ro', label='Original data')
plt.plot(train_X, 0.228853 * train_X + 0.950674, label='Fitted line')
#plt.legend()
plt.show()
```

- Simple Example : 출처([^1])
```python
import matplotlib.pyplot as plt
x = range(100)
y = [ i*i for i in x]
plt.plot(x,y)
plt.show()
```
[^1]: https://wikidocs.net/book/1634

### Subplot
* Simple
```
%matplotlib inline
import matplotlib.pyplot as plt

x=range(10)
y=[i*i for i in x]

fig = plt.figure()
subplot = fig.add_subplot(1, 2, 1)
subplot.set_title('1')
subplot.plot(x,y)
subplot = fig.add_subplot(1, 2, 2)
subplot.set_title('2')
subplot.plot(y,x)


```
* With For
```
import matplotlib
plt.rc('font', family='NanumGothicCoding')
matplotlib.rcParams['axes.unicode_minus'] = False

x=range(100)
fig = plt.figure()
for i in range(2):
    for j in range(4):
        subplot = fig.add_subplot(2, 4, i*4+j + 1)
        subplot.set_title(f'{i},{j}')
        subplot.plot(x,[ (ii**(j+1)) * (i-0.5)   for ii in x ])
```
* subplot with image Array Type1
```python
fig = plt.figure()
for i in range(2):
  for j in range(4):
    subplot = fig.add_subplot(2, 4, i*2+j + 1)
    subplot.set_xticks([])
    subplot.set_yticks([])
    subplot.set_title(f'{i},{j}')
    subplot.imshow(img[i*2+j])
```

* subplot with image Array Type2
```python
count=0
fig,ax=plt.subplots(4,2)
fig.set_size_inches(15,15)
for i in range (4):
    for j in range (2):
        ax[i,j].imshow(x_test[prop_class[count]])
        ax[i,j].set_title(f'{i},{j}')
        ax[i,j].grid(False)
        ax[i,j].set_xticks([])
        ax[i,j].set_yticks([])
        count+=1
plt.tight_layout()
```

#### Minus 폰트 깨짐 문제 해결
```
import matplotlib
matplotlib.rcParams['axes.unicode_minus'] = False
```
#### 한글 사용
```
import matplotlib.pyplot as plt
x = range(100)
y = [ i*i for i in x]
plt.rcParams["font.family"] = "NanumGothicCoding"
plt.plot(x,y)
plt.xlabel('엑스')
plt.ylabel('Probability')
plt.show()
```
or
* 설치된 폰트의 이름을 알 때
```
plt.rc('font', family='Nanum Gothic Coding')
```
or
* Font파일 위치는 아는데 이름은 모를때
```
from matplotlib import font_manager
font_path="/usr/share/fonts/truetype/nanum/NanumGothicCoding.ttf"
font_name = font_manager.FontProperties(fname=font_path).get_name()
plt.rc('font', family=font_name)
```
### Imshow
```
# Color
imshow(img[:,:,1])
# Gray
imshow(np.mean(img,axis=2), cmap=plt.cm.gray)

```
### Save to Image
```
matplotlib.use(‘Agg’)
import matplotlib.pyplot as plt
plt.plot([1,2,3])
plt.savefig(‘myfig’)
```

## Seaborn
### Pair Plot
```
import seaborn as sns
iris = sns.load_dataset("iris")
sns.pairplot(iris, hue="species")
```
### FaceGrid
```
import seaborn as sns
iris = sns.load_dataset("iris")
sns.FacetGrid(iris, hue="species", height=5).map(sns.kdeplot, "petal_length").add_legend()
```

###  Violin Plot
```
sns.violinplot(x="species", y="petal_width", data=iris, size=5)
```

### Scatter plot by Groups
```
sns.scatterplot(x='petal_length',
                y='petal_width',
                hue='species', # different colors by group
                style='species', # different shapes by group
                s=100, # marker size
                data=iris)
# 출처: https://rfriend.tistory.com/414 [R, Python 분석과 프로그래밍의 친구 (by R Friend)]
```

### Multiple histograms on the same axis
```
import pandas as pd
sns.histplot(iris[iris.species == "setosa"]["petal_length"],
             color="blue", label="setosa")
sns.histplot(iris[iris.species == "versicolor"]["petal_length"],
             color="red", label="versicolor")
sns.histplot(iris[iris.species == "virginica"]["petal_length"],
             color="green", label="virginica")
# 출처: https://rfriend.tistory.com/409 [R, Python 분석과 프로그래밍의 친구 (by R Friend)]
```

### seaborn subplot
```
%matplotlib inline
import matplotlib.pyplot as plt

fig, axes = plt.subplots(nrows=2,ncols=2)
fig.set_size_inches(12, 10)

sns.violinplot(x="species", y="sepal_length", data=iris, size=5, ax=axes[0][0])
sns.violinplot(x="species", y="sepal_width", data=iris, size=5, ax=axes[0][1])
sns.violinplot(x="species", y="petal_length", data=iris, size=5, ax=axes[1][0])
sns.violinplot(x="species", y="petal_width", data=iris, size=5, ax=axes[1][1])


axes[0][0].set(title="꽃받침의 길이 ")
axes[0][1].set(title="꽃받침의 넓이")
axes[1][0].set(title="꽃잎의 길이")
axes[1][1].set(title="꽃잎의 길이")
```

## KoNLPy
### Intro
- 형태소 분석
- 홈페이지 : http://konlpy.org/ko/latest/
- github : https://github.com/konlpy/konlpy
- 한글 형태소 품사 (Part Of Speech, POS) 태그표 : kkma.snu.ac.kr/documents/?doc=postag
### Install
##### Mac

    pip install konlpy

##### Centos
```bash
    sudo yum -y install epel-release
    sudo yum -y install python-pip
    sudo yum -y groupinstall 'Development Tools'
    sudo yum -y install python-devel
```

### Sample Code
```python
from konlpy.tag import Kkma
from konlpy.utils import pprint
kkma = Kkma()
pprint(kkma.sentences(u'네, 안녕하세요. 반갑습니다.'))
pprint(kkma.nouns(u'질문이나 건의사항은 깃헙 이슈 트래커에 남겨주세요.'))
pprint(kkma.pos(u'오류보고는 실행환경, 에러메세지와함께 설명을 최대한상세히!^^'))
```




## Jupyter
### Jupyter Notebook
#### Install
```bash
pip install "ipython[notebook]"
## or
pip install jupyter
```
#### Execute
```bash
jupyter notebook --ip=0.0.0.0 --no-browser
```

### Jupyter lab
#### Execute
```bash
jupyter lab --ip=0.0.0.0 --no-browser
```

### Usage
```
from pylab import *
import numpy as np

imsave('a.png',mnist.test.images[x].reshape((28,28)))
i=imread('a.png')
axis("off")
imshow(i,cmap='gray')
show()
```


### WebUI
* Link : http://localhost:8888
* 자동접속됨

### Shortcut
|key          |Action                  |
|-------------|------------------------|
|Tab          |코드자동완성            |
|Ctrl + ]     |들여쓰기(indent)        |
|Ctrl + [     |내어쓰기(detent)        |
|Shift + Enter|다음셀선택              |
|Enter        |에디트모드 진입         |
|Shift-Enter  |run cell , select below |
|Alt-Enter    |run cell , insert below |
|Y            |to code                 |
|M            |to markdown             |
|R            |to raw                  |
|A/B          |insert cell above/­below |
|X            |cut selected cell       |
|C            |copy selected cell      |
|Shift-V      |paste cell above        |
|V            |paste cell below        |
|Z            |undo last cell deletion |
|DD           |delete selected cell    |
|Shift-M      |merge cell below        |
|L            |toggle line numbers     |


## Yaml
### PyYAML
#### install
```
## https://pyyaml.org/wiki/PyYAML
wget http://pyyaml.org/download/pyyaml/PyYAML-3.13.zip
brew install LibYAML
python setup.py --with-libyaml install
python setup.py test
```

#### Basic Code for Python
```toTest
import yaml

sample_yaml_as_dict = '''
first_dict_key: some value
second_dict_key: some other value
'''

sample_yaml_as_list = '''
#Notice here how i don't need quotes. Read the wikipedia page for more info!
- list item 1
- list item 2
'''

my_config_dict = yaml.load(sample_yaml_as_dict)
print(my_config_dict)
#Will print:
#{'second_dict_key': 'some other value', 'first_dict_key': 'some value'}

my_config_list = yaml.load(sample_yaml_as_list)
print(my_config_list)
#Will print:
#['list item 1', 'list item 2']

#Load some external config file
with open('~/my_config.yaml') as fp:
    my_configuration = yaml.load(fp)

print(my_configuration_dict)


```

### ruamel.yaml
#### to test
```
import sys
#pip install ryd
from ruamel.yaml import YAML

inp = """\
#example
name:
  # details
  family: Smith   # very common
  given: Alice    # one of the siblings
"""

yaml = YAML()
code = yaml.load(inp)
code['name']['given'] = 'Bob'

yaml.dump(code, sys.stdout)
```

## imgaug
* Augmenting images for your machine learning projects.
* Github : https://github.com/aleju/imgaug
### install
```
pip3 install imaug
```

## Jinja2
/Users/Shared/__language/Jinja2/_memo_jinja2.md
