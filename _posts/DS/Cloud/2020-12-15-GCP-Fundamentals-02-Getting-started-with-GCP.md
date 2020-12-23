---
layout: post
title: "02: Getting Started with GCP"
category: "DS/Cloud"
comments: true
tags: ["Cloud", "GCP", "Google"]
feature-img: "assets/img/44.jpg"
feature-title: ""
use_math: true
series: "GCP Fundamentals"
summary: "본격적으로 시작해보자!"
---

# 학습 목표

1. Google Cloud Platform에서 프로젝트, 폴더 및 조직 노드의 용도를 알기
2. ID 및 액세스 관리의 목적 및 사용 사례 설명
3. Google Cloud Platform과 상호 작용하는 방법을 알기
4. Cloud Launcher를 사용하여 솔루션 배포를 구축하기

GCP에서 워크로드를 실행할 때 프로젝트를 사용하여 워크로드를 구성한다. Google Cloud Identity와 액세스 관리(IM 또는 IAM이라고도 함)를 사용하여 누가 무엇을 할 수 있는지 제어할 수 있다. 

또 이러한 기능을 여러 인터페이스를 선택하여 연결할 수 있다. 이번에는 이러한 기본 사항을 사용해 보는 것을 기반으로 시작한다.

프로젝트는 GCP에서 사용하는 리소스를 구성하는 주요 방법이다. 일반적으로 공통적인 비즈니스 목표를 기반으로 관련 리소스를 그룹화하는 데 사용한다. 최소한의 특권의 원칙은 클라우드든 사내든 모든 종류의 컴퓨팅 인프라를 관리하는 데 매우 중요하다. 이 원칙은 각 **사용자가 자신의 작업을 수행하는 데 필요한 권한**만 가지는 것을 말한다. 최소 권한 환경에서 사람들은 전체 종류의 오류로부터 보호된다. 

예를 들어보자. 내 동료가 우연히 실행 중인 생산 데이터베이스를 삭제한 적이 있다. 그러지 말았어야 했는데 시스템에서 루트 사용자로 일하고 있었기 때문이다.


<img width="871" alt="스크린샷 2020-12-16 오후 5 02 21" src="https://user-images.githubusercontent.com/37871541/102321037-78546680-3fc0-11eb-807f-d7ad7e74d35f.png">{: .center width="80%"}


GCP 고객은 IM을 사용하여 최소한의 특권을 구현하고, 모든 사람이 더 생산적으로 일할 수 있도록 한다. GCP의 관리 계층과 상호 작용하는 네 가지 방법은 웹 기반 콘솔, SDK 및 SDK 및 명령줄 툴, API, 모바일 애플리케이션 등이다. 이번 챕터에서는 콘솔과 명령줄 도구를 이용한다.

사내 인프라에 애플리케이션을 구축하면 전체 스택 보안을 책임져야 한다. 하드웨어의 물리적 보안과 해당 하드웨어가 있는 시설에서 디스크에 있는 데이터를 암호화하여 네트워크의 무결성에 이르기까지 애플리케이션에 저장된 컨텐츠를 안전하게 보호해야 한다.

애플리케이션을 Google Cloud Platform으로 이동하면 Google은 많은 하위 보안 계층을 처리한다. 그것의 규모 때문에, 구글은 대부분의 고객들이 스스로 할 수 있는 것보다 더 높은 수준의 보안을 제공할 수 있다. 보안 스택의 상위 계층은 고객의 책임으로 남는다. 구글은 IAM과 같은 도구를 제공하여 고객이 이러한 계층에서 선택한 정책을 구현할 수 있도록 지원한다.


# The Google Cloud Platform resource hierarchy

<img width="871" alt="스크린샷 2020-12-16 오후 5 20 46" src="https://user-images.githubusercontent.com/37871541/102322836-0af60500-3fc3-11eb-99cc-6bd7f7312ccc.png">{: .center width="80%"}

Bottom-up 방식으로 GCP 리소스 계층을 가장 쉽게 이해할 수 있다. 가상 시스템, 클라우드 스토리지 버킷, 테이블 및 빅 쿼리 등 GCP에서 사용하는 모든 리소스가 프로젝트로 구성된다. 

선택적으로 이러한 프로젝트를 폴더로 구성할 수 있다. 폴더는 다른 폴더를 포함할 수 있다. 조직에서 사용하는 모든 폴더와 프로젝트를 조직 노드 아래에 가져올 수 있다. 프로젝트, 폴더 및 조직 노드는 모두 정책을 정의할 수 있는 위치이다. 일부 GCP 리소스를 사용하면 앞서 언급한 클라우드 스토리지 버킷과 같이 개별 리소스에 정책도 적용할 수 있다. 

한편 정책은 계층에서 **아래로 상속**된다. 모든 Google Cloud 플랫폼 리소스는 프로젝트에 속해 있다. 프로젝트는 API 관리, 빌링 및 공동작업자 추가/제거, 기타 Google 서비스 등과 같은 GCP 서비스를 활성화 및 사용하기 위한 기반이다. 각 프로젝트는 별도의 구획이며 각 리소스는 정확히 하나의 구획에 속한다. 

<img width="871" alt="스크린샷 2020-12-16 오후 5 21 31" src="https://user-images.githubusercontent.com/37871541/102322917-25c87980-3fc3-11eb-9d82-1d5eeecede5e.png">{: .center width="80%"}

프로젝트 소유자와 사용자는 서로 다를 수 있다. 프로젝트 소유자와 사용자는 별도로 작성되고 개별적으로 관리된다. 각 GCP 프로젝트에는 사용자가 할당하는 **프로젝트 ID와 이름**이 있다. 프로젝트 ID는 영구적이고 변경 불가능한 식별자로 GCP 전체에서 고유해야 한다. 여러 컨텍스트에서 프로젝트 ID를 사용하여 GCP와 함께 작업할 프로젝트를 지정할 수 있다. 

반면에 프로젝트 이름은 사용자의 편의를 위해 지정되며 지정할 수 있다. 또한 GCP에는 각 프로젝트에 고유한 프로젝트 번호가 할당되어 다양한 컨텍스트에서 디스플레이가 표시된다. 하지만 그것을 사용하는 것은 대부분 이 과정의 범위를 벗어난다. 일반적으로 프로젝트 ID는 사람이 읽을 수 있는 문자열로 만들어지며 프로젝트를 참조하기 위해 자주 사용한다.


<img width="871" alt="스크린샷 2020-12-16 오후 5 22 10" src="https://user-images.githubusercontent.com/37871541/102322980-3c6ed080-3fc3-11eb-9ca0-47bf33d2997d.png">{: .center width="80%"}



그럴 필요는 없지만 프로젝트를 폴더로 구성할 수 있다. 폴더를 사용하면 더 관리를 효율적으로 할 수 있다. 예를 들어 폴더를 사용하여 조직의 여러 부서, 팀, 응용프로그램 또는 환경을 나타낼 수 있다. 폴더를 통해 팀은 독립적으로 작업할 수 있도록 관리 권한을 위임할 수 있다. 


<img width="871" alt="스크린샷 2020-12-16 오후 5 22 37" src="https://user-images.githubusercontent.com/37871541/102323032-4c86b000-3fc3-11eb-9d62-5b4c28d2116b.png">{: .center width="80%"}


폴더의 리소스는 폴더에서 IAM 정책을 상속한다. 따라서 프로젝트 3과 4를 동일한 팀에서 설계로 관리하는 경우 IAM 정책을 B 폴더에 넣을 수 있다. 반대로 이러한 정책의 중복 사본을 프로젝트 3과 프로젝트 4에 넣는 것은 지루하고 오류가 발생하기 쉽다.  폴더를 사용하려면 계층 맨 위에 조직 노드가 필요하다. 


<img width="871" alt="스크린샷 2020-12-16 오후 5 23 13" src="https://user-images.githubusercontent.com/37871541/102323099-61fbda00-3fc3-11eb-9eae-e4fd08a46091.png">{: .center width="80%"}


뭔가 어려워 보인다. 하지만 그렇지 않다. 효율적으로 관리하기 위한 계층도에 대해서 설명하는 것이다. 회사의 모든 프로젝트를 하나의 구조로 구성하는 것이 좋다. 대부분의 기업은 리소스가 사용되는 방식에 대한 중앙 집중식 가시성을 확보하고 정책을 중앙에서 적용하기를 원한다. 이것이 바로 조직 노드의 용도이다. 이런 계층도의 최상층이라 생각하면 된다. 

<img width="871" alt="스크린샷 2020-12-16 오후 5 23 55" src="https://user-images.githubusercontent.com/37871541/102323165-7a6bf480-3fc3-11eb-8558-77ec8219fe6f.png">{: .center width="80%"}


이러한 조직을 관리하기 위해서는 특별한 권한을 가진 사람들이 필요하다. 예를 들어 권한이 있는 사용자만 정책을 변경할 수 있도록 조직 정책 관리자를 지정할 수 있다. 

또한 프로젝트 작성자 역할을 할당할 수도 있다. 이것은 누가 비용을 지출할 수 있는지 제어할 수 있는 좋은 방법이다. 그러면 조직 노드를 어떻게 확보할 수 있을까?

사실, G Suite의 고객인지 여부에 따라 답이 달라진다. G Suite 도메인이 있는 경우 GCP 프로젝트는 자동으로 조직 노드에 속하게 된다. 그렇지 않으면 Google Cloud Identity를 사용하여 생성할 수 있다.


<img width="871" alt="스크린샷 2020-12-16 오후 5 25 42" src="https://user-images.githubusercontent.com/37871541/102323358-ba32dc00-3fc3-11eb-9b67-89f95f60064d.png">{: .center width="80%"}

명심해야 할 중요한 규칙이 하나 있다. 상위 수준에서 구현된 정책은 하위 수준에서 부여된 액세스 권한을 제거할 수 없다. 예를 들어, 책장 프로젝트에 적용된 정책이 사용자에게 클라우드 저장소 버킷을 수정할 수 있는 권한을 Pat에게 부여하지만 조직 수준의 정책은 Pat이 클라우드 저장소 버킷을 변경하지 않고 볼 수만 있다고 가정해 보자. 더 관대한 정책(읽기/쓰기 권한) 이 효력을 발휘한다. 

# Identity and Access Management (IAM)

<img width="871" alt="스크린샷 2020-12-17 오후 3 18 55" src="https://user-images.githubusercontent.com/37871541/102451085-30dee080-407b-11eb-8c87-99ffa51b3b9a.png">{: .center width="80%"}


IAM을 통해 관리자는 특정 리소스에 대한 작업을 수행할 수 있는 사용자를 인증할 수 있다. IAM 정책에는 "누구" 부분, "무엇을 할 수 있는지" 부분 및 "어떤 리소스에서" 부분이 있다. 

<img width="871" alt="스크린샷 2020-12-17 오후 3 20 07" src="https://user-images.githubusercontent.com/37871541/102451177-5a980780-407b-11eb-8672-07291e16b960.png">{: .center width="80%"}

"누구" 부분은 **사용자 이름**을 지정한다. IAM 정책의 "누구" 부분은 Google 계정, Google 그룹, Service 계정, 전체 G Suite 또는 Cloud Identity 도메인으로 정의할 수 있다. "할 수 있는 일" 부분은 IAM **역할**에 의해 정의된다. IAM 역할은 **사용 권한 모음**이다. 대부분의 경우 의미 있는 작업을 수행하려면 둘 이상의 권한이 필요하다. 예를 들어 프로젝트의 인스턴스를 관리하려면 인스턴스를 생성, 삭제, 시작, 중지 및 변경해야 한다. 따라서 사용 권한은 관리하기 쉬운 역할로 함께 그룹화된다. 

<img width="871" alt="스크린샷 2020-12-17 오후 3 22 14" src="https://user-images.githubusercontent.com/37871541/102451353-a64ab100-407b-11eb-81e6-c5a0549f4058.png">{: .center width="80%"}

IAM 정책의 "누구" 부분은 Google 계정, Google 그룹, Service 계정 또는 전체 G Suite 또는 Cloud Identity 도메인일 수 있습니다. Cloud IAM에는 세 가지 역할이 있다. 각자 차례대로 이야기합시다. 


<img width="871" alt="스크린샷 2020-12-17 오후 3 24 03" src="https://user-images.githubusercontent.com/37871541/102451483-e6aa2f00-407b-11eb-9117-833debd4989c.png">{: .center width="80%"}


원시적 역할은 광범위합니다. GCP 프로젝트에 적용하면 해당 프로젝트의 모든 리소스에 영향을 미칩니다. **소유자, 편집자 및 뷰어** 역할이다. 

지정된 리소스의 **뷰어**인 경우 상태를 검사하지만 변경할 수는 없다. **편집자**인 경우 뷰어가 수행할 수 있는 모든 작업을 수행할 수 있으며 뷰어의 상태를 변경할 수도 있다. 또한 **소유자**인 경우 편집자가 할 수 있는 모든 작업을 수행할 수 있으며 리소스에 대한 역할 및 사용 권한도 관리할 수 있다. 프로젝트의 소유자 역할도 청구 설정을 한 가지 더 수행할 수 있다. 

기업들은 누군가가 프로젝트의 리소스를 변경할 권리 없이 프로젝트에 대한 청구서를 관리할 수 있기를 바란다. 그렇기 때문에 다른 사용자에게 **청구 관리자 역할을 부여**할 수 있다. 


<img width="871" alt="스크린샷 2020-12-17 오후 3 26 13" src="https://user-images.githubusercontent.com/37871541/102451630-34bf3280-407c-11eb-8f54-7aa170363c8c.png">{: .center width="80%"}

또한 너무 한 담당자의 역할이 커지는 것을 방지하기 위해서 세분화된 유형까지 역할 분배가 가능하다. 이런 경우에 대한 유형이 predefined role이다. 예를 들어 이 과정 후반부에서 가상 머신을 서비스로 제공하는 컴퓨팅 엔진에 대해 살펴보자. Compute Engine은 미리 정의된 역할 집합을 제공하며 이러한 역할을 특정 프로젝트, 지정된 폴더 또는 전체 조직의 Compute Engine 리소스에 적용할 수 있다. 


# Interacting with Google Cloud Platform

Google Cloud Platform과 상호 작용할 수 있는 4가지 방법이 있다. 

1. Console
2. SDK, Cloud Shell
3. Mobile App
4. REST API

GCP 콘솔은 웹 기반 관리 인터페이스이다. 사용하는 모든 프로젝트와 리소스를 보고 관리할 수 있다. 또한 GCP 서비스의 API를 활성화, 비활성화 및 탐색할 수 있다. 

또한 Cloud Shell에 액세스할 수 있다. GCP에 대한 **명령줄 인터페이스**로 브라우저에서 쉽게 액세스할 수 있다. Cloud Shell에서는 Google Cloud Software Development Kit SDK에서 제공하는 툴을 먼저 설치할 필요 없이 사용할 수 있다. Google Cloud SDK는 GCP에서 리소스 및 애플리케이션을 관리하는 데 사용할 수 있는 도구 세트이다. 여기에는 Google Cloud Platform 제품 및 서비스에 대한 기본 명령줄 인터페이스를 제공하는 gcloud 툴이 포함된다. 구글 클라우드 스토리지용 gsutil과 BigQuery용 bq도 있다. SDK 명령을 실행하는 가장 쉬운 방법은 GCP 콘솔에서 Cloud Shell 버튼을 클릭하는 것이다. 이러한 모든 명령이 이미 설치되어 있는 가상 시스템의 **웹 브라우저**에 명령줄이 표시된다. 또한 랩톱, 가상 시스템 및 기타 클라우드의 온사이트 서버 등 자신의 컴퓨터에 SDK를 설치할 수 있다. SDK는 **도커** 이미지로도 사용할 수 있어 사용하기 쉽고 깔끔한 방법이다. 

GCP를 구성하는 서비스는 사용자가 **작성하는 코드가 이를 제어할 수 있도록** 애플리케이션 프로그래밍 인터페이스를 제공한다. 이러한 API를 RESTful이라고 합니다. 다시 말해, 그들은 대표적인 상태 전이 패러다임을 따른다. 우리는 그것이 무엇을 의미하는지 자세히 말할 필요가 없다. 기본적으로, 코드는 웹 브라우저가 웹 서버와 대화하는 것과 같은 방식으로 구글 서비스를 사용할 수 있다는 것을 의미한다. API는 리소스 및 GCP의 이름을 URL로 지정합니다. 코드는 JSON을 사용하여 API에 정보를 전달할 수 있으며, 이는 웹을 통해 텍스트 정보를 전달하는 매우 일반적인 방법입니다. 또한 사용자 로그인 및 액세스 제어를 위한 개방형 시스템이 있습니다. GCP 콘솔을 사용하여 API를 설정 및 해제할 수 있습니다. 많은 API는 기본적으로 해제되어 있으며, 많은 API는 할당량 및 제한과 연관되어 있습니다. 이러한 제한사항은 자원을 실수로 사용하지 않도록 보호합니다. 필요한 API만 사용하도록 설정할 수 있으며 리소스가 더 필요할 때 할당량 증가를 요청할 수 있습니다. 예를 들어 GCP 리소스를 제어해야 하는 애플리케이션을 작성하는 경우 API를 올바르게 사용해야 합니다. 그러기 위해서는 APIs Explorer를 사용해야 합니다. GCP 콘솔에는 APIs Explorer라는 도구가 포함되어 있어 API에 대해 대화식으로 배울 수 있습니다. 이를 통해 사용 가능한 API와 버전을 확인할 수 있습니다. 이러한 API는 매개 변수와 해당 API에 대한 설명서가 내장되어 있어야 합니다. 사용자 인증으로도 API를 대화식으로 사용해 볼 수 있습니다. API를 탐색했으며 이 API를 사용하는 애플리케이션을 만들 준비가 되었다고 가정해 보십시오. 처음부터 코딩 작업을 시작해야 합니까? 아니오. 구글은 당신의 코드에서 GCP를 호출하는 업무에서 많은 번거로움을 덜어주는 클라이언트 라이브러리를 제공합니다. 도서관에는 두가지 종류가 있다. Cloud Client Libraries는 최신 Google 클라우드이며 API에 권장되는 라이브러리입니다. 그들은 각 언어의 고유 스타일과 관용구를 채택한다. 반면에 Cloud Client Library는 최신 서비스와 기능을 지원하지 않는 경우도 있습니다. 이 경우 Google API 클라이언트 라이브러리를 사용하여 원하는 언어를 사용할 수 있습니다. 이 도서관은 일반성과 완전성을 위해 설계되었다. 마지막으로, 개발자들뿐만 아니라 모든 사람들이 관심을 가질 수 있는 한 가지 툴이 더 있습니다. GCP에서 사용하는 리소스를 검사하고 관리할 수 있는 Android 및 iOS용 모바일 앱이 있습니다. 대시보드를 작성하여 필요한 정보를 한 눈에 볼 수 있습니다.



