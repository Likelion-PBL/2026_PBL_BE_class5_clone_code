# 5주차 멤버 관리 시스템 (Java/SpringBoot 6주차 베이스 코드)

Java/SpringBoot 커리큘럼 6주차의 베이스가 되는 5주차 코드입니다.

## 프로젝트 구조

```
src/class5/
├── role/                  # 역할 (멤버) 도메인
│   ├── Role.java          # 추상 클래스 - 공통 멤버 정보
│   ├── Lion.java          # 아기사자
│   └── Staff.java         # 운영진
├── policy/                # 과제 제출 정책
│   ├── SubmissionPolicy.java        # 정책 인터페이스
│   ├── LionSubmissionPolicy.java    # 아기사자 제출 정책
│   └── StaffSubmissionPolicy.java   # 운영진 제출 정책
└── step2/                 # 의존성 주입(DI) 적용 버전
    ├── MemberRepository.java        # 저장소 인터페이스
    ├── MemoryMemberRepository.java  # 메모리 기반 저장소 구현체
    ├── MemberService.java           # 비즈니스 로직 (서비스)
    └── Main.java                    # 실행 진입점
```

## 6주차에서 할 일: Spring Boot 프로젝트로 이전

### 1. 프로젝트 생성

- [Spring Initializr](https://start.spring.io/)에서 프로젝트를 생성한다.
- **Spring Web** 의존성을 추가한다.
- **Java 17**, **Gradle**을 사용한다.

### 2. 5주차 클래스 복사

아래 클래스들을 Spring Boot 프로젝트의 적절한 패키지로 복사한다.

| 대상 | 설명 |
|------|------|
| `MemberRepository` | 저장소 인터페이스 |
| `MemoryMemberRepository` | 메모리 기반 저장소 구현체 |
| `MemberService` | 비즈니스 로직 처리 |
| `role/` 패키지 | `Role`, `Lion`, `Staff` |
| `policy/` 패키지 | `SubmissionPolicy`, `LionSubmissionPolicy`, `StaffSubmissionPolicy` |

## 핵심 개념

- **추상 클래스 & 인터페이스**: `Role`(추상 클래스), `MemberRepository`(인터페이스)를 통한 다형성
- **의존성 주입(DI)**: `MemberService`가 `MemberRepository` 인터페이스에 의존하여 구현체 교체 가능
- **전략 패턴**: `SubmissionPolicy`를 통해 역할별 과제 제출 정책을 분리
