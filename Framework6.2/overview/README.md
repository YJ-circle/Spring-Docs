# Spring Framework Overview

Spring Framework 6.0부터는 Java 17 이상이 필요합니다.

스프링은 기업 환경에서 자바를 활용해 애플리케이션을 쉽게 개발할 수 있도록 필요한 모든 것을 지원합니다. 

또한, Groovy (그루비) 와 Kotlin (코틀린) 같은 JVM 대체 언어도 지원하며, 애플리케이션의 요구에 맞춰 다양한 아키텍처(구조)를 유연하게 설계할 수 있습니다.

스프링 커뮤니티를 통해 오랜 시간 동안 다양한 실제 사용 사례에 대한 피드백을 받아 지속적으로 발전하였습니다.

그 결과 다양한 환경에서 유연하게 활용될 수 있게 되었습니다

예를 들어, 대규모 환경에서는 애플리케이션이 오랫동안 운영되며, JDK와 애플리케이션 서버의 업그레이드를 개발자가 임의로 할 수 없는 상황이 있습니다.

또한 클라우드 환경에서 서버가 내장된 하나의 JAR 파일로  실행될 수도 있습니다.

배치 작업이나 시스템 통합 작업처럼 서버 없이 독립적으로 실행될 수도 있습니다.


## "스프링"의 의미

"Spring"이라는 용어는 맥락에 따라 다르게 사용됩니다.

일반적으로 "Spring"이라고 말할 때, 처음 시작한 Spring Framework 프로젝트 자체를 의미합니다.

시간이 지나며 Spring Framework 외에도 다양한 Spring 프로젝트들이 만들어졌고,

이제는  대부분 사람들이 "Spring"이라고 할 때는 여러  Spring 프로젝트들, 전체를 의미합니다.

다만, 이 문서에서는 Spring Framework 자체인 기본적인 부분에 집중합니다.

Spring Framework는 여러 모듈로 나누어져 있고,  프로그램은 필요한 모듈을 선택해서 사용할 수 있습니다.

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