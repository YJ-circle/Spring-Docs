# Spring Framework Overview

Spring Framework 6.0부터는 Java 17 이상이 필요합니다.

스프링은 기업 환경에서 자바를 활용해 애플리케이션을 쉽게 개발할 수 있도록 필요한 모든 기능을 제공합니다.

애플리케이션의 요구에 맞춰 다양한 아키텍처를 유연하게 설계할 수 있습니다.

자바 외에도 Groovy (그루비)와 Kotlin (코틀린) 같은 JVM 대안 언어도 지원합니다.

스프링은 오랫동안 스프링 커뮤니티를 통해 다양한 실제 사용 사례에 대한 피드백을 받아 발전하였습니다.

그 결과 다양한 환경에서 유연하게 활용될 수 있게 되었습니다.

예를 들어, 대규모 기업 환경에서는 애플리케이션이 장기간 운영되며, JDK와 애플리케이션 서버의 업그레이드를 개발자가 임의로 할 수 없는 경우가 있습니다.

또한 클라우드 환경에서 서버가 내장된 하나의 JAR 파일로 실행될 수도 있습니다.

배치 작업이나 통합 작업처럼 서버 없이 독립적으로 실행될 수도 있습니다.


## "스프링"의 의미

"Spring"이라는 용어는 맥락에 따라 다르게 사용됩니다.

일반적으로 "Spring"이라고 말할 때, 처음 시작한 Spring Framework 프로젝트 자체를 의미합니다.

시간이 지나며 Spring Framework 외에도 다양한 Spring 프로젝트들이 만들어졌고,

이제는  대부분 사람들이 "Spring"이라고 할 때는 여러  Spring 프로젝트 전체를 의미합니다.

다만, 이 문서에서는 Spring Framework 자체인 기본적인 부분에 집중합니다.

Spring Framework는 여러 모듈로 나누어져 있고, 애플리케이션에서는 필요한 모듈을 선택해서 사용할 수 있습니다.

여러 모듈의 중심에는 설정 모델과 의존성 주입 메커니즘이 있는 핵심 컨테이너 모듈이 있습니다.

이외에도 Spring Framework는 메시징, 트랜잭션 관리, 데이터 지속성 및 웹 아키텍처를 위한 기본적인 기능을 제공합니다.

또한, Servlet 기반의 Spring MVC 웹 프레임워크와, 이를 병행하는 Spring WebFlux 반응형 웹 프레임워크도 포함되어 있습니다.



모듈에 관한 주의 사항:

Spring Framework의 JAR 파일은 **Java 모듈 시스템**을 지원하여 **모듈 경로**에 배포될 수 있습니다.

즉, 모듈이 활성화된 애플리케이션에서 Spring Framework의 JAR 파일을 사용할 수 있다는 뜻입니다.

모듈이 활성화된 애플리케이션에서 Spring Framework의 JAR 파일은 [**`Automatic-Module-Name 이라는 매니페스트 항목`**](https://github.com/spring-projects/spring-framework/blob/082a8cfae3dc7a0b8befa3f4c310cf68f4de41ab/gradle/spring-module.gradle#L52)을 포함하고 있습니다. 

이 항목은 JAR 파일의 실제 이름과는 별개로 **안정적인 모듈 이름**을 정의하여 프로그램에서 각 JAR 파일을 정확히 참조할 수 있도록 합니다.

안정적인 모듈 이름 정의에는 JAR 파일의 이름에서 `점(.)` 대신 `하이픈(-)`을 사용하는 규칙이 적용됩니다.

예를 들어 `spring.core`, `spring.context` jar파일의 모듈 이름은 `spring-core`나 `spring-context`와 같이 변경됩니다.

물론, Spring Framework의 JAR 파일은 클래스패스에서도 문제 없이 작동합니다.

## '스프링과 스프링 프레임워크'의 역사

스프링은 [J2EE](https://ko.wikipedia.org/wiki/%EC%9E%90%EC%B9%B4%EB%A5%B4%ED%83%80_EE) 초기 사양의 복잡성에 대응하여 2003년 탄생했습니다.

일부에서는 Java EE와 현대판 후속작인 자카르타 EE가 Spring과 경쟁하고 있다고 하지만, 실제로는 상호보완적입니다.

스프링 프로그래밍 모델은 자카르타 EE 플랫폼 사양을 따르지 않고, 기존 EE 사양에서 엄선된 개별 사양과 통합됩니다:
* Servlet API ([JSR 340](https://jcp.org/en/jsr/detail?id=340))
* WebSocket API ([JSR 356](https://www.jcp.org/en/jsr/detail?id=356))
* Concurrency Utilities ([JSR 236](https://www.jcp.org/en/jsr/detail?id=236))
* JSON Binding API ([JSR 367](https://www.jcp.org/en/jsr/detail?id=367))
* Bean Validation ([JSR 303](https://www.jcp.org/en/jsr/detail?id=303))
* JPA ([JSR 338](https://www.jcp.org/en/jsr/detail?id=338))
* JMS ([JSR 914](https://www.jcp.org/en/jsr/detail?id=914))
* 필요한 경우, 트랜잭션 조정을 위한 JTA/JCA 설정도 지원합니다.

또한 스프링 프레임워크는 애플리케이션 개발자가 스프링에서 제공하는 전용 메커니즘 대신, 표준화된 Dependency Injection (JSR 330)과 Common Annotations (JSR 250) 사양을 선택하여 사용할 수 있도록 지원합니다.

스프링 프레임워크는 개발자가 스프링 전용 메커니즘 대신 선택하여 사용할 수 있도록 Dependency Injection ([JSR 330](https://www.jcp.org/en/jsr/detail?id=330)) 및 Common Annotations ([JSR 250](https://www.jcp.org/en/jsr/detail?id=250)) 사양을 지원합니다.

원래 이러한 사양은 `javax` 패키지를 기반으로 했습니다.

Spring Framework 6.0부터는 Jakarta EE 9 수준으로 업그레이드되었으며, 이는 Servlet 5.0+, JPA 3.0+ 등을 포함하고, 전통적인 javax 패키지 대신 jakarta 네임스페이스를 기반으로 합니다.

EE 9가 최소 지원 버전으로 설정되었고, EE 10도 이미 지원됩니다.

Spring은 Jakarta EE API의 발전을 위한 즉시 사용 가능한 지원을 제공할 준비가 되어 있습니다. Spring Framework 6.0은 Tomcat 10.1, Jetty 11, Undertow 2.3와 완전히 호환되며, Hibernate ORM 6.1과도 호환됩니다.

Java/Jakarta EE는 시간이 지나면서 애플리케이션 개발에서 중요한 역할을 맡게 되었습니다.

초기 J2EE와 Spring에서는 애플리케이션을 서버에 배포하는 방식으로 개발하였습니다.

그러나 오늘날 Spring Boot의 도움으로 애플리케이션은 DevOps 및 클라우드 친화적인 방식으로 개발되고 있으며, 서블릿 컨테이너가 내장되어 있어 변경이 매우 간편합니다.

Spring Framework 5부터는 WebFlux 애플리케이션이 서블릿 API를 직접 사용하지 않으며, 서블릿 컨테이너가 아닌 서버(예: Netty)에서도 실행될 수 있습니다.

Spring은 끊임없이 혁신하고 발전하고 있습니다. Spring Framework 외에도 Spring Boot, Spring Security, Spring Data, Spring Cloud, Spring Batch와 같은 다양한 다른 프로젝트들이 존재합니다.

각 프로젝트는 자체 소스 코드 저장소, 이슈 추적기, 릴리스 주기를 가지고 있다는 점을 기억하는 것이 중요합니다.

모든 Spring 프로젝트의 전체 목록은 spring.io/projects에서 확인할 수 있습니다.

##디자인 철학

스프링 프레임워크를 학습할 때는 기능만이 아니라, 어떤 원칙을 따르는지 아는게 중요합니다.

스프링 프레임워크의 기본 원칙은 다음과 같습니다:

* 모든 단계에서 선택의 자유를 제공한다.

스프링을 사용하면 설계 결정을 가능한 한 늦게 할 수 있도록 유연성을 제공합니다.

예를 들어, 코드를 수정할 필요 없이 설정만 변경하여 데이터베이스와의 연동을 처리하는 영속성 제공자(Persistence Provider, JPA 구현체)를 교체할 수 있습니다.

많은 인프라 문제와 서드파티 API들과 통합하는 경우도 마찬가지 입니다.


* 다양한 관점을 수용한다.

스프링은 유연성을 중시하며, 특정 방식으로 작업 해야한다고 강요하지 않습니다.

다양한 애플리케이션 요구사항과 관점을 지원할 수 있도록 설계되었습니다.


* 하위 호환성을 유지한다

스프링에 의존하는 애플리케이션과 라이브러리가 쉽게 유지보수 될 수 있도록 돕습니다.
여러 JDK 버전 및 서드파티 라이브러리와의 호환성을 신중히 관리하여 버전 간 변화로 발생할 수 있는 문제를 최소화하도록 신중히 업데이트 해왔습니다.


* API를 신경써서 설계합니다

스프링 팀은 직관적이고, 여러 버전과 긴 시간 동안 안정적으로 사용할 수 있는 API를 설계하기 위해 많은 시간과 노력을 기울입니다.


* 코드 품질에 대해 높은 기준을 유지합니다.

스프링 프레임워크는 몇 안 되는 패키지 간 순환 의존성이 없는 깔끔한 코드 구조를 유지하는 프로젝트로, 이러한 코드 품질을 위해 많은 노력을 기울이고 있습니다.

특히 의미가 명확하고, 최신 정보를 담으며, 정확한 Javadoc을 제공함으로써 개발자들이 더욱 효율적으로 활용할 수 있도록 돕고 있습니다.


## 피드백과 기여
사용 방법에 대한 질문이나 문제 진단 및 디버깅이 필요하다면, Stack Overflow를 사용하는 것이 좋습니다.

[여기](https://stackoverflow.com/questions/tagged/spring+or+spring-mvc+or+spring-aop)에서 Stack Overflow에서 사용 가능한 추천 태그 목록을 확인할 수 있습니다.

스프링 프레임워크에서 문제가 있다고 확신하거나 기능을 제안하고 싶다면, [GitHub Issues](https://github.com/spring-projects/spring-framework/issues)를 이용해 주세요.

문제에 대한 해결책이나 수정 제안이 있다면 [GitHub](https://github.com/spring-projects/spring-framework)에서 Pull Request를 제출할 수 있습니다.

하지만, 단순한 문제를 제외한 대부분의 경우, issue tracker에 티켓을 생성하여 토론을 진행하고, 이후 참고할 수 있도록 기록을 남기는 것이 좋습니다.

자세한 내용은 [CONTRIBUTING 가이드라인](https://github.com/spring-projects/spring-framework/tree/main/CONTRIBUTING.md)과 최상위 프로젝트 페이지에서 확인할 수 있습니다.


## 시작하기
스프링을 시작하는 경우, [스프링 부트](https://spring.io/projects/spring-boot) 기반 애플리케이션을 만들어 스프링 프레임워크를 사용하는 것이 좋습니다.

스프링 부트는 스프링 기반 애플리케이션 제작에 필요한 설정을 빠르게 생성할 수 있도록 해줍니다. (옵션도 선택이 가능합니다.)

스프링 부트는 스프링 프레임워크를 기반으로 하며, 세부적인 설정보다 기본적인 설정을 선호하여 최대한 빨리 실행될 수 있도록 설계되었습니다.

스프링 프로젝트를 만들기 위해 [start.spring.io](https://start.spring.io/)에 접속하여 기본 프로젝트를 생성하거나 ['RESTful 웹 서비스 구축 시작하기'](https://spring.io/guides/gs/rest-service)와 같은 [시작 가이드](https://spring.io/guides) 중 하나를 따라할 수 있습니다.

이 가이드는 이해하기 쉬울 뿐 아니라, 매우 구체적인 작업을 중심으로 구성되어 있고, 대부분 Spring Boot를 기반으로 합니다.
 
또한 특정 문제를 해결할 때 고려해야 할 다른 Spring 프로젝트들도 다루고 있습니다.