---
title : Chirpy 테마로 GitHub 블로그 만들기 ②
date : '2023-08-08'
categories : [Blog]
tags : [chirpy, github, blog, git, gitblog, vscode]
---


이번에는 블로그의 세부 설정을 만져보도록 하겠습니다.

1. jekyll admin 설치
2. _config.yml 수정
3. vscode로 포스팅하기  
     
정도를 다루어보겠습니다.


## 1. jekyll admin 설치

```jekyll admin```은 jekyll 플러그인 중 하나로 편리한 인터페이스를 통해 jekyll 블로그를 설정할 수 있다는 장점이 있습니다. 

설치는 매우 간단합니다. 이전에 만들어 놓은 블로그 로컬 저장소의 ```Gemfile``` 이라는 이름의 파일을 열어봅니다.

![gemfile](/assets/img/gemfile.png)
맨 밑에 한 줄을 추가합니다.
```console
gem 'jekyll-admin', group: :jekyll_plugins
```

파일을 저장합니다. 이제 터미널을 열어 밑의 내용을 입력합니다.
```shell
bundle install
```  

놀랍게도 이게 끝입니다. 로컬 서버를 열어 동작하는지 확인해 봅시다.

```shell
jekyll serve
```

```htttp://127.0.0.1:4000/admin```으로 이동하여 아래와 같은 화면이 나오면 성공입니다.  

![admin](/assets/img/admin.png)

{:.prompt-tip}

> #### Error : could not fetch the config 메시지 팝업 시  
> 위와 같은 에러가 나타나면 다음과 같이 해결합니다.  
> 로컬 저장소의 ```_config.yml``` 파일을 열고 가장 아래에 다음 내용을 추가합니다.
> ```
> jekyll_admin:
>    hidden_links:
>    homepage: ""
> ```

이후 에러가 다시 나오는지 확인합니다. 저는 이 방법으로 해결했습니다.

<br>

## 2. _config.yml 수정

jekyll 블로그의 기본적인 설정은 ```_config.yml``` 을 통해 할 수 있습니다.   
jekyll admin 페이지에서는 이를 `configuration` 탭에서 제공합니다. 

수정할 수 있는 항목은 다음과 같습니다.   
* ```lang```: 언어를 설정합니다. ```ko``` 로 변경할 수 있지만 데이터셋이 없어 효과는 없습니다. 하지만 커스터마이징이 가능하므로 변경해 둡니다.
* ```timezone```: 시간대를 설정합니다. ```Asia/Seoul``` 로 변경합니다.
* ```title```: 블로그 제목을 설정합니다. 원하는 제목을 적습니다.
* ```tagline```: 블로그 부제목을 설정합니다. 역시 원하는 내용을 적습니다.
* ```description```: 블로그가 검색될 수 있는 키워드를 적습니다.
* ```url```: 블로그 도메인입니다. ```username.github.io``` 형식으로 적습니다.
* github, twitter(X) ``username``: 본인 소셜 아이디를 적으면 됩니다.
* `social.name`: 블로그에서 쓰이는 이름입니다. 본인이 원하는 닉네임을 적습니다. 
* `social.email`: 본인 이메일을 적습니다.
  
* `google_analytics.id`: 구글 애널리틱스 아이디를 적습니다. 아직 없으면 그대로 둡니다. 이는 다음 번에 자세히 다루어보도록 하겠습니다.

* `theme_mode`: 블로그를 라이트 모드/다크 모드 중 무엇을 사용할 것인지 선택합니다. 기본값은 시스템 디폴트 값을 쓰고, 좌측 하단에 모드 간 전환 버튼이 있습니다.
* `avatar`: 블로그 좌측 상단의 프로필 이미지를 설정합니다. 외부 이미지 링크나 로컬 이미지 경로를 입력합니다.
* `toc`: 블로그 화면 오른편에 포스트 목차를 표시하는 설정입니다. 기본값은 `true` 입니다.
* `comments`: 댓글 관련 기능 설정인데, 저는 `utteranc.es` 를 이용해 댓글 기능을 만들어서 이 부분은 그대로 놔두었습니다.

당장 설정할 만한 항목은 이정도로 볼 수 있겠습니다. 내용을 변경/수정하고 로컬에서 테스트한 후, git에 푸시하여 설정을 마무리합니다. 

<br>

## 3. vscode로 포스팅하기

앞서 언급해두었지만 jekyll 블로그는 `markdown` 형식을 사용합니다. 마크다운 편집기는 무엇을 사용하셔도 상관없지만, 저는 `vscode`를 이용해서 편집하는 방법을 소개하겠습니다.

그에 앞서 jekyll admin 페이지에도 포스트 편집기가 있습니다. `Posts` 탭에서 편집기로 편집할 수 있습니다. 편집기 레이아웃이 잘 되어 있으니 이것을 사용하셔도 무방합니다. 

우선 `vscode`가 없다면 먼저 설치하고, 초기 세팅을 합시다.   
[MacOS - Visual Studio Code 설치하기](https://willnfate.tistory.com/entry/Macbook-Pro-M2-Visual-Studio-Code-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0)

실행하면 아무것도 없는 빈 창이 나타납니다.  
![vscodeno](/assets/img/vscodeno.png)

메뉴 막대의 `view` 탭에서 `Extensions` 를 클릭합니다. 또는 단축키 `Command + Shift + X` 를 통해 마켓플레이스를 엽니다.  

![vscext](/assets/img/vscmark.png)
검색창에 `markdown` 을 입력하고 `Markdown All in One`을 설치합니다.   

<br>  

이제 편집을 해 봅시다. 마켓플레이스 창을 닫고 `Command + o` 를 눌러, 블로그 로컬 저장소 폴더를 엽니다.   
![vscblog](/assets/img/vscblog.png)

`_posts` 폴더에 생성했던 테스트 md파일을 열어봅니다. 없다면 터미널을 켜서 생성해줍니다.
```shell
touch YYYY-MM-DD-TEST.md
```
![vscterm](/assets/img/vscterm.png)  

파일을 열어 아래 스크린샷의 빨간 네모친 버튼을 클릭합니다.
![vsca1](/assets/img/vsca1.png)  
![vsctest](/assets/img/vscad2.png)  
위와 같이 미리보기 화면이 나타납니다. 
 
vscode를 사용하면 편집한 테스트 파일을 git에 올리는 것도 매우 간단합니다.  
![vscpush](/assets/img/vscpush.png)


## 4. 완료!

![testp](/assets/img/test2.png)
드디어 나만의 블로그가 만들어졌습니다. 

다음 포스트에서는 간단한 블로그 커스터마이징에 대해 다루겠습니다.


<br>

## Useful Links

[Jekyll Chirpy 테마 사용하여 블로그 만들기 \| 하얀눈길 블로그](https://www.irgroup.org/posts/jekyll-chirpy/)  
[깃허브 블로그 포스트 작성하기 | 공부한거 정리 블로그](https://lugan1.github.io/blog/github-blog/)  
[GitHub jekyll-admin | GitHub](https://github.com/jekyll/jekyll-admin)