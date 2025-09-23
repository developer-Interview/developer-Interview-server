# 🍳 AI Product Cookbook

**비개발자도 AI를 활용해 나만의 프로덕트를 만들 수 있도록 돕는 가장 친절한 안내서**

안녕하세요\! 👋 `AI Product Cookbook`에 오신 것을 환영합니다.
이곳은 코딩 경험이 많지 않아도, '바이브 코딩(Vibe Coding)'과 같은 직관적인 방법과 강력한 AI 도구를 활용해 아이디어를 실제 프로덕트로 만들 수 있도록 돕는 공간입니다.

서버는 최신 기술 스택인 **Java 21**과 **Spring Boot**를 기반으로 구성하여, 여러분의 아이디어가 탄탄하고 확장 가능한 기술 위에서 실현될 수 있도록 안내할 것입니다.

자, 이제 나만의 프로덕트를 만들기 위한 첫걸음을 함께 내디뎌 볼까요? 🚀

-----

## 🎯 이 가이드의 목표

  * **프로젝트 기본 구조**를 이해하고 직접 설정할 수 있습니다.
  * 최신 **백엔드(서버)** 개발 환경을 직접 구성할 수 있습니다.
  * **프론트엔드** 코드를 담을 공간을 마련하고, 앞으로의 개발 방향을 이해합니다.
  * "나도 프로덕트를 만들 수 있다\!"는 자신감을 얻게 됩니다.

-----

## 🚀 시작하기 (Getting Started)

프로젝트를 시작하기 위해 필요한 준비물과 설정 과정을 안내합니다.

### 1\. 사전 준비물 (Prerequisites)

macOS 환경에서는 [Homebrew](https://www.google.com/search?q=https://brew.sh/index_ko)라는 패키지 관리자를 사용하면 개발 도구를 터미널 명령어로 쉽게 설치할 수 있습니다. 아래 가이드를 따라 필요한 프로그램들을 설치해 주세요.

#### 1단계: Homebrew 설치하기

터미널(`Terminal`) 앱을 열고 아래 명령어를 붙여넣어 Homebrew를 먼저 설치합니다. (이미 설치되어 있다면 이 단계는 건너뛰세요.)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### 2단계: Java Development Kit (JDK) 21 설치하기

Homebrew를 이용해 Java 21 버전을 설치합니다.

```bash
brew install openjdk@21
```

설치가 완료되면, 시스템이 Java를 인식할 수 있도록 아래 명령어를 추가로 입력해 주세요. (macOS 비밀번호를 물어볼 수 있습니다.)

```bash
sudo ln -sfn /opt/homebrew/opt/openjdk@21/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-21.jdk
```

설치가 잘 되었는지 확인하려면 터미널에 `java -version`을 입력하고 `openjdk version "21..."` 메시지가 보이는지 확인하세요.

#### 3단계: Git 설치하기

대부분의 macOS에는 Git이 이미 설치되어 있습니다. `git --version` 명령어로 확인해보고, 만약 설치되어 있지 않다면 아래 명령어로 설치합니다.

```bash
brew install git
```

#### 4단계: GUI 애플리케이션 설치하기

아래 프로그램들은 공식 홈페이지에서 직접 다운로드하여 설치하는 것이 더 간편합니다.

  * **[IntelliJ Community Edition](https://www.jetbrains.com/idea/download/)**: Java (Spring) 개발을 편리하게 도와주는 개발 도구(IDE)입니다.
  * **(선택) [Docker Desktop](https://www.docker.com/products/docker-desktop/)**: 나중에 Testcontainers 등 고급 테스트 환경을 구성할 때 필요합니다.

-----

### 2\. 프로젝트 설정 (Step-by-Step)

1.  **프로젝트 복제 (Clone)**
    터미널을 열고 아래 명령어를 입력해 이 프로젝트를 여러분의 컴퓨터로 가져옵니다.

    ```bash
    git clone https://github.com/jsoonworld/ai-product-cookbook.git
    cd ai-product-cookbook
    ```

2.  **프론트엔드 폴더 생성**
    서버 폴더는 다음 단계에서 자동으로 생성되므로, `frontend` 폴더만 미리 만들어 줍니다.

    ```bash
    mkdir frontend
    ```

3.  **백엔드(서버) 프로젝트 생성 및 추가**
    [**start.spring.io**](https://start.spring.io/) 사이트를 이용해 서버 프로젝트의 뼈대를 만듭니다.

      * **Project**: `Gradle - Groovy`
      * **Language**: `Java`
      * **Spring Boot**: 최신 안정 버전 (기본 선택된 버전)
      * **Project Metadata**:
          * Group: `com.cookbook`
          * Artifact & Name: `server`
      * **Java**: **`21`**
      * **Dependencies (의존성)**: 프로젝트의 목적에 맞게 아래 목록을 참고하여 자유롭게 추가하세요.
          * **✅ 기본 추천 (이것만으로도 시작은 충분해요\!)**
              * `Spring Web`: 웹 API 서버를 만들기 위한 필수 요소
              * `Spring Data JPA`: 데이터베이스 작업을 쉽게 처리하는 기능
              * `Lombok`: 코드를 간결하게 만들어주는 도우미
              * `H2 Database`: 설치 없이 바로 사용하는 테스트용 데이터베이스
          * **🚀 심화 선택 (프로젝트를 더 강력하게 만들고 싶을 때)**
              * **데이터베이스**: `MySQL Driver` (실제 서비스용 DB를 사용할 때)
              * **캐싱/메시징**: `Spring Data Redis`, `Spring for Apache Kafka` (대규모 트래픽 처리나 비동기 작업이 필요할 때)
              * **보안**: `Spring Security`, `OAuth2 Client` (로그인, 회원가입 기능이 필요할 때)
              * **테스트**: `Testcontainers` (실제 DB나 Kafka와 동일한 환경에서 테스트하고 싶을 때)

    설정 후 **GENERATE** 버튼을 눌러 `server.zip` 파일을 다운로드하세요. 그 다음, **다운로드한 zip 파일의 압축을 풀면 `server` 폴더가 생성됩니다.** 이 폴더를 `ai-product-cookbook` 프로젝트 폴더 안으로 그대로 옮기거나 복사해 주세요.

    최종 폴더 구조는 아래와 같아야 합니다.

    ```
    ai-product-cookbook/
    ├── frontend/
    └── server/      <- 압축을 풀어 생성된 폴더
    ```

4.  **프론트엔드(화면) 파일 생성**
    `frontend` 폴더 안에 간단한 시작 페이지 `index.html` 파일을 만듭니다.

    ```html
    <!DOCTYPE html>
    <html lang="ko">
    <head>
        <meta charset="UTF-8">
        <title>AI Product Cookbook</title>
    </head>
    <body>
        <h1>🍳 AI Product Cookbook에 오신 것을 환영합니다!</h1>
    </body>
    </html>
    ```

5.  **설정 확인**

      * **서버**: IntelliJ로 `server` 폴더를 열고, `ServerApplication.java` 파일을 찾아 실행 ▶️ 하세요. 콘솔에 `Tomcat started on port(s): 8080` 메시지가 보이면 성공입니다.
      * **프론트엔드**: `frontend/index.html` 파일을 웹 브라우저로 열어 환영 메시지가 보이는지 확인하세요.

-----

## ✅ 다음 단계 (Next Steps)

이제 여러분의 아이디어를 담을 그릇이 준비되었습니다. 앞으로 이 Cookbook에서는 다음 내용들을 다룰 예정입니다.

  * [ ] 첫 번째 API(데이터 요청 창구) 만들기
  * [ ] AI 프롬프트를 활용해 프론트엔드 화면 디자인하기
  * [ ] 서버와 프론트엔드를 연결하여 데이터 주고받기
  * [ ] 실제 클라우드 서버에 배포하기

-----

## 🙌 기여 및 질문 (Contributing)

이 프로젝트를 더 좋게 만들기 위한 어떤 아이디어나 기여도 환영합니다\! 궁금한 점이나 개선 제안이 있다면 언제든지 [Issues](https://www.google.com/search?q=https://github.com/jsoonworld/ai-product-cookbook/issues)를 통해 알려주세요.
