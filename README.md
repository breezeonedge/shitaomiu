# shitaomiu
Shitao Miu Archiving Project

---

## Shitao Miu 관련 아카이빙 사이트

AKB48 Team8 멤버인 Shitao Miu와 관련된 자료를 모으고 있습니다.

대부분의 자료는 [디시인사이드 시타오 미우 마이너갤러리](http://shitaomiu.com)에서 가져왔습니다.

## 개발

1. 참고 사이트

  - Jekyll
    - 블로그/정적웹사이트 저작도구
    - [공식사이트](https://jekyllrb.com/)
    - [한글문서](https://jekyllrb-ko.github.io/)

  - GitHub Pages
    - GitHub 저장소 프로젝트용 무료 웹사이트 서비스
    - [공식사이트](https://pages.github.com/)
    - [카카오 개발블로그](https://github.com/kakao/kakao.github.io)

2. 요구 사항

  - Ruby ~= 2.5.1
  - GitHub Pages
    - [Dependency versions](https://pages.github.com/versions/)
    - jekyll == 3.7.3
    - github-pages == 188
    - jekyll-theme-modernist == 0.1.1
    - sass == 3.5.6

3. 설치

  ```bash
  $ git clone -b gh-pages breezeonedge@github.com/breezeonedge/shitaomiu
  $ gem install bundle
  $ cd shitaomiu
  $ bundle install # 의존성이 모두 설치됩니다.
  ```

4. 실행

  ```bash
  $ bundle exec jekyll serve --baseurl '' --watch
  $ open http://localhost:4000
  ```

5. 배포(발행)

  ```bash
  $ git commit -m '...'
  $ git push origin/gh-pages gh-pages
  ```

## 기여방법

[디시인사이드 시타오 미우 마이너갤러리](http://shitaomiu.com)에 더 많은 정보를 남겨주세요.