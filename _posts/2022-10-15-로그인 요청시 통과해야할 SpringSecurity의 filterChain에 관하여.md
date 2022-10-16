---
layout: single
title: "Spring Security filterchain"
categories: Spring Security
toc: true
author_profile: false
sidebar:
    nav: "docs"
---


# FilterChain
- 스프링 설정을 하기 위해 config 클래스를 만들고 config 클래스로 설정하기 위해 @EnableWebSecurity을 넣어준다. 해당 애너테이션의 속성인 debug를 통해 어떤 필터체인이 통과되는지를 알 수 있다. 
```java
@EnableWebSecurity(debug = true)
public class SecurityConfig{}
```

## Security Debugger
	- 시큐리티가 적용되는 URI를 클라이언트가 호출시 다음과 같이 관련 로그들이 서버 콘솔에 출력된다. 
```java
2022-09-12 00:29:55.926  INFO 44500 --- [nio-8080-exec-3] Spring Security Debugger                 : 

************************************************************

Request received for GET '/login':

org.apache.catalina.connector.RequestFacade@7ef4baf

servletPath:/login
pathInfo:null
headers: 
host: localhost:8080
connection: keep-alive
cache-control: max-age=0
sec-ch-ua: "Whale";v="3", " Not;A Brand";v="99", "Chromium";v="104"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
upgrade-insecure-requests: 1
user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.5112.87 Whale/3.16.138.22 Safari/537.36
accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
sec-fetch-site: none
sec-fetch-mode: navigate
sec-fetch-user: ?1
sec-fetch-dest: document
accept-encoding: gzip, deflate, br
accept-language: ko-KR,ko;q=0.9,en-US;q=0.8,en;q=0.7
cookie: JSESSIONID=CDB35706316E699A091FF6D534E1DA90


Security filter chain: [
  DisableEncodeUrlFilter
  WebAsyncManagerIntegrationFilter
  SecurityContextPersistenceFilter
  HeaderWriterFilter
  CsrfFilter
  LogoutFilter
  UsernamePasswordAuthenticationFilter
  DefaultLoginPageGeneratingFilter
  DefaultLogoutPageGeneratingFilter
  BasicAuthenticationFilter
  RequestCacheAwareFilter
  SecurityContextHolderAwareRequestFilter
  AnonymousAuthenticationFilter
  SessionManagementFilter
  ExceptionTranslationFilter
  FilterSecurityInterceptor
]
```
- Security filter chain에는 기본으로 설정되어 있는 체인 16개가 로그에 보여진다. 이들 필터체인을 살펴보면서 SpringSecurity가 어떻게 어플리케이션의 보안을 지키는지를 살펴보자 



## Security filter chain

  ### DisableEncodeUrlFilter
	  -
  ### WebAsyncManagerIntegrationFilter
	  -
  ### SecurityContextPersistenceFilter
	  -
  ### HeaderWriterFilter
	  -
  ### CsrfFilter
	  -
  ### LogoutFilter
	  -
  ### UsernamePasswordAuthenticationFilter
	  -
  ### DefaultLoginPageGeneratingFilter
	  -
  ### DefaultLogoutPageGeneratingFilter
	  -
  ### BasicAuthenticationFilter
	  -
  ### RequestCacheAwareFilter
	  -
  ### SecurityContextHolderAwareRequestFilter
	  -
  ### AnonymousAuthenticationFilter
	  -
  ### SessionManagementFilter
	  -
  ### ExceptionTranslationFilter
	  -
  ### FilterSecurityInterceptor
	  -




************************************************************