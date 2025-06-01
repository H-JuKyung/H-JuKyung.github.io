---
title: Jekyll Chirpy(v7.3.0) 테마로 기술 블로그 만들기
date: 2025-06-01 12:00:00 +0900
categories: [Git, Blog]
tags: [jekyll, chirpy, github-pages]
excerpt: Jekyll Chirpy 테마로 기술 블로그를 만들고 배포하는 방법을 정리했습니다.
image:
  path: /assets/post/Git/0601_1.png
  alt: jekyll-chirpy
published: true
---

기존에는 기술 블로그를 주로 노션이나 티스토리에 작성해왔습니다.  
그러던 중 구글링을 하다가 velog나 티스토리처럼 흔히 쓰이는 플랫폼 말고, 새로운 블로그 형식을 접하게 되었습니다.  
그게 바로 GitHub Pages를 활용한 블로그였습니다.  

GitHub Pages는 로컬에서 마크다운 형식으로 글을 작성하고,    
단순히 push만 하면 바로 블로그에 게시할 수 있어서 간편해 보였습니다.   
그래서 저도 한번 만들어보기로 결심했습니다.  

수많은 테마 중에서 **Jekyll Chirpy 테마**를 선택하게 되었는데,  
많은 분들이 사용하고 있을 뿐 아니라 디자인이 깔끔하고 심플해서 가장 마음에 들었습니다.  

지금부터 Window 환경에서 Chirpy 테마를 적용한 GitHub 블로그를 만드는 방법을 소개하겠습니다.     

---
# 1️⃣ Chirpy 테마 설치 방법

## 🔍 Chirpy Starter / GitHub Fork

Jekyll 기반의 Chirpy 테마를 설치하는 방법에는 두 가지가 있습니다.  

- **Chirpy Starter**    
공식 Chirpy Starter 템플릿을 사용하여 새로운 저장소를 생성하고, 초기 세팅을 바로 시작하는 방법입니다.  
- **GitHub Fork**   
Chirpy 테마의 공식 저장소를 Fork하여 내 저장소로 복사한 후, 내 블로그를 구축하고 유지하는 방법입니다.  

### 🚀 두 가지 방법의 장단점

|     | **Chirpy Starter** | **GitHub Fork** |
|-----|--------------------|-----------------|
| **장점** | 빠른 시작 가능, 기본 설정 제공 | 공식 Chirpy 테마 최신 버전 유지 가능, 업데이트 및 유지보수 용이 |
| **단점** | 업그레이드 시 Starter 업데이트가 필요 | 초기 설정이 Starter에 비해 약간 복잡할 수 있음 |

Chirpy Starter는 처음 블로그를 만들 때 빠르게 시작할 수 있다는 장점이 있지만,   
이후 Chirpy 테마의 버전이 올라가면 Starter를 업데이트하거나 새로 구성해야 하는 번거로움이 있습니다.  

반면, GitHub Fork 방식은 공식 저장소를 내 계정으로 복사하므로   
**Chirpy 최신 버전으로 유지하고 쉽게 업데이트할 수 있는 장점**이 있습니다.      
또한 기존 Fork된 저장소에서 내가 수정한 내용을 계속 유지할 수 있어 관리하기 좋습니다.

### 💡 Fork 방식 선택 이유
저는 Chirpy 테마를 장기적으로 운영하고 싶었고, 테마 업데이트나 관리가 쉬운 방법을 찾았습니다.   
그래서 **GitHub Fork 방식**을 선택했습니다.  

---

## 💻 Chirpy 테마 Fork하기

앞서 설명했듯이 Chirpy 테마를 설치하는 방법 중 저는 GitHub Fork 방식을 선택했습니다.  
이제 실제로 Chirpy 테마를 Fork하는 방법을 단계별로 소개하겠습니다.

### 🌟 Fork 단계
1. [Chirpy 공식 GitHub 저장소](https://github.com/cotes2020/jekyll-theme-chirpy)에 접속합니다.
2. 우측 상단의 **로그인 후 오른쪽 상단 Fork 버튼**을 클릭합니다.
3. Fork된 저장소 이름은 반드시 `내아이디.github.io` 형태로 지정합니다.  
   - 이렇게 하면 GitHub Pages에서 자동으로 `https://내아이디.github.io` 주소로 배포됩니다.

### 🌟 로컬 Clone

{: .prompt-warning }
> **주의:**  
> 로컬에 Git이 설치되어 있지 않다면 [Git 공식 사이트](https://git-scm.com/)에서 설치한 후 진행하세요.

Fork가 완료되면 Fork한 저장소를 내 컴퓨터에 복제(clone)합니다.
```bash
git clone https://github.com/내아이디/내아이디.github.io.git
cd 내아이디.github.io
```

이제 Chirpy 테마를 사용할 준비가 끝났습니다. 다음 단계에서는 루비 설치를 진행해봅시다! 🚀

---

# 2️⃣ Ruby 설치 방법

## 💎 Ruby 설치 (Windows 환경)

Chirpy 테마는 Jekyll 기반으로 동작하기 때문에, Ruby 환경이 필요합니다.  
특히 Windows 환경에서는 Ruby와 함께 DevKit도 설치해야 Jekyll 빌드에 필요한 도구를 사용할 수 있습니다.

### 🌟 설치 단계
1. [RubyInstaller for Windows 공식 사이트](https://rubyinstaller.org/downloads/)에 접속합니다.
2. **Ruby+Devkit 3.x.x (현재 기준 권장: 3.4.4-2, x64)** 버전을 다운로드합니다.
![Ruby downloads](/assets/post/Git/0601_2.jpg)
3. 설치 프로그램을 실행하면, 기본적으로 모든 체크박스가 선택된 상태로 나타납니다.  
   - 변경 없이 그대로 **Next**를 클릭하여 설치를 진행합니다.  
   - 설치 완료 후, **"Run 'ridk install' to setup"**라는 체크박스가 선택된 상태로 나타나는데,  
     그대로 **Finish** 버튼을 클릭하면 **명령 프롬프트 창**이 자동으로 실행됩니다.  
   - 프롬프트에 아래와 같은 메시지가 표시됩니다:  
     ```
     Which components shall be installed? If unsure press ENTER []
     ```  
     이때 **Enter**를 누르면 3가지 구성 요소가 모두 설치되고 완료됩니다.
4. 설치가 끝나면 명령 프롬프트(cmd)나 Git Bash를 열고, 다음 명령어로 Ruby 설치를 확인합니다:  
```bash
$ ruby -v
ruby 3.4.4 (2025-05-14 revision a38531fd3f) +PRISM [x64-mingw-ucrt]
$ gem -v
3.6.7
```

---

## 📦 의존성 설치 (bundle install)

Ruby 설치가 완료되었으므로, 로컬 Clone한 폴더로 이동해 의존성을 설치합니다.     
Gemfile에 명시된 라이브러리가 설치되며, Bundler도 자동으로 로컬에 설치됩니다.
```bash
cd 내아이디.github.io
bundle install
```

- bundle install을 실행하면, Gemfile.lock 파일에 맞춰 Bundler와 의존성 gem이 설치됩니다.
- 별도로 gem install bundler를 실행하지 않아도 됩니다.

---

# 3️⃣ Node.js 설치 방법 및 JS 빌드

## 🛠️ Node.js 설치

Chirpy 테마는 Ruby 기반의 Jekyll뿐 아니라, 자바스크립트와 스타일링 빌드를 위해 Node.js 환경이 필요합니다.  
Node.js 설치 후, `npm install`과 `npm run build` 명령어를 실행해 Chirpy의 JS, CSS 자산을 빌드해야 블로그가 정상적으로 동작합니다.

### 🌟 설치 단계
1. [Node.js 공식 사이트](https://nodejs.org/)에 접속합니다.
2. **LTS(Long Term Support) 버전**을 다운로드합니다.  
   (예: Node.js 22.x LTS 버전)
3. 다운로드한 설치 파일을 실행하여 기본 옵션으로 설치합니다.

---

## 🌟 의존성 설치 및 빌드

Node.js 설치가 완료되면, 로컬 Chirpy 폴더(`내아이디.github.io`)에서 다음 명령어를 실행합니다.

```bash
cd 내아이디.github.io
npm install
npm run build
```

- `npm install` : 프로젝트의 Node.js 의존성을 설치합니다.
- `npm run build` : Chirpy의 JS, CSS 빌드 파일을 생성합니다.

{: .prompt-warning }
> **참고:**  
> `npm run build`를 하지 않으면 Chirpy의 JS, CSS 파일이 생성되지 않아 블로그에서 기능이 정상 동작하지 않을 수 있습니다.

JS 빌드까지 완료하면, 이제 `bundle exec jekyll serve`로 로컬 블로그를 실행해볼 수 있습니다! 🚀

---

# 4️⃣ 블로그 로컬 실행 및 GitHub Pages 배포

## 💻 블로그 로컬 실행

Chirpy 테마의 모든 의존성 설치와 빌드가 완료되었으니, 로컬에서 블로그를 실행하고 GitHub Pages를 통해 배포할 차례입니다.

로컬에서 블로그를 미리보기 위해 다음 명령어를 실행합니다.
```bash
bundle exec jekyll serve
```

- 브라우저에서 `http://127.0.0.1:4000/` 주소를 입력하면 블로그가 열립니다.
![로컬 블로그 실행 화면](/assets/post/Git/0601_3.jpg)
- 처음 블로그를 실행하면 총 4개의 게시물이 작성되어 있습니다. 추후 `_posts` 폴더에서 삭제할 수 있습니다.
- 로컬 서버에서는 글을 작성하고 수정한 내용을 실시간으로 확인할 수 있어 편리합니다.

## 📝 `_config.yml` 설정 항목 및 수정 방법

Chirpy 테마의 `_config.yml` 파일은 블로그 설정의 핵심 파일로,  
블로그 제목, 작성자 정보, GitHub Pages 주소, 시간대 등 여러 항목을 관리합니다.  

다음은 기본적으로 포함된 항목들과, 내 정보로 수정할 부분을 정리한 표입니다.

| 항목 | 설명 | 예시 / 수정 방법 |
|------|------|-------------------|
| `lang` | 블로그 언어 | `ko` (한국어) |
| `timezone` | 시간대 | `Asia/Seoul` |
| `title` | 블로그 제목 | `내 블로그 이름` |
| `tagline` | 블로그 부제목 | `블로그 부제목` |
| `description` | 블로그 설명 | `블로그 설명` |
| `url` | GitHub Pages 주소 | `https://github.com/내아이디` |
| `baseurl` | GitHub Pages 하위 경로 (루트면 비워둠) | `` (루트일 경우) |
| `social.name` | 작성자 이름 | `본인 이름` |
| `social.email` | 작성자 이메일 | `본인 이메일 계정` |
| `social.links` | Twitter 계정 / GitHub 계정 | `본인 계정` |
| `theme_mode` | 다크모드 기본 설정 | `"light"` 또는 `"dark"` |

---

## 🚀 GitHub Pages 배포

`_config.yml` 설정을 수정하고 블로그 글 작성까지 완료했다면,  
로컬 저장소의 변경 사항을 GitHub 저장소에 반영(커밋 및 푸시)하는 방법은 다음과 같습니다.    

```bash
git add .                         # 전체 파일 추가
git status                        # Git 상태 확인
git commit -m "커밋 메시지 작성"   # 변경 사항 커밋
git push                          # GitHub 저장소에 푸시
```

> **⚠️ 참고**   
> - 변경 사항을 반영하면 GitHub Pages 배포는 자동으로 진행됩니다.  
> - 배포까지는 1~2분 정도 소요될 수 있습니다.     

### 🌟 GitHub Pages 배포 주소 확인

1. GitHub 저장소의 Settings 메뉴로 이동합니다.
2. 왼쪽 사이드바에서 Pages를 클릭합니다.
3. GitHub Pages 배포 브랜치(예: master)와 경로(/root 또는 /docs)가 표시됩니다.
4. "Your site is live at" 오른쪽에 주소(링크)를 클릭하면 배포된 블로그를 확인할 수 있습니다.
   - 예를 들어, 저장소 이름이 내아이디.github.io라면:   
   배포 주소: `https://내아이디.github.io`

---

드디어 GitHub Pages와 Chirpy 테마로 나만의 기술 블로그를 완성했습니다.  
이제부터는 이 블로그에 저만의 기록을 차곡차곡 쌓아갈 예정이에요.  
읽어주셔서 감사합니다! 😊