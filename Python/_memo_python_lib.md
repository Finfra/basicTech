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
### Install
```python
    yum groupinstall 'Development Tools'
    <!-- yum install gcc-gfortran-4.1.2-52.el5_8.1 gcc44-gfortran-4.4.6-3.el5.1 libgfortran.x86_64 lapack.x86_64 blas.x86_64 -->
    yum install blas-devel lapack-devel
    yum install python-devel
    pip install "ipython[notebook]"
    //yum install numpyca
    pip install numpy
```
### Basic Usage
```python
import numpy as np
data = [[1,2],[3,4]]
arr=np.array(data)
arr.shape
arr.ndim
np.empty((3,3))
np.ones((3,3))
np.zeros((3,3))
np.arange(5)
## array([0, 1, 2, 3, 4])
```
### Library
|함 수                  |설 명                                                     |비고                          |
|---------------------|--------------------------------------------------------|----------------------------|
|abs, fabs            |절대값을 리턴. 복소수가 아닌 경우에는 빠른 연산을 위해 fabs를  이용한다.            |numpy.abs(arr)              |
|sqrt                 |제곱근(루트)을 계산함.                                           |numpy.sqrt(arr)             |
|square               |제곱을 계산함.                                                |numpy.square(arr)           |
|Exp                  |지수를 계산함.                                                |numpy.Exp(arr)              |
|Log                  |로그를 계산함.                                                |numpy.Log(arr)              |
|sign                 |각 원소의 부호를 계산함. 양수 : 1, 음수 : -1                          |numpy.sign(arr)             |
|ceil                 |소수를 올림으로 계산함.                                           |numpy.ceil(arr)             |
|floor                |소수를 버림으로 계산함.                                           |numpy.floor(arr)            |
|rint                 |소수를 반올림한다. type은 유지된다.                                  |numpy.rint(arr)             |
|modf                 |각 원소의 몫과 나머지를 리턴한다. 두 개의 ndarray를 리턴한다.                 |numpy.modf(arr)             |
|isnan                |숫자인지 아닌지를 판별해서 불리언 배열을 리턴한다.                            |numpy.isnan(arr)            |
|add                  |두 배열을 더한다.                                              |numpy.add(arr1, arr2)       |
|subtract             |첫 번째 배열에서 두 번째 배열을 뺀다.                                  |numpy.subtract(arr1, arr2)|
|multiply             |두 배열을 곱한다.                                              |numpy.multiply(arr1, arr2)|
|divide, floor_divide|첫 번째 배열에서 두 번째 배열을 나눈다. floor_divide는 몫만 리턴한다.          |numpy.divide(arr1, arr2)    |
|power                |첫 번째 배열의 원소를 두 번째 배열의 원소의 값 만큼 제곱한다.                    |numpy.power(arr1, arr2)     |
|maxinum, fmax        |두 배열 중 큰 값을 리턴한다. fmax는 NaN을 무시한다.                      |numpy.maximum(arr1, arr2)   |
|minimum, fmin        |두 배열 중 작은 값을 리턴한다. fmin은 NaN을 무시한다.                     |numpy.minimum(arr1, arr2)   |
|mod                  |첫 번째 배열에서 두 번째 배열을 나눈 나머지를 리턴한다.                        |numpy.mod(arr1, arr2)       |
|greater, less, equal|첫 번째 배열 원소와 두 번째 배열 원소간의 >, <, = 조건 결과를 불리언 배열로 리턴한다.|numpy.greater(arr1, arr2)   |
### Matrix Basic
```python
import numpy as np
x=np.matrix('1 2; 3 4')
np.arange(25).reshape((5, 5))
np.array(range(25)).reshape((-1, 5))
np.ndarray((5, 5))
a=np.array([[1, 2],[3, 4]])
a[1][1]

a=np.ones(12)
a.reshape(-1,3)

```
### Matrix Examples

* 2차원으로 3차원 만들기
  - 일괄 생성시 상위 차원 1 추가하기
  - 숫자 입력시 각 괄호 입력
```
i1=np.ones((1,2,2))
i2=np.array([[[1,2],[3,4]] ] )

a=np.vstack( (i11,i22,i11) )
print(f"{a.shape}\n\n{a} ")

```

* etc
```python
>>> np.abs(arr)
array([[1, 2],
       [3, 4]])
>>> np.sqrt(arr)
array([[ 1.        ,  1.41421356],
       [ 1.73205081,  2.        ]])
>>> a*a
array([[ 0.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  0.]])
>>> arr*arr
array([[ 1,  4],
       [ 9, 16]])
>>> np.dot([1,0],[[1,0,1],[1,1,np.sqrt(3)]]) # == [  [1,0] · [1,1] ,  [1,0] · [0,1] , [1,0] · [1,np.sqrt(3)]
array([ 1.,  0.,  1.])
>>> np.cross([0.,1.],[1.,0.])
array(-1.0)
>>> a1=np.array([1,2,3]).reshape( [1,3])
>>> a2=np.array([4,5,6]).reshape( [1,3])
>>> np.concatenate((a1,a2),axis=0)
array([[1, 2, 3],
       [4, 5, 6]])

```

### inv example
* y=2x+1 , y=-x+4
```
import numpy as np
a=np.array([[1, -2], [1, 1]])
b=np.array([[1], [4]])
np.dot(np.linalg.inv(a),b)
```

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
