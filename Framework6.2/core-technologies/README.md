# 핵심 기술

이 장에서는 스프링 프레임워크에 필수적인 모든 기술을 다룹니다.

기술들 중 가장 중요한 것은 스프링 프레임웤의 제어의 역전(Inversion of Control, IoC) 컨테이너 입니다.

스프링 프레임워크의 IoC 컨테이너에 대한 설명에 이어, 스프링의 AOP 기술에 대한 포괄적인 설명이 이어집니다.

스프링 프레임워크는 자체 AOP 프레임 워크가 있습니다.

이 AOP 프레임 워크는 개념적으로 이해하기 쉽고 자바 엔터프라이즈 프로그래밍에서 AOP 요구 사항의 80%를 효과적으로 해결합니다.

스프링의 AspectJ 통합에 대한 내용도 제공됩니다. AspectJ는 현재 Java 엔터프라이즈 분야에서 가장 풍부한 기능을 갖추고 있으며, 가장 성숙한 AOP 구현체로 평가받고 있습니다.

AOT(Ahead-Of-Time) 처리 기능은 애플리케이션을 미리 최적화하는 데 사용될 수 있습니다.

이는 일반적으로 [GraalVM](https://www.graalvm.org/)을 사용하여 [네이티브 이미지 배포](https://thelightway.gitbook.io/spring-study-framework6.2/packaging/graalvm-native-images)를 위해 사용됩니다.