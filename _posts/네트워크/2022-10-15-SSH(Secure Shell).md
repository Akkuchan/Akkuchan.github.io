---
layout: single
title: "SSH(Secure Shell)"
categories: 네트워크
toc: true
author_profile: false
sidebar:
    nav: "docs"
---


# Secure Shell
- SSH란 통신하는 두 대상간의 통신 데이터를 암호화하여 보안을 강화하는 통신 프로토콜이다. 
- 사용자 인증을 위하여 공개 열쇠 암호기법을 사용한다.
- telnet, rlogin, rcp등의 프로토콜에서는 통신 데이터가 유출될 경우 모든 정보가 그대로 유출되는 상황이 벌어진다.  통신 데이터가 암호화되지 않기 때문이다. 
- 이와 달리 SSH는 통신 데이터의 문자를 전부 암호화하기에 데이터가 유출되어고 보다 보안성이 높은 프로토콜이다.


## Secure Shell의 특징
- 기본 포트로 22번을 사용한다. 
	- 원격 통신을 막기 위해서 일부 ISP나 기관, 단체에서 사용하는 네트워크는 22번 포트를 방화벽이나 라우터로 아예 막아 놓기도 한다. 
- 원격 통신 프로토콜이기에 CLI 기반이지만 X.org 툴이 설치되어있다면 GUI로 사용할 수도 있다. 



## SSH 클라이언트
- 현재에는 업데이트를 지원해 윈도우 터미널로도 SSH 통신이 가능하다. 
- 하지만 GUI를 제공하는 여러 오픈소스들이 존재하고 편리해 Xsheel, putty와 같은 오픈소스 툴을 클라이언트로 사용하기도 한다.
- VSC에서도 특정 플러그인을 사용하면 SSH 클라이언트로 사용할 수 있다. 



출처
https://namu.wiki/w/Secure%20Shell
https://openwiki.kr/tech/ssh
https://velog.io/@gusdnr814/TLS-HTTPS-SSH-FTP



