# 더 자바 코드를 조작하는 다양한 방법

[Inflearn. 더 자바 코드를 조작하는 다양한 방법](https://www.inflearn.com/course/the-java-code-manipulation)

## 1장 : JVM(Java Virtual Machine)

- https://medium.com/webeveloper/jvm-java-virtual-machine-architecture-94b914e93d86

## 2장 : 바이트 코드 조작

### 코드 커버리지는 어떻게 측정할까?

- 코드 커버리지(Code Coverage)
  - 테스트 코드가 내 소스 코드를 얼만큼 Cover 하는지 퍼센트(%) 로 나타낸것
  
#### JaCoCo 
  
- 의존성 추가
  
```xml
<plugin> 
    <groupId>org.jacoco</groupId> 
    <artifactId>jacoco-maven-plugin</artifactId> 
    <version>0.8.4</version> 
    <executions> 
        <execution> 
            <goals> 
                <goal>prepare-agent</goal> 
            </goals> 
        </execution> 
        <execution> 
            <id>report</id> 
            <phase>prepare-package</phase> 
            <goals> 
                <goal>report</goal> 
            </goals> 
        </execution> 
    </executions> 
</plugin> 
```

- 메이븐 빌드
  - mvn clean verify 

- 코드 커버리지 실패할 경우 빌드 실패 하도록 설정

```xml
<execution> 
    <id>jacoco-check</id> 
    <goals> 
        <goal>check</goal> 
    </goals> 
    <configuration> 
        <rules> 

           <rule> 
                <element>PACKAGE</element> 
                <limits> 
                    <limit> 
                        <counter>LINE</counter> 
                        <value>COVEREDRATIO</value> 
                        <minimum>0.50</minimum> 
                    </limit> 
                </limits> 
            </rule> 
        </rules> 
    </configuration> 
</execution> 
``` 

- 실행된 결과 확인
  - target
    - site
      - jacoco
        - index.html (우클릭, Run)
 

> https://www.eclemma.org/jacoco/trunk/doc/index.html
>
> http://www.semdesigns.com/Company/Publications/TestCoverage.pdf
