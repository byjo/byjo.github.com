---
layout: post
title: Spring Social 맛보기
categories: ["Book", "Spring 5 Recipes"]
tags: ["Java", "Spring"]
---

약 1년을 봐왔지만 아직도 정확하게 모르겠는 우리 서비스의 인증 방식을 이해하기 위해 spring social과 security를 한 번 파보려 한다. 옆에서 줏어들은 건 많지만 아직 그 개념이 흐릿하기에 일단 용어 정리부터 먼저 시작하자.

# Terms
+ OAuth : 표준화 된 인증 프로토콜이다. OAuth 인증을 위한 Open API를 제공하는 기반 서비스(A) - OAuth 인증을 통해 사용자에게 A 서비스의 기능을 제공하는 응용 서비스(B) - 사용자(C) 간의 연결로 이뤄진다.
|     역할    |     OAuth 1.0    |               OAuth 2.0               |
|:-----------:|:----------------:|:-------------------------------------:|
| 사용자      | User             | Resource Owner                        |
| 기반 서비스 | Service Provider | Resource Server + Authrozation Server |
| 응용 서비스 | Consumer         | Client                                |
+ credential : 애플리케이션의 식별자(API 키, API 시크릿)
+ Authentication and Authorization 



Spring Social은 애플리케이션과 소셜 네트워크 서비스 연결을 위한 통합 API를 제공한다. 

- Spring Social의 구성
    + Connect Framework : 흐름 제어 
    + ConnectController : 서비스 프로바이더 - 어플리케이션 - 유저 간의 OAuth를 주고받는다
    + SocialAtuhenticationFilter : 로그인을 위해 Spring Security와 연결
