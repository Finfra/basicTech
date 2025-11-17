# Linux 기초

## 개요

Linux는 오픈소스 Unix 계열 운영체제로, 서버, 개발 환경, 임베디드 시스템 등에서 널리 사용됩니다.
명령줄 인터페이스(CLI)를 통한 강력한 시스템 제어와 안정성으로 개발자들에게 필수적인 환경입니다.

## 주요 개념

### 파일 시스템
- 디렉토리 구조: `/`, `/home`, `/etc`, `/var`, `/usr`
- 절대 경로와 상대 경로
- 파일 권한: `rwx` (읽기, 쓰기, 실행)

### 기본 명령어
- **파일 탐색**: `ls`, `cd`, `pwd`
- **파일 조작**: `cp`, `mv`, `rm`, `mkdir`
- **파일 내용**: `cat`, `less`, `head`, `tail`
- **검색**: `find`, `grep`

### 권한 관리
- 사용자와 그룹
- `chmod`: 권한 변경
- `chown`: 소유자 변경
- `sudo`: 관리자 권한 실행

## 실습 예제

### 기본 파일 조작
```bash
# 디렉토리 생성
mkdir my_project

# 파일 생성
touch README.md

# 파일 복사
cp file1.txt file2.txt

# 파일 이동/이름 변경
mv old_name.txt new_name.txt

# 파일 삭제
rm file.txt

# 디렉토리 삭제 (재귀적)
rm -rf directory/
```

### 파일 권한 설정
```bash
# 파일 권한 확인
ls -l file.txt

# 실행 권한 추가
chmod +x script.sh

# 숫자로 권한 설정 (755 = rwxr-xr-x)
chmod 755 script.sh

# 소유자 변경
sudo chown user:group file.txt
```

### 파일 내용 검색
```bash
# 파일 내용 출력
cat file.txt

# 파일 내용에서 패턴 검색
grep "pattern" file.txt

# 디렉토리에서 파일 찾기
find . -name "*.txt"

# 프로세스 검색
ps aux | grep python
```

## 참고 자료

- [Linux Command Line Basics](https://ubuntu.com/tutorials/command-line-for-beginners)
- [리눅스 파일 시스템 계층 구조](https://www.pathname.com/fhs/)
- [Bash 스크립팅 가이드](https://www.gnu.org/software/bash/manual/)
