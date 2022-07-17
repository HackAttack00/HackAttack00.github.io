---
layout: post
title: cocoapod 업데이트 에러
date: 2022-07-23 19:04:06 +0900
category: cocoapod


---

# 코코아팟 업데이트 에러

아 넘나 싫은것..

코코아 팟 업데이트 관련해서 루비 권한 에러, 루비 버전 에러를 해결하기 위한 명령어 셋이다.

여기저기 뒤져서 세팅한 순서대로 정리.

여기서 문제는 Xcode를 외장하드에 저장해서 사용하다가 로컬에 설치했는데

~~~script
brew install gcc
brew unlink ruby-build
brew install --HEAD ruby-build
sudo xcode-select --switch /Applications/Xcode.app
sudo gem install cocoapods
rbenv --version
rbenv install 2.7.6
sudo gem install cocoapods -n /usr/local/bin

~~~

