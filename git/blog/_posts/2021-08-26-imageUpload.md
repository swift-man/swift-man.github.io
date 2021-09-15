---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title: "블로그에 이미지 올리기"
toc: true
toc_sticky: true
toc_label: 목차
depth: 
  - title: "Git"
    url: /git/
    icon: "fab fa-github"
  - title: "Blog"
    url: /git/blog/
    icon: "far fa-folder-open"
---
블로그에 이미지를 업로드하는 방법은 여러가지가 있다.  
나의 경우 추후 Github 용량을 고려하여 Google Drive 를 쓰기로 했다.

## 링크 만들기
구글 드라이브에 이미지를 업로드 하자.
![Image](https://drive.google.com/uc?export=view&id=1ofLmA9slWa9shjtZtoSNHsPkWLXC5ynY)  



![Image](https://drive.google.com/uc?export=view&id=1FN7DqMxK2PDohPq7d0pSLL2-1RKOrPR_)  
모두에게 공유로 링크를 만들면 아래와 같은 링크가 나온다.  
```
ex) https://drive.google.com/file/d/1CuhXzbSrIdJjjs4DpbOl_O18oKV4FiL_/view?usp=sharing
https://drive.google.com/file/d/{ id }/view?usp=sharing
```

이것을 실제 이미지 주소로 가져와야 하는데 URL 룰은 아래와 같다.
```
ex) https://drive.google.com/uc?export=view&id=1CuhXzbSrIdJjjs4DpbOl_O18oKV4FiL_
https://drive.google.com/uc?export={ id }
```

## Markdown 문법으로 post 에 붙이기
```
![Image](https://drive.google.com/uc?export=view&id=1CuhXzbSrIdJjjs4DpbOl_O18oKV4FiL_)
```
이미지 태그를 추가해서 이미지가 나오는지 확인하자.

## MacOS 용 이미지 컨버터 툴 만들기
나의 경우는 하나하나 만들고 이미지를 올리기 까지 반복되는 작업이 귀찮아 툴을 하나 만들었다.  
처음엔 입력받을 URL 칸을 10개정도 두었다. 보통 한번에 포스팅할때 이미지가 10장 이하로 들어갈 것이라고 생각했다.
![Image](https://drive.google.com/uc?export=view&id=1Vuq90K4Fief7QpVh1zx2Csw4o7riRTSl)

![Image](https://drive.google.com/uc?export=view&id=19Exl8TnNTK33gHtPqR_bH65hwKpN7Osl)
구글드라이브에서 생성한 공유 URL 을 넣고
![Image](https://drive.google.com/uc?export=view&id=1FyviyQeFPTTjqe2hQTjX_KNfi8eoCvgT)
Convert 버튼을 누르면 변경 해준다.

실제로 계속 사용 중인데 너무너무 편하다. 다만 Convert 버튼의 위를 변경해줘야 겠다.  

프로그램 배포는 아쉽게도 어려워 코드를 공개해 놓았다.
[<i class="fas fa-link"></i> 소스보기](https://github.com/swift-man/GoogleDriveOriginalURL)
