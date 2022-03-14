---
title: "[Spring] spring mvc - dispacter servlet"
date: 2022-03-14 11:14:28 -0400
categories: spring 
tags : [spring, servlet, mvc]
published: true
---


1. Dispatcher Servlet 이란

    - 요청을 특정 컨트롤러에 매핑하기위한 frontController 패턴을 적용한 servlet 이다.
    - 과거에는 서블릿을 컨트롤러 당 하나씩 두고 있었고 컨트롤러 추가할때마다 서블릿을 web.xml에 등록하거나 @WebServlet 을 이용해야했다. 

<br></br>

2. Dispatcher Servlet 동작 방식
        
    - @Controller 사용하면

        ![controller](/assets/images/Controller.jpeg)

        1. 클라이언트 요청을 Dispatcher Servlet 이 받는다.
        2. HandlerMapping 에게 정보를 보내 요청 처리할 Controller를 찾는다.
        3. Controller로 위임 처리할 HandlerAdapter 를 찾는다.
        4. 찾은 HandlerAdapter를 사용해서 Controller의 메소드를 실행한다. 
            
            이때 Controller의 반환값은 Model과 View 이다.
            
        5. Dispatcher Servlet은 View 이름을 ViewResolver에게 전달한다. ViewResolver는 이름을 토대로 View객체를 검색후 반환한다.
        6. Dispatcher Servlet은 찾은 View에게 Model을 전달해준다.
        7. View결과를 클라이언트에게 반환한다.
        
    - @RestController , @ResponseBody 사용하면

        ![controller](/assets/images/RestController.png)

        1. 클라이언트 요청을 Dispatcher Servlet이 받는다.
        2. HandlerMapping 에게 정보를 보내 요청 처리할 Controller를 찾는다.
        3. Controller로 위임 처리할 HandlerAdapter 를 찾는다.
        4. 찾은 HandlerAdapter를 사용해서 Reflection으로 Controller의 메소드를 실행한다. 
            
            이때 Controller의 반환값은 Response Entity다.
            
        5. HandlerAdpater가 반환받은 ResponseEntity를 통해 Response 처리를 진행하고 클라이언트로 반환한다. 


<br><br/>
        
  
> 참고
> 

[https://mangkyu.tistory.com/18](https://mangkyu.tistory.com/18)

[https://galid1.tistory.com/525?category=783055](https://galid1.tistory.com/525?category=783055)