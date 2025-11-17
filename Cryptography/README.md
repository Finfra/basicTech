# 비대칭 암호화

## 개요

비대칭 암호화(공개키 암호화)는 공개키와 개인키 한 쌍을 사용하는 암호화 방식입니다.
공개키로 암호화한 데이터는 개인키로만 복호화할 수 있으며, 안전한 통신과 디지털 서명에 사용됩니다.

## 주요 개념

### 대칭 암호화 vs 비대칭 암호화

**대칭 암호화**
- 암호화와 복호화에 같은 키 사용
- 빠른 속도
- 키 배포 문제

**비대칭 암호화**
- 공개키와 개인키 쌍 사용
- 느린 속도
- 안전한 키 교환

### 주요 알고리즘

**RSA (Rivest-Shamir-Adleman)**
- 가장 널리 사용되는 비대칭 암호화
- 키 길이: 2048bit, 4096bit
- 디지털 서명 및 키 교환

**ECC (Elliptic Curve Cryptography)**
- 타원 곡선 기반
- RSA보다 짧은 키로 동일한 보안 수준
- 모바일 환경에 적합

### 활용 사례

- **HTTPS/TLS**: 웹 통신 암호화
- **SSH**: 안전한 원격 접속
- **디지털 서명**: 문서 무결성 및 인증
- **PGP/GPG**: 이메일 암호화

## 실습 예제

### SSH 키 생성 및 사용
```bash
# RSA 키 쌍 생성 (2048bit)
ssh-keygen -t rsa -b 2048 -C "your_email@example.com"

# ED25519 키 생성 (더 안전하고 빠름)
ssh-keygen -t ed25519 -C "your_email@example.com"

# 공개키 확인
cat ~/.ssh/id_rsa.pub

# SSH로 서버 접속
ssh user@server.com

# 공개키를 서버에 등록
ssh-copy-id user@server.com
```

### Python에서 RSA 사용 (cryptography 라이브러리)
```python
from cryptography.hazmat.primitives.asymmetric import rsa, padding
from cryptography.hazmat.primitives import hashes, serialization

# 개인키 생성
private_key = rsa.generate_private_key(
    public_exponent=65537,
    key_size=2048
)

# 공개키 추출
public_key = private_key.public_key()

# 메시지 암호화
message = b"Hello, World!"
encrypted = public_key.encrypt(
    message,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

# 메시지 복호화
decrypted = private_key.decrypt(
    encrypted,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)
```

### GPG로 파일 암호화
```bash
# GPG 키 생성
gpg --gen-key

# 공개키 목록 확인
gpg --list-keys

# 파일 암호화
gpg --encrypt --recipient your_email@example.com file.txt

# 파일 복호화
gpg --decrypt file.txt.gpg > file.txt

# 디지털 서명
gpg --sign file.txt

# 서명 검증
gpg --verify file.txt.gpg
```

## 참고 자료

- [RSA 암호화 원리](https://ko.wikipedia.org/wiki/RSA_%EC%95%94%ED%98%B8)
- [SSH 키 기반 인증](https://www.ssh.com/academy/ssh/public-key-authentication)
- [Python cryptography 문서](https://cryptography.io/en/latest/)
- [GPG 사용 가이드](https://gnupg.org/documentation/)
- [Let's Encrypt - 무료 TLS 인증서](https://letsencrypt.org/)
