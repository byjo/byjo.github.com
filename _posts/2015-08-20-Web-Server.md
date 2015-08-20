---
layout: post
title: "웹 서버 기초"
description: ""
category: "Server" 
tags: [Server, Web Server, Servlet, JSP]
---
## 웹서버
: 클라이언트로부터 HTTP 요청을 받고, 요청에 해당하는 정보, 리소스를 응답으로 보내줌 (+ 클라이언트로부터 정보를 받음)
ex) Apache, nginx ...  
- 웹 서버는 페이지를 동적으로 생성하지 못함  
- -> 이를 다른 프로그램에 요청

## 웹 어플리케이션 서버(WAS)
: 웹 어플리케이션을 서버에서 실행할 수 있도록 해주는 것 
ex) 아파치 톰캣, 제티

cf. 이 웹 서버에서 실행 되는 동적 페이지 생성 프로그램 중 하나가 서블릿임  
- WAS 또한 웹 서버의 기능과 어플리케이션 기능(컨테이너)의 역할 두 부분으로 나눠짐

## 서블릿

#### 서블릿 컨테이너
서블릿 컨테이너는 HTTP 요청을 받아서 Servlet을 실행시키고, 그 결과를 사용자 브라우저에게 전달해주는 기능을 제공하는 컴포넌트

#### 컨테이너의 요청처리
- HTTP request가 들어오면 HttpServletResponse, HttpServletRequest 객체를 생성
- URL을 분석하여 요청한 서블릿을 알아냄
- 해당 서블릿에 Response/Request 객체를 인자로 넘김
- 서블릿의 Service() 메소드를 호출(메소드에 따라 doGet, doPost)
- Service()가 동적인 페이지를 만들어내면 Response에 실어서 컨테이너로 보냄
- 스레드 작업이 끝나면 컨테이너가 HttpResponse를 만들어 클라이언트로 내려보냄
cf. tomcat은 컨테이너의 좋은 예이다. apache와 같은 웹 서버가 사용자로부터 Servlet에 대한
요청을 받으면 Servlet을 바로 호출하는 것이 아니라 Servlet을 관리하고 있는 컨테이너에게
이 요청을 넘긴다. 이 컨테이너는 Servlet이 배포(deploy)된 컨테이너다. 요청을 넘겨받은 컨
테이너는 HTTP Request와 HTTP Response 객체를 만들어 이를 인자로 Servlet doPost( )나
doGet( ) method 중 하나를 호출한다. 

#### 컨테이너 초기화 
- 컨테이너가 시작되면 컨테이너는 배포된 웹 애플리케이션 관련한 서블릿 클래스 파일을 검색.
- 클래스를 로딩하는 작업은 컨테이너 시작 혹은 최초 클라이언트 접근시 이루어짐
- 컨테이너가 서블릿을 초기화할 때, 서블릿마다 하나씩 ServletConfig를 생성.
- 컨테이너는 DD에서 서블릿 초기화 파라미터를 읽어 이 정보를 ServletConfig로 넘김
- 서블릿 init()에 ServletConfig 전달
- 그 다음 디폴트 생성자가 호출되고 Init()이 한 번 호출.

####리스너
특정 상황을 모니터링 하다가 해당 상황이 발생하면 동작하는 일종의 서블릿. 웹 어플리케이션 시작 및 운영 종료 과정에서 발생하는 일련의 과정에서 특정 상황에 필요한 작업을 처리하기 위해 사용.
- 컨텍스트가 초기화 되는 것을 알아채고 초기화 파라미터를 읽음
- 초기화 파라미터를 검색명으로 객체를 생성하여 ServletContext 속성에 묶어둠
- 객체를 Context에서 공유할 수 있게 됨

cf. DD(Deployment Description) : 서블릿과 JSP 수행을 위한 정보들이 담겨있음 ; web.xml


## JSP(Java Server Page)
- HTML + Java
- HTML 내에 Java를 삽입, 동적으로 페이지를 생성해서 클라이언트에게 보내줌 
- Servlet의 확장 형태. 처음에는 Sevlet에서 print를 통해서 동적 페이지를 생성. 근데 불편.
- jsp 처리 과정
    - 사용자가 jsp요청
    - jsp파일을 java소스파일로 변환
    - 컴파일하여 class파일로 변환
    - 메모리 로딩되고, init() 실행하여 Servlet인스턴스화
    - 서블릿과 동일하게 요청 처리

## 세션(Session)과 쿠키(Cookie)
- HTTP는 무상태 연결로 클라이언트를 구별하기 위해서는 세션이 필요
- 컨테이너는 클라이언트에 Response의 일부로 세션 ID를 보내고 그 다음 요청부터 클라이언트는 Request의 일부로 세션 ID를 돌려보낸다. 가장 일반적인 방법은 쿠키를 이용하는 방법
- 만약 쿠키를 사용하지 않도록 클라이언트에서 설정되어 있다면 URL에 JsessionID를 붙여서 정보를 주고 받음
- 세션 객체들은 서버에 남아서 자원을 소모하지만 서버에서는 클라이언트가 떠났는지 알 수 없음
- 세션이 종료되는 이유는 시간이 다되거나, 세션 객체의 invaliate() 실행, 애플리케이션 다운

{% include JB/setup %}
