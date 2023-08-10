---
title : Chirpy 테마로 GitHub 블로그 만들기 ④
date : '2023-08-10'
categories : [Blog]
tags : [chirpy, github, blog, git, gitblog, vscode]
---


이번에는 블로그의 자잘한 설정들을 만져보도록 하겠습니다.   
이정도만 해줘도 나름 구색을 갖춘 블로그라 할 수 있을 것 같습니다.

1. 댓글 기능 추가 (`giscus`)
2. 구글 애널리틱스 등록
3. 외부 링크 새 탭에서 열도록 설정

<br>

## 댓글 기능 추가하기
  
<br>

댓글 시스템을 적용하려고 이리저리 구글링을 하니, `disqus`, `utterances`, `giscus` 요 세가지 정도의 서비스를 찾아냈습니다.   

그래서 처음에는 `utterances` 를 로컬에 적용해놓았었는데, 또 인터넷을 뒤지다보니 `giscus` 가 더 좋아보이더라구요. ~~팔랑귀~~  

`disqus`는 소셜 계정을 기반으로 동작합니다. 나머지 두 가지 서비스와 달리 GitHub Issue와는 별개입니다.

`utterances`와 `giscus`는 거의 유사한 시스템입니다. 전자는 Issues, 후자는 Discussions에 기반하여 동작하므로, 깃허브 계정을 필요로 합니다.   
다만 `giscus` 쪽이 장점이 더 많습니다. 자세한 내용은 [여기](https://jojoldu.tistory.com/704)를 참고해보세요.
  
<br>
아무튼 바로 시작해봅시다.

<br>  
  
  
### 저장소에서 Discussion 활성화

1. Github 저장소 페이지의 Settings로 들어갑니다.
![githubset](/assets/img/4post/githubsetting.png)
<br>  

2. General 탭에서 그대로 스크롤을 내려 `Features` 섹션에서 `Discussions` 를 활성화합니다.
   ![discussions](/assets/img/4post/ghdiscuss.png)

<br>


### Disscusions 세팅

<br>

![image](/assets/img/4post/img5.png)

새로 생긴 `Discussions` 탭에서 새로운 카테고리를 생성합니다.  

![6img](/assets/img/4post/6img.png)

`Announcement` 포맷을 선택합니다.  

![7img](/assets/img/4post/7img.png)

Title은 `Comments` 라고 적습니다.
  

### giscus 앱 설치

[giscus app](https://github.com/apps/giscus)을 인스톨합니다.  

![giscusinstall](/assets/img/4post/giscusins.png)  

블로그 저장소를 선택한 뒤 설치합니다.

<img src='/assets/img/4post/install2.png' width='80%' height='80%'>  

  

<br>

### giscus 세팅

<br>

[giscus.app](https://giscus.app/ko) 에서 설정을 마저 해줍니다.

![8img](/assets/img/4post/8img.png)

빈칸에 저장소 이름을 넣습니다. 형식은 `username/reponame` 입니다.  

![9img](/assets/img/4post/9img.png)  

페이지 경로를 포함하는 방법을 선택합니다. 카테고리는 `Announcements` 로 선택합니다.  

![10img](/assets/img/4post/10img.png)  

기능과 테마는 원하는 것으로 설정합니다.   이후 `<script>` 태그를 복사합니다.  

<br>  

`저장소/_layouts/` 디렉토리의 `post.html` 파일을 엽니다.  

![11img](/assets/img/4post/11img.png)

가장 아래에 복사한 내용을 붙여 넣습니다.   

<br>

### 테스트  

로컬에서 테스트합니다.    

![test](/assets/img/4post/giscustest.png)  

댓글이 작성되면 해당 포스트뿐 아니라 github discussions 페이지에서도 확인할 수 있습니다.  

![test2](/assets/img/4post/githtest.png)


<br>

  

## 구글 애널리틱스 등록

<br> 

블로그를 구글 애널리틱스에 등록하면 블로그의 세부적인 통계를 제공받을 수 있습니다.  

[구글 애널리틱스](https://analytics.google.com/analytics/web/?hl=ko#/a280802238p401580224/admin/account/create) 링크로 들어갑니다.
  

![gg1](/assets/img/4post/gg1.png)  

계정 이름을 입력합니다. 꼭 깃허브 아이디가 아니어도 됩니다.  
계정 데이터 공유 설정은 원하는대로 설정합니다.  

![gg2](/assets/img/4post/gg2.png)  

속성 이름은 블로그 이름으로 해두었습니다. 시간대와 통화 역시 한국 기준으로 설정해줍니다.  

![gg3](/assets/img/4post/gg3.png)
![gg4](/assets/img/4post/gg4.png)

비즈니스 세부정보를 입력합니다.  

![gg5](/assets/img/4post/gg5.png)
![gg6](/assets/img/4post/gg6.png)

플랫폼을 `웹`으로 선택하고 url과 이름을 적습니다.  

![gg7](/assets/img/4post/gg7.png)

웹 스트림 세부정보가 나타나면 `측정 ID` 를 복사합니다.   


![gg8](/assets/img/4post/gg8.png)

블로그 저장소의 `_config.yml` 을 열고 `google_analytics` 항목에 ID를 붙여넣습니다.


<b>로컬 서버의 정보는 집계하지 않습니다.</b> 수정된 내용을 git에 푸시하고 정보 수집이 작동하는지 확인합니다.  


<br>  

## 외부 링크 새 탭에서 열리게 설정하기  

외부 페이지 링크를 클릭하면 현재 블로그 페이지가 외부 페이지로 로딩됩니다.  
사용자 편의를 위해 새로운 탭에서 페이지를 로드하도록 설정해봅니다.  


링크 하나하나 해당 설정을 적용하는 방법이 있지만,  `jekyll-target-blank` 라는 플러그인을 설치하면 더 편합니다.  


저장소에서 `Gemfile` 을 엽니다. 마지막 줄에 아래 라인을 추가합니다.  

```ruby
gem 'jekyll-target-blank'
```  

그리고 `_config.yml` 파일의 가장 밑에 아래 라인을 추가합니다.

```yaml
plugins:
   - jekyll-target-blank
```

{:.prompt-tip}
> 위 방법이 동작하지 않으면 터미널에서 블로그 저장소 디렉토리로 이동한 후, 다음 명령을 입력합니다.  
> ```terminal
> gem install jekyll-target-blank
> ```

  

<br>

## 완료!   

![jumping!](/assets/img/4post/catjumping.gif)

대부분의 설정을 마무리했습니다!  
혹시 더 세팅이 필요한 부분이 있다면 추가적으로 포스팅해보겠습니다.


<br>

## Useful Links

[Utterances 에서 Giscus 로 마이그레이션하기](https://jojoldu.tistory.com/704)  
[Git Blog에 댓글 기능 추가하기](https://da-in.github.io/posts/Blog-Comments/)  
[Setting up comments using Giscus](https://technicaljourneys.com/2022/01/giscus-comments/)  
[Jekyll Theme external link management](https://www.ifnullthen.com/posts/Jekyll-Open-Blank/)  
[jekyll-target-blank](https://github.com/keithmifsud/jekyll-target-blank)