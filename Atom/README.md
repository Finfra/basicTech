# 1. Link
* 텍스트 에디터 Atom(아톰)의 설치와 기본설정 : http://dovetail.tistory.com/62
* Atom Editor(Opentutorials) : https://opentutorials.org/module/1579
* Essential Atom Packages : http://blog.hswolff.com/essential-atom-packages/


# Tip
* Split Screen in Atom Editor : cmd-k + arrow key

# Plugin
## remote-edit-ni
* -----END OPENSSH PRIVATE KEY----- 타입을 지원하지 않아. key 생성시 "ssh-keygen -m PEM -f mykey -N ''" 방식으로 키생성해야 함.
* Putty용 파일은 puttygen 사용
* cf) ppk를 -----BEGIN RSA PRIVATE KEY----- 타입으로 바꾸기
```
puttygen c.ppk -O private-openssh-new -o cx
puttygen c.ppk -O private-openssh     -o cx
puttygen c     -O private             -o cx

```
