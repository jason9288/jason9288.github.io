---
title : Chirpy 테마로 Github 블로그 만들기 ①
date : '2023-08-07'
categories : [Blog]
tags : [chirpy, github, blog, git, gitblog, vscode]
---

> 인터넷을 뒤져보던 중 깃허브를 통해 블로그를 개설할 수 있다는 것을 보고 마음이 확 끌려서 작업에 착수하기 시작했습니다.  

그런데 생각보다 난관이 많았습니다. 대부분은 짤막한 제 지식 때문이었지만...
 
 그래서 제가 경험한 것들을 토대로 ```Chirpy``` 테마로 깃허브 블로그를 만드는 방법을 기록 겸 소개해드리려고 합니다.



```Applc Silicon mac, macOS Ventura 환경 기준입니다.```



## 1. 사전 설정 하기

블로그를 생성하기 전 사전 확인 해야하는 작업들은 다음과 같습니다.

- [GitHub](https://github.com/) 회원가입
- ruby 설치  
   
   터미널에 아래 명령어를 입력하여 ruby를 설치합니다.
   ```shell
   brew install ruby
   ```

    {:.prompt-warning}
    > 이때  ```zsh: command not found: brew``` 라는 에러가 발생한다면, 맥에 ```brew```가 설치되지 않은 것입니다.   
    > ruby를 설치하기 전 다음 명령어로 ```brew```를 설치합니다.
   > ```shell 
    >/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   >```   
    >설치 과정에 문제가 있다면 [Homebrew 홈페이지](https://brew.sh/)에서 ```other installation options```를 클릭, pkg 파일을 통해 다운받을 수도 있습니다. 

- Node.js 설치
   ```shell
   brew install node
   ```

## 2. Chirpy fork

테마를 다운받는 여러 방법이 있지만 이 포스트에서는 소스를 fork 받아 만드는 방법을 소개하겠습니다. 

[Chirpy fork](https://github.com/cotes2020/jekyll-theme-chirpy/fork)에서 소스를 fork 받습니다. 이때 깃허브에 본인 계정으로 로그인되어 있어야 합니다.

![image1](/assets/img/fork1.png)

Repository name은 **반드시** ```<github 아이디>.github.io``` 로 설정해야 합니다. 이는 생성될 블로그의 도메인이 됩니다.

그리고 Repository 페이지에서 Settings로 이동합니다. branch를 ```master```에서 ```main```으로 변경합니다. 

![fork2](/assets/img/fork2.png)



### Clone 하기

우선 블로그 파일과 소스가 저장된 Repo를 로컬에 불러와야 합니다.  
터미널에서 원하는 디렉토리로 이동한 후
git clone 명령을 입력합니다.
```shell
git clone 'repository 링크'
```
![clone](/assets/img/clone.png)
링크는 위 스크린샷처럼 확인할 수 있습니다.

지정한 위치에서 repo의 이름과 동일한 폴더가 생겼다면 clone에 성공한 것입니다.


### Chirpy 초기화

터미널 디렉토리를 클론해 온 저장소로 이동합니다.  
그리고 아래 명령을 사용해서 Chirpy를 초기화합니다.
```shell
tools/init.sh
```
오류가 뜨면 디렉토리를 tools 폴더로 이동해서 ```ìnit.sh``` 또는 ```init``` 명령어를 입력합니다.

  
  
    

### 로컬에서 테스트

jekyll 블로그는 로컬에서 게시물 또는 블로그 설정들을 관리할 수 있습니다. 이 상태에서는 블로그가 외부적으로 노출되지 않습니다. 

이를 git에 푸시하게 된다면 비로소 온라인에 등록이 되고, 앞에서 설정했던 도메인 주소 ```username.github.io``` 에서 접속이 가능하게 됩니다. 

이제 로컬에서 실행시키기 위한 작업을 해 봅시다.  
로컬 실행 명령어를 입력하기 전 터미널 디렉토리는 블로그 저장소로 위치시킨 상태여야 됩니다.


1. 터미널에서 다음 명령을 입력합니다.
   ```shell
   gem install bundler
   ```
2. 다음 명령으로 jekyll을 설치합니다.
    ```shell
    gem install jekyll
     ```
3. 아래 명령을 사용하면 jekyll 로컬 실행을 할 수 있습니다.
    ```shell
    jekyll serve
    ```
  

{:.prompt-warning}
> 위 과정에서 오류가 발생한다면, [Jekyll 공식 홈페이지의 가이드라인](https://jekyllrb-ko.github.io/docs/installation/macos/)을 읽고 누락된 과정을 시행해보시기 바랍니다.  
    
  

아래와 같이 출력된다면 정상적으로 실행된 것입니다.
![term1](/assets/img/terminal1.png)  
  

로컬 서버가 실행되었으니 가서 확인해봅시다.  
터미널에 출력된 대로 브라우저 주소창에 ```http://127.0.0.1:4000/``` 을 입력하여 Chirpy 스타일을 확인할 수 있다면 성공입니다.  
  

로컬 서버를 종료하려면 터미널 창에서 ```control + c```를 입력합니다.  
그런데 웬 컬러 피커가 나오고 종료가 되지 않을 때는, ```control + shift + c``` 를 입력합니다.

<br>  



## 3. GitHub 푸시 전 설정

로컬 테스트에서 아무런 문제가 없었다면 git에 배포해봅시다.  
 

1. 깃허브 repo settings에서 소스를 GitHub Actions로 변경합니다.
    ![gitset1](/assets/img/gitset1.png)  

    
2. 변경 후 바로 밑의 ```Configure``` 를 클릭, jekyll.yml 편집창이 나오면 아무것도 수정하지 _않은_ 채로 오른쪽 위 초록색 ```Commit changes...``` 를 클릭합니다.

3. ```Commit changes``` 창에서도 역시 수정 없이 바로 초록색 Commit changes를 클릭합니다.

4. Finder에서 블로그 저장소 내의 /.github/workflow 에서 ```pages-deploy.yml.hook``` 을 삭제합니다.

    .github 폴더는 숨겨진 폴더로, 단축키 ```Command + Shift + .``` 을 눌러 보이게 할 수 있습니다.

5. GitHub와 로컬 리소스를 동기화합니다. 
    ```shell
    git pull
    ```
      
      이번에도 터미널 디렉토리는 블로그 저장소로 위치된 상태여야합니다.

6. .gitignore 파일을 열어 맨 밑줄 ```assets/js/dist```을 주석처리합니다. (숨겨진 파일입니다.)
    ```
    # Bundler cache
    .bundle
    vendor
    Gemfile.lock

    # Jekyll cache
    .jekyll-cache
    _site

    # RubyGems
    *.gem

    # NPM dependencies
    node_modules
    package-lock.json

    # IDE configurations
    .idea
    .vscode

    # Misc
    # assets/js/dist ## 주석처리
    ```

<br>

## 4. 테스트 포스트 만들기

이제 첫번째 테스트 페이지를 만들어봅시다.   
jekyll 블로그는 ```markdown``` 문법을 사용합니다. ```확장자:.md```  
많은 마크다운 편집기들이 있으니 편의에 맞춰 사용하셔도 됩니다.

일단 가장 간단한 방법으로 문서를 생성해봅시다.

터미널에서 저장소 폴더 내 _posts로 이동합니다. 이 폴더에는 이제부터 게시할 ```markdown``` 형식의 포스트들이 위치하게 됩니다.
```shell
cd ~/저장소 경로/_posts
```
새로운 파일을 생성하려면 ```touch``` 명령어를 사용합니다.
```shell
touch 2023-08-07-test.md
```

{:.prompt-warning}
> 포스트할 마크다운 파일의 이름은 **항상 YYYY-MM-DD-포스트제목.md** 형식으로 해 주어야 합니다.   
> 다른 형식일 경우 블로그에 게시물이 보이지 않습니다.

Finder에서 보면 2023-08-07-test.md 파일이 생성된 것을 볼 수 있습니다. 이를 실행해봅니다.  
다른 편집기가 없는 상황이라면 mac의 기본 텍스트 편집기로 실행됩니다. 

```markdown``` 문법에 대해서는 이미 인터넷에 잘 나와있습니다. [마크다운 가이드](https://www.markdownguide.org/basic-syntax/)에서 간단한 문법을 확인해봅시다.

아무튼 테스트 페이지이니 대충 아무 말이나 적어 저장합니다.
```markdown
테스트 페이지입니다.
# 제목입니다.
## 제목입니다.
### 제목입니다.

[네이버](https://www.naver.com)
[구글](https://www.google.com)
```

처럼 대충 적습니다.     
  
<br>


## 5. git push하기


드디어 git push를 할 차례입니다. 터미널에 다음 명령을 입력합니다.
```shell
git add -A
git commit -m "test"
git push
```
<br>

![gits](/assets/img/gitsucess.png)

push에 성공했다고 출력되면 GitHub의 Actions 탭을 살펴봅니다. 

![workflow](/assets/img/workflow.png) 
   
workflow 현황에서 오류가 발생되면 블로그 기능이 정상적으로 동작하지 않습니다.
  
<br>

정상적으로 실행되면 블로그 주소 ```username.github.io```를 입력하고 제대로 만들어졌는지 확인해봅시다.  

![blogtest](/assets/img/blogtest.png)

<br>

## 6. 잔디를 심어보자

![jandi](/assets/img/jandi.png)
GitHub에서 fork해온 repository에 커밋을 하면 잔디가 심어지지 않는 문제가 있습니다.   
사실 문제라기보다는 GitHub 규정상 원래 그렇다고 하네요.  
  
  해결하려면 fork해온 repo를 그대로 복제해서 본인 repo로 만들어야합니다.   
  그렇게 복잡한 작업은 아닙니다. 저는 밑의 상세하게 설명해주신 포스트를 보고 해결했습니다.

[(Git/Github) 깃허브 잔디 누락 현상](https://kdjun97.github.io/git-github/plant-grass/)




<br>

## 7. 완?성

![굴러는간다](/assets/img/굴러는간다.gif)
<center> 이걸로 끝..? </center><br>

블로그 이름, 카테고리, 디자인 등등 아직 구성된게 거의 없지만, 우선 깃허브 블로그의 기본적인 틀을 완성했습니다.

다음 포스트에서 블로그 설정에 관한 내용을 다루어보도록 하겠습니다. 

<br>

## Useful Links

[Jekyll Chirpy 테마 사용하여 블로그 만들기 \| 하얀눈길 블로그](https://www.irgroup.org/posts/jekyll-chirpy/)  
[jekyll chirpy 설치 시 발생하는 오류 해결하기 | Analogrammer](https://kiffblog.tistory.com/233)  
[깃허브 잔디 누락 현상 | Jumy Blog](https://kdjun97.github.io/git-github/plant-grass/)