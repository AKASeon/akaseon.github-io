---
layout: post
title:  "github을 Blog 처럼 사용하기"
date:   2015-10-21
categories: jekyll update
---
# Install Jekyll
## For Ubuntu
### Jekyll 설치 준비
필요 패키지 설치

```
$ sudo apt-get install ruby ruby-dev make gcc nodejs
```
### Jekyll 패키지 설치
> gem : ruby 라이브러리 패키지 인스톨 도구  
>> gem guide 문서  
>> [RubyGems-Guide][1]  
>> [RubyGems-Guide-한글][2]

gem 을 이용하여 jekyll 를 설치

```
$ sudo gem install jekyll --no-rdoc --nori
```

> gem 을 이용하지 않고 apt-get 으로 jekyll 을 설치를 할 경우 아래와 같은 메세지를 볼수 있다.  
> ```bash: /usr/bin/jekyll: No such file or directory```  
> 그렇기 때문에 gem 을 이용하여 설치 하도록 한다.

## For Mac
coming soon...

## jekyll with Github

### Repository 생성
jekyll page 용으로 사용할 repository를 github 에 생성 한다.
생성할 repository 를 local 로 git clone 명령어를 통하여 내려 받는다.

```
$ git clone [repository 주소]
ex )
$ git clone https://github.com/AKASeon/memo.git
```

### Repository checkout
page 작업 하기 위하여 gh-pages 로 checkout 한다.

```
$ git checkout --orphan gh-pages
```

### jekyll Web page 생성
jekyll web page 를 생성한다.

```
$ jekyll new .
```

gitbub 에서 해당 페이지를 볼수 있도록 \_config.yml 를 수정한다.
baseurl 를 github 에서 생성한 repository 이름으로 수정 한다.
각종 정보도 업데이트를 한다.
```
# Site settings
title: Your awesome title
email: your-email@domain.com
description: > # this means to ignore newlines until "baseurl:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
baseurl: "/test" # the subpath of your site, e.g. /blog/
url: "" # the base hostname & protocol for your site
twitter_username: jekyllrb
github_username:  jekyll
```

### github push
github 에 commit 하기 위하여 수정한 모든 파일을 추가, coommit 및 github 에 push 를 수행한다.  

```
$ git add.                      # git에 모든 파일을 추가
$ git commit -m 'make page'     # local commit
$ git push origin gh-pages      # github 에 push
```

이젠 http://[계정명].github.io/repository/ 로 접속하여 정상적으로 page 가 뜨는지 확인 한다.
ex ) http://akaseon.github.io/memo/

## article upload
\_post 디렉토리에 markdown 문서를 push 하면 web 에서 확인 가능하다.  
파일 제목은 파일이름은 YYY-MM-dd-{영문제목}.markdown 으로 생성한다.  
확장자는 markdown 으로 해야 인식한다.  
md 로 생성 하였을때는 인식 못 하였다.  

```
$ git add YYY-MM-dd-{영문제목}.markdown # git에 article 추가
$ git commit -m 'post article'         # local commit    
$ git push origin gh-pages             # github 에 push
```

# 참조
http://michaelchelen.net/81fa/install-jekyll-2-ubuntu-14-04/   
https://nolboo.github.io/blog/2013/10/15/free-blog-with-github-jekyll/   
http://blog.saltfactory.net/jekyll/upgrade-github-pages-dependency-versions.html

[1]: http://guides.rubygems.org/ "RubyGems-Guide"
[2]: http://ruby-korea.github.io/rubygems-guides/ "RubyGems-Guide-한글"
