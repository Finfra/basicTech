
# 구문
## if,for
    - for문
        for i in range(1,10):
            print i
    - if문
        x=input('su?')
        print x
        if x>10:
            print "more 10"
        else:
            print "less 10"
## Lambda
```python
map(lambda x: x**2, [0,1,2,3])
reduce(lambda x,y: x+y, [0,1,2,3])
filter(lambda x: x < 5, range(10))
```
##  DataFormat
### list
```
a=[1,2,3]
```
### Dic
```
b={"aa":1,"bb":2}
```
#### collections
```
from collections import defaultdict
d=defaultdict(lambda: None)
d["a"]       # no error, return None
```


## String Format
* cf: https://brownbears.tistory.com/421
## str.format
* from Python3
```
print( "Hi, {}".format('steve') )
print( "{0}, {1}, {0}".format('2','steve') )
print( "{id}, {name}".format(id='2',name='steve') )
```

## f-string
* from Python3.6
```
name="Steve"
print(f'Hello {name}')
```

## "*args", "*kwargs"
* **kwargs   => keyword agruments 의 줄임말 !
```python
def print_param(*args):
  print(args)
  for p in args:
    print(p)

print_param('a', 'b', 'c', 'd')

#('a', 'b', 'c', 'd')
#a
#b
#c
#d

```
* **kwargs   => keyword agruments 의 줄임말 !
```python
def print_param2(**kwargs):
  print kwargs
    print(kwargs.keys())
    print(kwargs.values())
    for name, value in kwargs.items():
      print("%s : %s" % (name, value))
print_param2(first = 'a', second = 'b', third = 'c', fourth = 'd')

#{'second': 'b', 'fourth': 'd', 'third': 'c', 'first': 'a'}
#['second', 'fourth', 'third', 'first']
#['b', 'd', 'c', 'a']
#second : b
#fourth : d
#third : c
#first : a

```


* 출처: https://leti-lee.tistory.com/2 [hongni]


## old %
```
echo '
print("   Column1, Column2")
for i in range(1,1000,40):
       print("%10.2f , %10d"%(i/3,i))
' |python > a.csv
cat a.csv

```



## Exceptioin
### Exception list
https://docs.python.org/3/library/exceptions.html
### Basic Examples
```
i=1
try:
    print(1/(3-i)^10)
except  ZeroDivisionError as err:
    print("0으로 나누지 마세요.")
    print(err)
    print(err.args)
except TypeError:
    print("type err")
except  Exception as err:
    print("--------------------")
    logging.exception('')
    print("--------------------")
    print(err.args)
else:
    print("None Error")
finally:
    print("--------------------")
```
### raise
```
try:
    raise Exception('spam', 'eggs')
except Exception as inst:
    print(type(inst))    # the exception instance
    print(inst.args)     # arguments stored in .args
    print(inst)          # __str__ allows args to be printed directly,
                         # but may be overridden in exception subclasses
    x, y = inst.args     # unpack args
    print('x =', x)
    print('y =', y)

```

# Install & Uninstall & Management
## Pytyhon3.6
```
add-apt-repository -y ppa:deadsnakes/ppa
apt install -y python3.6
apt install -y python3.6-dev
curl https://bootstrap.pypa.io/get-pip.py -o /tmp/get-pip.py
python3.6 /tmp/get-pip.py
mv /usr/local/bin/pip /usr/local/bin/pip2
rm /usr/bin/python
ln -s /usr/bin/python3.6 /usr/bin/python
ln -s /usr/local/bin/pip3.6 /usr/local/bin/pip3
ln -s /usr/local/bin/pip3.6 /usr/local/bin/pip
```
## Python3.7
```
add-apt-repository -y ppa:deadsnakes/ppa
apt install -y python3.7
apt install -y python3.7-dev
curl https://bootstrap.pypa.io/get-pip.py -o /tmp/get-pip.py
python3.7 /tmp/get-pip.py
ln -s /usr/bin/python3.7 /usr/bin/python
ln -s /usr/local/bin/pip3.7 /usr/local/bin/pip3
ln -s /usr/local/bin/pip3.7 /usr/local/bin/pip

```
## Python3.8
```
apt -y install  python3.8
apt -y install python3.8-distutils
wget https://bootstrap.pypa.io/get-pip.py
python3.8 get-pip.py
python3.8 -m pip install --user --upgrade pip
[[ -f /usr/bin/python ]]&&rm /usr/bin/python
ln -s /usr/bin/python3.8 /usr/bin/python
[[ -f /usr/bin/pip ]]&&rm /usr/bin/pip
ln -s /usr/local/bin/pip3.8 /usr/bin/pip
[[ -f /usr/bin/pip3 ]]&&rm /usr/bin/pip3
ln -s /usr/local/bin/pip3.8 /usr/bin/pip3
```

## Centos7
### Python3.7.3 & pip3
```
yum install -y wget
yum install -y gcc openssl-devel bzip2-devel libffi-devel make
wget https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tgz
tar xzf Python-3.7.3.tgz
rm -f Python-3.7.3.tgz
cd Python-3.7.3
./configure --enable-optimizations
make altinstall
python3.7 -V
ln -s /usr/local/bin/python3.7 /usr/bin/python3

wget https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py
```

## PIP
### pip 설치 안될때
```
export PIP_REQUIRE_VIRTUALENV=false
```

### Version 확인
```
pip -V
```
### upgrade
* New
```
pip install --upgrade pip
#or
/usr/local/bin/python3.7 -m pip install --upgrade pip
```
* Old
```
pip install pipupgrade
pipupgrade --latest --yes
```

###  freeze and -r
```
pip freeze > requirements.txt
#새로운 시스템으로 파일 이동후 사용하거나 ==를 >=로 바꿔서 사용
pip install -r requirements.txt
```

## AutoComplete in terminal for osx
* Source : https://nicolas.perriault.net/code/2010/python-tab-completion/
1. Append this to  "~/.profile"
```
export PYTHONSTARTUP=$HOME/.pythonrc.py
```
2. Append this to "~/.pythonrc.py"
```
try:
    import readline
except ImportError:
    print("Module readline not available.")
else:
    import rlcompleter
    readline.parse_and_bind("tab: complete")
```
3. Source it
```
source ~/.profile
```

cf) VirtualEnv에만 적용하기.
```
brew install readline python
mkvirtualenv -p $(which /python2) \
    --no-site-packages `pwd`/env
```

* Uninstall
```
sudo rm -rf /Library/Frameworks/Python.framework/Versions/2.7
sudo rm -rf "/Applications/Python 2.7"
cd /usr/local/bin/
ls -l /usr/local/bin | grep '../Library/Frameworks/Python.framework/Versions/2.7' | awk '{print $9}' | tr -d @ | xargs rm
```

## VirtualEnv
### virtualenv Basic
* 내 계정에서 virtualenv가능하게 하기
sudo apt-get install python-pip python-dev python-virtualenv
sudo apt-get install python3-pip python3-dev
pip3 install virtualenvwrapper

  * 환경 만들기
virtualenv --system-site-packages tf1

* virtualenv 셋팅 찾기
find ~/|grep activate

* virtualenv로 들어가기
workon tf1

* virtualenv 지우기
rmvirtualenv tf1

* 나가기
deactivate


### workon 방식

#### Setting
```
sudo -i
pip3 install virtualenvwrapper #apt install python-virtualenv
python3 -m pip install virtualenvwrapper
python3 -m pip install virtualenv
exit
cat <<EOF>>~/.bashrc
VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
export WORKON_HOME=~/.virtualenvs
. /usr/local/bin/virtualenvwrapper.sh
EOF
```
#### 가상환경 리스트
```
workon
```

#### 가상환경 만들기
```
mkvirtualenv p3 --python=python3
```

#### 가상환경에 들어가기
```
workon p3
```

#### 가상환경에서 나오기
```
deactivate
```

#### 가상환경 지우기
```
rmvirtualenv p3
```

#### Jupyter가능하게 하기
```
workon p3
pip install ipykernel
python -m ipykernel install --user --name=p3
```





## Conda
### Install
* Cheatsheet : https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf
* Chack New version : https://www.anaconda.com/distribution/
```
cd /tmp/
curl -O https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh
bash Anaconda3-2019.10-Linux-x86_64.sh
```
* 주의) 퍼미션 쓰기가능하게 하주기(유저권한 포함)
```
C:\Users\nowage\.conda
C:\ProgramData\Anaconda3
```


### Usage
```
conda list env
conda env list

conda create -n t1 python=3
conda activate t1

conda install numpy
conda remove numpy

deactivate
conda remove env t1
```

### Tip
* Disable Prompt if "base"
```
conda config --set auto_activate_base False
```


## Windows 환경
### 주의사항
1. windows10에 git-scm 사용시 : python을 호출 못하는 경우 있음.
2. "#!/usr/bin/env python" 문을 사용하면 안됨.
3. 경로에 xx.py를 넣어두고 실행하는 것 안됨(xx.bat에서 호출해서 사용할 것)

# Util
## pydoc
* before python3.7 : only support localhost
```
pydoc -p 9999 &
```
* after python3.7 : support external host
```
pydoc -n 0.0.0.0 -p 8080
```

# Builtin Library
## Core
### zip
```python
>>> a=[1,2,3]
>>> b=[4,5,6]
>>> zip(a,b)
[(1, 4), (2, 5), (3, 6)]
```

## struct
- Python 문자열로 표현된 C structs와 Python Value 간의 변환
- Link : http://hextracker.tistory.com/141
- 특징
    + 파일에 Binary Data를 저장하거나 Network Connection 시 사용
- 주요 Fuction
    + struct.pack(fmt,v1,v2,...)
        지정된 Format에 따라 v1,v2,..의 Values를 Pack을 수행하며 그 결과는 String으로 리턴

    + struct.unpack(fmt,string)
        지정된 Format에 따라 String을 Unpack을 수행하며 그 결과는 Tuple로 리턴

### Example
```python
import struct

def getDword(s, offset) :
    return struct.unpack("<L", s[offset:offset+4])[0]

def main():
    str = "123456789"
    tmp = getDword(str,0)
    print hex(tmp)

if __name__ == '__main__':
    main()
```
### Byte Order
|Character|Byte Order           |Size     |Alignment|
|---------|---------------------|---------|----------|
| @        |Native               |Native   |Native    |
| =        |Native               |Standard|None      |
| <        |Little-Endian        |Standard|None      |
| >        |Big-Endian           |Standard|None      |
| !        |network(=Big-Endian) |Standard|None      |

###  Format Characters
|Format|C Types           |Python Type        |Standard Size|
|------|------------------|-------------------|--------------|
| x    |Pad Byte          |No Value           |              |
| c    |char              |String of length 1 |1             |
| b    |signed char       |integer            |1             |
| B    |unsigned char     |integer            |1             |
| ?    |_Bool             |bool               |1             |
| h    |short             |integer            |2             |
| H    |unsigned short    |integer            |2             |
| i    |int               |integer            |4             |
| I    |unsigned int      |integer            |4             |
| l    |long              |integer            |4             |
| L    |unsigned long     |integer            |4             |
| q    |long long         |integer            |8             |
| Q    |unsigned long long|integer            |8             |
| f    |float             |float              |4             |
| d    |double            |float              |8             |
| s    |char[]            |string             |              |
| p    |char[]            |string             |              |
| P    |void *            |integer            |              |

## os
### os.path
```
import os
import sys
from pathlib import Path

basePath=os.path.dirname(sys.argv[0])

childPath=os.path.join(basePath,"test")

os.makedirs(childPath)
print(os.listdir(basePath))
parentPath=Path(basePath).parent
# join(os.path.abspath( join(basePath,"..") )
executedPath=os.getcwd()

os.path.isdir(basePath)

os.path.isfile(basePath)
```

## Regular Expression
### re.escape
### re.findall
```
re.findall('a','apache')
# ['a', 'a']
```

#### MultiLine Examples
```
import re
s='''
aa
bbb cc
dd
'''
re.findall('bb.*$',s,re.DOTALL)
```

### re.finditer
### re.fullmatch
### re.functools
### re.match
* 주의 정확히 일치 해야 함.
```
p=re.compile('[a-z]+')
if p.match("python"):
  print('Match')


if not re.match('a$',"ca"):
     print("Match")
else:
     print("NoMatch") # <==요게 나옴 정확히 않맞으니까.
```

### re.search/compile/group
* match Object의 메서드들
    - Method,  Descrption
    - group(), 일치된 문자열을 반환한다.
    - start(), 일치된 문자열의 시작 위치를 반환한다.
    - end(),   일치된 문자열의 끝 위치를 반환한다.
    - span(),  일치된 문자열의 (시작 위치, 끝 위치) 튜플을 반환한다.
* Example Simple
```
regex = re.compile('(a+).*(c+)')
mo = regex.search('abc')
mo.group(2)
# 'c'
```

* Example Full
```
import re

matchObj = re.search('s+', "a a ss a ssss")
print(matchObj)

regex=re.compile('(a)(b)(.*)')
mo=regex.search('abca')
print(mo.group(1))

print(matchObj.group())
# ss
print(matchObj.start())
# 4
print(matchObj.end())
# 6
print(matchObj.span())
# (4,6)
```

### re.split
### re.sub
```
re.sub(r"18|28",r"xx","She is 18, her sister is 28.")
```

### re.subn
```
re.subn(r"18|28",r"xx","She is 18, her sister is 28.")
# ('She is xx, her sister is xx.', 2)

re.subn(r"18",r"xx","She is 18, her sister is 28.")
# ('She is xx, her sister is 28.', 1)

```
### Example
```
import re
operater = '[\+|\-|\/|\*|\(|\)]+'
e="(3+4)*5"
operaters=re.findall(operater,e)
variables=re.split(operater, e)
```


## argparse
* Parser for command-line options, arguments and sub-commands
* Doc : https://docs.python.org/3.3/library/argparse.html

### Example
* Simple
```
import argparse
parser = argparse.ArgumentParser(description='---------')
parser.add_argument('filePath', metavar='path', type=str, help='Input FilePath')
parser.add_argument("-d", "--debug", action="store_true", help="Debug Mode On")
args = parser.parse_args()

print(args.filePath)
print(args.debug)
```

  * Some Complex
```
import argparse
parser = argparse.ArgumentParser(description='Process some integers.')
parser.add_argument('integers', metavar='N', type=int, nargs='+',help='an integer for the accumulator')
parser.add_argument('--sum', dest='accumulate', action='store_const',const=sum, default=max,help='sum the integers (default: find the max)')
args = parser.parse_args()
print(args.accumulate(args.integers))
print(dir(args))
```
* cf) no argparse
```
import sys
print('sys.argv 길이 : ', len(sys.argv))
for arg in sys.argv:
    print('arg value = ', arg)
```
## closure : Dynamic Function
```
def f(a=1,b=2):
    print(a,b)
      return a+b

def mf(a,b):
    def f1():
        return f(a,b)
    return f1

fn1=mf(1,1)
fn2=mf(1,2)
fn1()
fn2()
```

## json
```
import json
json_data=open('xx.json').read()
d=json.loads(json_data)

```

## dateutil
* String to Date
```python
from dateutil.parser import parse
parse('2000-01-01')
```
* Date add
```python
import datetime
from dateutil.parser import parse
d=parse('2010-01-01')-parse('2000-01-01')
print(d)
print(parse('2010-01-01') + datetime.timedelta(days=10) )
```

## pdb
* Source : http://pythonstudy.xyz/python/article/505-Python-디버깅-PDB
```
import pdb; pdb.set_trace()
```
### PDB Syntax

|PDB     |명령어	실행내용                           |
|--------|-----------------------------------|
|help    |도움말                                |
|next    |다음 문장으로 이동                         |
|print   |변수값 화면에 표시                         |
|list    |소스코드 리스트 출력. 현재 위치 화살표로 표시됨        |
|where   |콜스택 출력                             |
|continue|계속 실행. 다음 중단점에 멈추거나 중단점 없으면 끝까지 실행|
|step    |Step Into 하여 함수 내부로 들어감            |
|return  |현재 함수의 리턴 직전까지 실행                  |
|!변수명 = 값|변수에 값 재설정                          |


## pathlib.Path
* Manual : <https://docs.python.org/3/library/pathlib.html>
```
from pathlib import Path
parentPath=Path(basePath).parent
# join(os.path.abspath( join(basePath,"..") )
```

## subprocess
```
import subprocess
p = subprocess.Popen('df -h', shell=True, stdout=subprocess.PIPE)
print(str(p.communicate()[0], 'utf-8'))
```

# Examples
## for me
### 1줄 파이썬 웹서버
```
python2 -m SimpleHTTPServer 8000
```
## For Student
### 구구단 전단
```
for dan in xrange(2,10):
    print "\n %d 단 "%dan
    for x in xrange(1,10):
        print "%d x %d = %d"%(dan,x,dan*x)
```
### 높음 낮음 게임 예
```
import random
sol = random.randint(1, 100)
guess = -1
count = 0
while sol != guess:
    count += 1
    guess = input('1과 100사이의 숫자를 입력하세요 :')
    if guess < sol:
        print '더 높은 숫자를 골라보세요'
    elif guess > sol:
        print '더 낮은 숫자를 골라보세요'
    else:
        print count, '번 만에 맞췄습니다'
```
### list to 2D-Matrix
```python
a=[0.0,8.04,10.0,9.14,10.0,7.46,8.0,6.58,8.0,6.95,8.0,8.14,8.0,6.77,8.0,5.76,13.0,7.58,13.0,8.74,13.0,12.74,8.0,7.71,9.0,8.81,9.0,8.77,9.0,7.11,8.0,8.84,11.0,8.33,11.0,9.26,11.0,7.81,8.0,8.47,14.0,9.96,14.0,8.10,14.0,8.84,8.0,7.04,6.0,7.24,6.0,6.13,6.0,6.08,8.0,5.25,4.0,4.26,4.0,3.10,4.0,5.39,19.0,12.50,12.0,10.84,12.0,9.13,12.0,8.15,8.0,5.56,7.0,4.82,7.0,7.26,7.0,6.42,8.0,7.91,5.0,5.68,5.0,4.74,5.0,5.73,8.0,6.89]
it=iter(a)
rowCnt=8
x = [[i for i in range(rowCnt)] for j in range(len(a)/rowCnt)]

```
# 유용한 코드
```
cf)
pd0#
pd#
pda#
pdf#
pdm#
pic#
pis#
```
## IntroSpection
### 설치된 페키지 확인
#### pydoc
```
pydoc -n 0.0.0.0 -p 8080
```

#### by Code
* 화면 출력
```
help("modules")
```
* List로 받기
```
import sys
sys.modules.keys()
```

### list 보기
print('\n'.join(dir(m)))

### 찾기
```
import re;print('\n'.join(list(filter(re.compile('^[^ _]').match,dir(m)) )))

### 속성 찾기
__m=m;print('\n'.join([_m for _m in dir(__m) if not callable(getattr(__m,_m))]))

### 함수 찾기
__m=m;print('\n'.join([_m for _m in dir(__m) if callable(getattr(__m,_m))]))

### 모듈 찾기
import inspect;_n="m";print('\n'.join([_m for _m in dir(eval(_n)) if inspect.ismodule(eval("%s.%s"%(_n,_m) ))  ] ))

### 호출 가능한지 보기.
```
callable(getattr(m,"sin"))
```
### 객체 내용 보기.
```
import inspect;_n="m";__n=eval(_n);print("\n code     = %s \n name or value = %s \n type= %s \n isCallable = %s\n"% (_n,__n,__n.__name__ if inspect.ismodule(__n) else __n.__class__, callable(__n)))
```
### 모든 모듈 보기
* Simple
```
help("modules")
```
* Good Version
```
import sys
for module in sys.modules:
    try:
        print(module,sys.modules[module].__version__)
    except:
        try:
            if  type(modules[module].version) is str:
                print(module,sys.modules[module].version)
            else:
                print(module,sys.modules[module].version())
        except:
            try:
                print(module,sys.modules[module].VERSION)
            except:
                pass
```

## Advanced Dir
```
import pandas as pd

print('\n'.join(dir(pd)))
print('\n'.join([s for s in dir(pd) if s.find('data') >= 0 ]))
print('\n'.join([m for m in dir(pd) if callable(getattr(data,m))]))
print('\n'.join([m for m in dir(pd) if not callable(getattr(data,m))]))
print('\n'.join([s for s in dir(pd) if s.upper().find('data'.upper()) >= 0 ]))
```

## Command Line Arguments
* link : http://www.cyberciti.biz/faq/python-command-line-arguments-argv-example/
    import sys
    total = len(sys.argv)
## 폴더(Path)관련
### Path 얻기
```
import os
print (os.getcwd())                                  # 현재 디렉토리의
print (os.path.realpath(__file__))                   # 파일
print (os.path.dirname(os.path.realpath(__file__)) ) # 파일이 위치한 디렉토리
```
### 폴더 내용 출력
```
from os import listdir
from os.path import isfile, join
mypath='/data2/original'
onlyfiles = [f for f in listdir(mypath) if isfile(join(mypath, f))]
```
### 하위 폴더 리스트
```
{python3Parts}
```
### Path Codes
- http://pythonstudy.xyz/python/article/507-파일과-디렉토리
* 현재 작업 폴더 얻기,
```
os.getcwd()
```
* 디렉토리 변경,
```
os.chdir("C:\Tmp")
```
* 특정 경로에 대해 절대 경로 얻기,
```
os.path.abspath(".\\Scripts")
```
* 경로 중 디렉토리명만 얻기,
```
os.path.dirname("C:/Python35/Scripts/pip.exe")
```
* 경로 중 파일명만 얻기,
```
os.path.isfile("C:/Python35/Scripts/pip.exe"):
```
* 경로 중 디렉토리명과 파일명을 나누어 얻기,
```
os.path.basename("C:/Python35/Scripts/pip.exe"))
```
* "파일 각 경로를 나눠 리스트로 리턴하기,
```
os.path.split("C:/Python35/Scripts/pip.exe")
```
* os.path.sep은 OS별 경로 분리자",
```
os.path.sep은 OS별 경로 분리자 "C:\Python35\Scripts\pip.exe".split(os.path.sep)
```
* 경로를 병합하여 새 경로 생성,
```
os.path.join('C:\Tmp', 'a', 'b')
```
* 디렉토리 안의 파일/서브디렉토리 리스트,
```
os.listdir("C:\Python35")
```
* 파일 혹은 디렉토리 경로가 존재하는지 체크하기,
```
os.path.exists("C:\Python35")
```
* 디렉토리 경로가 존재하는지 체크하기,
```
os.path.isdir("C:\Python35")
```
* 파일 경로가 존재하는지 체크하기,
```
os.path.isfile("C:\Python35\python.exe")
```
* 파일의 크기,
```
os.path.getsize("C:\Python35\python.exe")
```

## get key from value in dictionary.
```python2
d={"기온·강수량":1,"날씨":9}
d.keys()[d.values().index(9)]
```

## 한글 딕셔너리 출력
```
    import json
    dic={"한글":33}
    print json.dumps(dic, ensure_ascii=False)
```

## 한글 딕셔너리 출력2
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import pprint
class MyPrettyPrinter(pprint.PrettyPrinter):
    def format(self, _object, context, maxlevels, level):
        if isinstance(_object, unicode):
            return "'%s'" % _object.encode('utf8'), True, False
        elif isinstance(_object, str):
            _object = unicode(_object,'utf8')
            return "'%s'" % _object.encode('utf8'), True, False
        return pprint.PrettyPrinter.format(self, _object, context, maxlevels, level)
d={'한글':1}
print MyPrettyPrinter().pprint(d)
```
* Source : http://mcchae.egloos.com/11076302#comment_11076302

## 날짜 범위를 리스트로 만들기
```python
import datetime
start = datetime.datetime.strptime("20130101","%Y%m%d")
end = datetime.datetime.strptime("20151031", "%Y%m%d")
date_generated = [start + datetime.timedelta(days=x) for x in range(0, (end-start).days)]
for date in date_generated:
    print date.strftime("%Y%m%d")
```

## 대화형 입력 : expect
```python
    import pexpect
    child = pexpect.spawn ('splunk login')
    child.sendline('admin')
    child.sendline('xxxx')
```

### 설치
```bash
    https://pypi.python.org/pypi/pexpect/ 에서 받거나
    easy_install pip
    pip pexpect
```
- 수동 설치
    ```bash
    tar xzvf pexpect-4.0.1.tar.gz
    cd pexpect-4.0.1
    python setup.py install
    ```

## list에서 Matching 해서 list인덱스 배열로 리턴하기
```
x=[11,22,33,44]
y=[11,33,22,44,44]
[x.index(i) for i in y if i in y]
```

## list → Dictionary → onehot encoding (enumerate)
```python
a=["a","b","c"]
l={ k:v for k,v in enumerate(a)}
```

## list → dictionary → onehot
```python
dictionary_data=["aa","bb","cc","dd"]

encoder_dic={ k:v for v,k in enumerate(dictionary_data)}
encoder_dic
decoder_dic={ k:v for k,v in enumerate(dictionary_data)}
decoder_dic

org_data=["aa","bb","bb","cc","cc","cc","dd","dd","dd","dd"]
encoded_data=[encoder_dic[i] for i in org_data]
encoded_data

decoded_data=[decoder_dic[i] for i in encoded_data]
decoded_data


one_hot=np.identity( len(encoder_dic.keys()) )
```

## OS명령
```
import os
print(os.system ('ls -al') )
```

## File Read
* basic Example
```
with open('~/a.txt','r') as f:
    print(f.readline())
```
* 여러줄 읽기

```
with open("~/a.txt", 'r') as f:
  while True:
    line = f.readline()
    if not line: break
    print(line)
  f.close()



# Cf
## OS명령으로 특정 내용을 포함하는 파일 찾기
* xxxx라는 문장이 있고 py확장자를 가진 파일을 하위 폴더에서 찾음.
```
find ./  -iname "*\.py" |xargs grep -ni "xxxx"
```
