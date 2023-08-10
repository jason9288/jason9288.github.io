---
title : Chirpy 테마로 GitHub 블로그 만들기 ③
date : '2023-08-09'
category : [Blog]
tags : [chirpy, github, blog, git, gitblog, vscode]
---


블로그를 일단 만들긴 했는데 뭔가 밋밋하고, 내 입맛대로 꾸미고 싶은 충동이 들었습니다.  
그래서 이번 포스트에서는 chirpy 테마 커스터마이징에 대해 정리하겠습니다.  
필요한 부분에서 원하는대로 수정해봅시다.

1. 아바타 (프로필) 바꾸기
2. 블로그 제목, 부제목 편집
3. 사이드바 편집
4. 파비콘 편집
5. 블로그 메인 컬러 변경

<br>
<br>


## 1. 아바타 바꾸기

프로필 사진이 아무것도 없어 심심해 보입니다. 원하는 이미지를 등록해봅시다. 

`_config.yml` 을 엽니다. (jekyll admin의 configuration 탭에서 편집해도 됩니다.)  
avatar 항목에 이미지 경로를 적어 넣습니다.  
![ava](/assets/img//post3/avatarvsc.png)

이미지는 `/블로그저장소/assets/img/` 디렉토리에 저장합니다. 또는 외부 인터넷 링크를 입력합니다.

<br>

## 2. 타이틀 편집

블로그 타이틀의 폰트/색상 편집은 `_sass/addon/commons.scss` 에서 이루어집니다.  
![title](/assets/img/post3/title.png)
저는 폰트 색상 정도만 변경했습니다.
  

<br>

## 3. 사이드바 편집 

### 사이드바 디자인 변경

물론 chirpy의 기본 디자인도 맘에 들지만, 아무래도 사용하는 분들이 많은 테마다보니 나름의 특색이 있어야 하지 않나 싶습니다.  
사이드바 디자인만 바꿔도 딱 차별화가 되겠죠? 한번 편집해봅시다.  

역시 `commons.scss` 파일을 엽니다. `#sidebar` 를 검색하며 아래와 같은 라인을 찾습니다.  
![ddd](/assets/img/post3/sideva.png)
원하는 이미지를 넣고 싶다면 빨간 네모친 부분처럼 바꿔줍니다.  
`url`에는 로컬 이미지 경로를 적습니다. `/assets/img`의 디렉토리입니다. 외부 링크 연결도 가능합니다.   
<br>
`background-size` 는 `auto`로 두되, `n% n%`의 원하는 비율로도 설정이 가능합니다.

아니면 특정 색상이나 그라데이션 배경으로 설정도 가능합니다.  
단색 배경을 사용하려면 다음과 같이 변경합니다.
```css
/* background: var(--sidebar-bg);*/
background: rgb(0, 0, 0)
```
원하는 숫자를 집어넣으시면 됩니다. 또는 헥스 코드를 사용해도 됩니다.  

그라데이션 배경을 넣고 싶다면 [CSS Gradient](https://cssgradient.io/)를 참조하여 코드를 복사, 붙여넣기합니다.

{:.prompt-tip}
> 다크 모드와 라이트 모드에서의 설정을 달리 하려면, `common.scss` 파일은 기본값 그대로 두고 `/_sass/colors/`의 `dark-typography.scss`와 `light-typography.scss` 파일을 열어   
> `--sidebar-bg` 항목에 상기한 방식처럼 편집하면 됩니다.

<br>

### 사이드바 텍스트 편집

사이드바 디자인을 바꾸었더니 원래 있던 글씨가 잘 보이지 않는 문제가 발생할 수도 있습니다.    

{:.prompt-warning}
> 아래 방법은 라이트/다크 모드에 동시 적용됩니다.  
> 각각 따로 변경하고자 한다면 `dark-typography.scss`와 `light-typography.scss` 에 있는 해당 색상 변수를 편집하셔야 합니다.  
>

다시 `commons.scss` 를 수정합니다. 아래 빨간 네모 구역처럼 바꿉니다.  

노란색 네모친 부분이 없다면 똑같이 추가해주세요. 기본 텍스트/아이콘 설정을 편집하는 부분입니다.
![](/assets/img/post3/textedit.png)
* `hover`: 마우스가 해당 항목 위에 있을 때의 설정을 구성합니다.  
* `active`: 선택된 항목의 설정을 구성합니다. 
  
  
* `span`: 텍스트 설정입니다. 'Home', 'Categories' 등등..  
* `i`: 아이콘 설정입니다.    


좌측 하단의 조그만 버튼도 색상을 맞춥니다. 같은 파일 내의 아래 빨간 부분을 수정합니다.
![](/assets/img/post3/buttoncolor.png)  



위 설명에 따라 이리저리 색상을 맞추어봅시다. 


<br>

## 4. 파비콘 편집

<br>

![favicon](/assets/img/post3/favicon.png)

우리가 인터넷을 할 때 보는 이 조그만 아이콘이 파비콘입니다.   
내 입맛대로 수정해봅시다.<br>

### 이미지 찾기

파비콘으로 쓸만한 이미지를 찾아야 합니다. 이미 있는 분들은 스킵하셔도 됩니다.   
[Iconfinder.com](https://www.iconfinder.com/)에서 무료 일러스트를 다운받을 수 있습니다.

<img src="/assets/img/post3/vscodeno.png" width='70' height='70'>
<center>저는 이 아이콘으로 정했습니다.</center>  

<br>

### 파비콘 변환  

<br>

![](/assets/img/post3/makfac.png)
[favicon generator](https://www.favicon-generator.org/)에서 다운받은 이미지를 파비콘으로 변환합니다.    

<img src="/assets/img/post3/favlis.png" width="50%" height="50%">  

다운받은 압축파일을 열어 이름이 `favicon`으로 시작하는 것만 복사해서 `/assets/img/favicon` 폴더에 붙여넣습니다. __이미 있는 파일을 대치합니다__.

<br>

### 로컬에서 체크

<br>

![favchk](/assets/img/post3/facchek.png)

정상적으로 적용이 되었습니다.

<br>

## 5. 블로그 메인 컬러 변경

메인 컬러를 바꾼 사이드바와 어울리는 컬러로 변경해봅시다.   
저는 초록색 배경이니 초록색으로 바꾸어 보겠습니다.

색깔을 다크 모드와 라이트 모드 두가지에 따로 설정하겠습니다.  
먼저 `/_sass/colors` 디렉토리의 `dark-typography.scss` 파일을 엽니다. 
![](/assets/img/post3/darkcolo.png)
`--link-color` 항목을 수정합니다. rgb또는 헥스 코드를 적습니다.  

마찬가지로 `light-typography.scss`도 수정합니다. 

<br>

수정 후 로컬에서 테스트하고, 제대로 동작하면 git에 푸시합니다.

<br>

## 6. 완료!

<br>

![](/assets/img/post3/giphy.gif)

이제 대강의 커스터마이징도 완료했습니다.   
물론 이것 말고도 `commons.scss`를 둘러보며 본인이 원하는 항목을 편의대로 수정해도 좋습니다. ~~하지만 전 귀찮아서~~

다음 포스트에서는 댓글 기능 구현, 구글 애널리틱스 등록 등에 관한 내용을 다루겠습니다. 

만약 잘 안되는 부분을 알려주세요. 짧은 지식을 총동원해 최대한 도움이 되는 선에서 답변해드리겠습니다.

<br>

## Useful Links 

[Chirpy 테마 커스터마이징 \| 하얀눈길 블로그](https://www.irgroup.org/posts/Chirpy-%ED%85%8C%EB%A7%88-%EC%BB%A4%EC%8A%A4%ED%84%B0%EB%A7%88%EC%9D%B4%EC%A7%95/)  
[블로그 커스터마이징 하기 \| Dodev](https://wlqmffl0102.github.io/posts/Customizing-Blogs/)

