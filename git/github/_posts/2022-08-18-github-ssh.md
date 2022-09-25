---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title:  "GitHub ssh 접속 설정"
toc: true
toc_sticky: true
toc_label: 목차
tag: "GitHub"
depth: 
  - title: "Git"
    url: /git/
    icon: "fab fa-github"
  - title: "GitHub"
    url: /git/github/
    icon: "far fa-folder-open"
---
## ssh
원격 컴퓨터에 접속하기 위한 protocol  
id, password 가 필요없으며 public key를 외부에 두어 통신  

SSH를 통해 Git 저장소에 연결하여 HTTPS 인증을 사용하여 안전하게 연결  
Git 자격 증명 관리자 또는 개인용 액세스 토큰을 사용하는 것을 권장

![Image](https://drive.google.com/uc?export=view&id=1vZV2EJ_WSJPRZGa6et0QJwN7A2veFizf)  

## SSH 키 만들기
### 만들기 전에 이미 있는지 확인하자.
![Image](https://drive.google.com/uc?export=view&id=1nvs6b5tIz0LD4iBlvQKB4Adq7nH2UGvv)  

* id_rsa
* id_rsa.pub
> ssh 폴더는 기본으로 숨겨져 있다.


#### macOS
```
/Users/username/.ssh/
```

#### windows
```
/c/Users/username/.ssh/
```

### ssh-keygen
SSH와 함께 사용할 3072비트 RSA 키 생성
![Image](https://drive.google.com/uc?export=view&id=1FwANjgI9QkC0B-fLu0VOXlXjzAYRUL0j)  
```
ssh-keygen -C "{user@email.com}"
```

> 암호는 private key에 대한 보안 계층을 제공<br/>
재 연결 시 암호를 입력할 필요가 없도록 캐시하도록<br/>
키체인에 저장 또는 [<i class="fas fa-link"></i> ssh-agent를 구성](https://docs.microsoft.com/ko-kr/azure/devops/repos/git/use-ssh-keys-to-authenticate?view=azure-devops#rememberpassphrase){:target="_blank"}

## 생성된 두개의 ssh key 확인
private key, public key로 쌍으로 키를 관리하며 이를 통해 안전하게 통신

### private key
* id_rsa
클라이언트에 저장해 놓는다.  
> 외부로 전송 금지

### public key
* id_rsa.pub


> .pub 가 public key

잘 업로드가 되었다면 public key는 웹브라우저에서 확인이 가능하다.
![Image](https://drive.google.com/uc?export=view&id=1aVbKh4ubZvgmg0HDxrIoc2bEO6c4R0xA)  

```
https://github.com/{username}.keys
```
![Image](https://drive.google.com/uc?export=view&id=1DY4cvXWKAL0xxz83G2D92f0bdr5xdFH2)  

## ParseBoard에 public key 복사하기
터미널에서 아래 명령어를 입력하자.
```
pbcopy < ~/.ssh/id_rsa.pub
```

## GitHub에 등록하기
GitHub에 로그인하여 Setting에 등록한다.
```
Github / Settings / SSH and GPG keys / SSH Keys
```
![Image](https://drive.google.com/uc?export=view&id=114dRmdetz-BzXzhSINWcGc6BKfKZiuaU)  
복사한 public key를 `New SSH key` 를 통해 등록하자.

### 잘 연동이 되었는지 확인
터미널에서 clone 명령어를 실행해보자.
```
git clone git@github.com:{username}/{repository}.git
```

## 필자가 만난 오류
![Image](https://drive.google.com/uc?export=view&id=1OJ42P30yhEjw4fJa7bG-Smi9SZC9q7Hp)  
### terminal prompts disabled
#### For Github:

```
git config --global --add url."git@github.com:".insteadOf "https://github.com/"
```
#### For Gitlab:
```
git config --global --add url."git@gitlab.com:".insteadOf "https://gitlab.com/"
```

### Permission denied (publickey) 오류 발생
ssh-agent에 ssh 개인키를 추가
```
ssh-add -K ~/.ssh/id_rsa
```

그래도 해결이 안된다면 github docs [<i class="fas fa-link"></i> Error: Permission denied (publickey)](https://docs.github.com/en/authentication/troubleshooting-ssh/error-permission-denied-publickey){:target="_blank"}를 참고하자.


### Xcode SPM authentication failed because no credentials provided
```
git config --global --edit

[url "git@github.com:"]
    insteadOf = https://github.com/
```
그래도 해결이 안된다면
```
git config --global --unset-all url.git@github.com:.insteadof
```
