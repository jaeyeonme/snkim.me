---
title: "Mac에서 Hugo로 블로그 개설하기"
description: "hugo를 사용해서 간단하게 블로그를 만들어본다."
date: 2021-09-08T20:55:11+09:00
draft: false
tags: ["hugo", "blog", "tip"]
categories: ["etc"]
---

## 로컬에 휴고 사이트 설치 및 실행

### 설치

1. `homebrew`로 hugo 설치.

   ```bash
     brew install hugo
   ```

2. hugo로 사이트 생성.

   ```bash
     hugo new site <Site-Name>
   ```

3. 생성된 사이트에 들어가서 theme 설치. 내 경우는 LoveIt theme를 적용하였다.

   ```bash
     cd <Site-Name>

     git clone https://github.com/dillonzq/LoveIt.git themes/LoveIt
   ```

4. `config.toml` 파일 수정하기

   ```toml
     baseURL = "http://example.org/"

     # [en, zh-cn, fr, ...] determines default content language

     defaultContentLanguage = "en"

     # language code

     languageCode = "en"
     title = "My New Hugo Site"

     # Change the default theme to be use when building the site with Hugo

     theme = "LoveIt"

     [params]

     # LoveIt theme version

     version = "0.2.X"

     [menu]
     [[menu.main]]
     identifier = "posts" # you can add extra information before the name (HTML format is supported), such as icons
     pre = "" # you can add extra information after the name (HTML format is supported), such as icons
     post = ""
     name = "Posts"
     url = "/posts/" # title will be shown when you hover on this menu link
     title = ""
     weight = 1
     [[menu.main]]
     identifier = "tags"
     pre = ""
     post = ""
     name = "Tags"
     url = "/tags/"
     title = ""
     weight = 2
     [[menu.main]]
     identifier = "categories"
     pre = ""
     post = ""
     name = "Categories"
     url = "/categories/"
     title = ""
     weight = 3

     # Markup related configuration in Hugo

     [markup]

     # Syntax Highlighting (https://gohugo.io/content-management/syntax-highlighting)

     [markup.highlight] # false is a necessary configuration (https://github.com/dillonzq/LoveIt/issues/158)
     noClasses = false
   ```

### 첫 포스트 발행

```bash
  hugo new posts/first-post.md
```

처음 생성하면 `content/posts/` 경로에 `first-post.md`파일이 생성된다.

`draft=true`로 지정되어 있을텐데 개발 모드에서 실행하면서 확인하기 위해 `false`로 변경해주자.

그리고 본문 내용이 있어야하므로 `hello hugo`라고 입력해 준 다음 저장한다.

### 실행

1. 로컬 `localhost:1313`에서 실행하기

   ```bash
     hugo serve
   ```

## 배포하기

### 빌드 파일 생성

아래 커맨드를 실행하면 public폴더에 정적파일이 생성된다.

```bash
  hugo
```

[Netlify]()

## 번외. LoveIt 테마의 이쁜 컴포넌트들

{{< admonition >}}
A **note** banner
{{< /admonition >}}

{{< admonition abstract >}}
An **abstract** banner
{{< /admonition >}}

{{< admonition info >}}
A **info** banner
{{< /admonition >}}

{{< admonition tip >}}
A **tip** banner
{{< /admonition >}}

{{< admonition success >}}
A **success** banner
{{< /admonition >}}

{{< admonition question >}}
A **question** banner
{{< /admonition >}}

{{< admonition warning >}}
A **warning** banner
{{< /admonition >}}

{{< admonition failure >}}
A **failure** banner
{{< /admonition >}}

{{< admonition danger >}}
A **danger** banner
{{< /admonition >}}

{{< admonition bug >}}
A **bug** banner
{{< /admonition >}}

{{< admonition example >}}
An **example** banner
{{< /admonition >}}

{{< admonition quote >}}
A **quote** banner
{{< /admonition >}}

> 이것은 인용구 스타일입니다.

- **이것은 글자 강조입니다.**

{{< style "text-align:center; strong{color:#00b1ff;}" >}}

- 스타일을 넣어 봅니다.
  가운데 **strong tag에 색상 넣기** 정렬!
  {{< /style >}}

![Image preview](sunset.jpg "Image Preview. Beautiful Sunset")

- [font-awesome](https://fontawesome.com/)으로 아이콘을 사용 하려면 `config.toml`에 아래 코드를 적용해 주면 된다. :(far fa-user fa-fw): :(fab fa-apple):

  ```toml
    [params.page]
      fontawesome = true
  ```

- **그래프**도 됩니다

  {{< mermaid >}}
  pie
  "react" : 386
  "vue" : 85
  "svelte" : 15
  {{< /mermaid >}}

- [TypeIt](https://typeitjs.com/)
  {{< typeit >}}
  간장공장공장장은 _간장공장장이고_ 된장공장공장장은 **된장공장장이다**...
  {{< /typeit >}}

## References

[hugo loveit theme](https://hugoloveit.com/theme-documentation-basics/#22-install-the-theme)

[ialy님의 블로그](https://ialy1595.github.io/post/blog-construct-2/)
