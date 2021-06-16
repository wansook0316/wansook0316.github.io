---
layout: post
title: "10: Project Planning and Management"
category: "DV/Concept"
comments: true
tags: [Concept, "Development Method"]
feature-img: "assets/img/78.jpg"
feature-title: ""
use_math: true
series: "Development Method"
summary: "프로젝트 계획과 관리는 어떻게 해야할까?"
---


* WBS
* Ghant Chart
* Man-Month


# Man-month

* `The mythical man-month`
* "지연되고 있는 소프트웨어프로젝트에 사람을 추가하는 것은 더 느리게 만들 뿐이다."
  * 한달에 몇명 필요한가?
  * 한사람이 한달동안 할 수 있는 일
  * 너무 쉽게 산출하면 안된다.
    * 개별 인력의 개발 능력을 생각안하기 때문.

    * 사람 더 넣는다고 단순히 효율이 증대되는 것이 아님
    * 사람 교육해서 쓰고 그러니 시간이 더 걸린다.
    * 그래서 해당 모델이 소프트웨어 개발에 있어서는 안 맞는다.
  * IBM OS/360을 만들면서 느낀 경험
  * 일정이 점점 지연되어서 개발자를 더 투입함
  * 실패함. 왜?
  * algol 컴파일러 개발했는데, 더 인력 투입하나마나 6개월 걸리는 작업이었다.
  * 소프트웨어 작업을 측정하는 것은 신화다.
  * 프로그래밍 프로젝트는 매우 복잡하다.
    * 애시당초 딱딱 업무가 끊어지기 어렵다.
    * 커뮤니케이션이 없으면 만들 수 없다.
      * 그래서 agile에서는 서로 대화하는 세션이 항상있는 것
    * 간트 차트에서 적은 액션과 사람자체를 그냥 연결할 수 없음
      * agile에서는 아침에 만나서, 리스팅하고 그걸 특정사람에게 임명
      * 임명할 때도 그사람에 대한 역량을 기반으로 임명함
    * 경험상 그래서 넣어봤자 프로젝트가 느려짐
    * 결국 대화가 필요한데 사람이 늘어나면 이 시간 자체가 늘어남
    * 어느 수준인지도 알아야되고, 즉 1:1대화를 한다면 n(n-1)/2 만큼의 만남이 필요함
    * 정리
      * 일을 딱딱 나눌 수 없다.
      * 대화가 필요하다. 뭘 잘하는 지 등등
      * 그래서 느려지는 경향이 있다.
* "No silver bullet"
  * 정해진 한가지 방법은 없음
  * 그 팀의 상황을 고려하여 해야 하는 것임
  * Open source를 활용한다고 쳐도 이를 수정해서 사용해야 하는 것임
  * 다양한 분야에 대해 이를 맞춰서 해야하는 것..
* The second-system effect
  * 일단 출시한 시스템의 다음 버전을 만든다고 생각하면 다시한번 생각하자.
  * 너무 많은 기능을, 아쉬운 것을 다 넣어서 만드는 것은 아닌가?
* Bug..
  * 에러를 줄이려다가 더 많은 에러를 만날 수도 있음
  * 치명적인 에러를 줄이고 자잘한 에러를 덜 신경써라
* Progress Tracking
  * Agile : 매일만나 얘기함
  * 일정 지연이 너무 많이 발생함
  * 매일 만나서 그냥 얘기해라
  * 아니면 주에한번 한달한번 하다가 하루씩 늦어지면 그렇게 되는 것임
  * 그렇게 해야 유기적으로 돌아감
* Conceptual integrity (조직 문화)
  * 제일 좋은 시스템은 설명할 필요가 없어야 함
  * 그럼 누군가가 일종의 철학을 만들어야 함
  * 회사에서는 개발 철학, 설게 철학 이라는 말을 많이함
  * 이러한 부분에 대해 개발팀이 모두 공유하고 있어야 함
* The manual
  * 누군가는 시스템의 메뉴얼, 규격을 써야 한다.
  * 문서 작성하지 말자고는 하지만, 사실 어느정도는 적어야 함
  * 그리고 소스코드 자체가 설명서일만큼 잘 작성해야 한다.
* The pilot system
  * 기술이 가능한지
  * 프로토타입을, 즉 핵심기능을 만들어보고 버리는 것
  * 그러면 이제 고객에 대해 줄 서비스에 대해 바꿀점을 잘 알고 줄 수 있게 됨
  * 이런 단계를 거치지 않으면 pilot 시스템에 국한되서 제공하게 될 것임
  * 미리한번 해보고 확인해봐라
* Formal documents
  * 어떤 목적? : 우리 프로젝트의 목적
  * 경비
  * 어떻게 달성할 것인지
  * Readme를 작성하는 것
* 프로젝트 일정 잡기
  * 프로젝트 시간을 추정할 때, 제품과 시스템에 대해서 고민해야 한다.
  * 간단한 프로그램짜는 것에 거의 3배정도의 시간이 걸린다.
  * 회의는 무의미한 시간이 많음.
  * 최대한 기술적 이슈에 대해 시간을 써라.
* Communication
  * 어떠한 방법을 써서라도 소통을 잘해라
  * 물어볼게 있으면 그냥 물어봐라
  * 아키텍쳐대로 만드는데, 이게 맞나? 물어봐
  * 물어봐서 불투명한 것을 제거한다.
* The surgical Team
  * 결국 팀안에 한명의 제대로된 개발자가 있는게 일의 효율이 좋다.
  * 좋은 프로그래머는 5~10배 성능차이가 난다.
  * (언제 저렇게 되나..)
* Code Freeze and system versioning
  * Freezing한다 그러면 손뗀다.
  * 의미 있는 버전이 나왔을 때 Freezing, versioning해라
* Specialized tools
  * 훌륭한 도구는 개발 기간 단축, 성능 향상
  * 도구를 만들어서 해결해라
  * 팀이 필요로하면 도구를 만들어라
  * 그리고 그 도구를 만드는 역할을 한다면 더 좋다.
  * 대부분 회사들의 시니어는 도구 개발하는 쪽에 있는 경우가 많다.
  * 도구? : 수작업이 불편하면 자동화 도구
  * 일정 단축, 품질 향상
* 개발 비용을 낮춰라
  * 당시는 waterfall
  * 아키텍쳐개발이 끝나고 구현하는 애를 고용해라
  * 소프트웨어를 만들지 말아라(?) : 살수 있으면 외주맡기든, 사라
    * 요즘말로 재구성? : 오픈소스 찾아라


# 마지막
* Agile 하게 개발
1. 문제 정의 -> 디자인적 사고, 진짜 문제 정의, 발명 원리, 파레토 차트
2. 요구 사항 분석 -> 정량적, 정성적, 시장 분석 등
3. 풀이 방법 고민 -> 자료구조, 알고리즘, 오픈소스, 각종 지식
4. 구현 -> 코드 컨벤션, 프레임워크 사용법, TDD
5. 피드백 -> 반영
6. 관리 -> Git
7. 협업 -> Github, slack, notion, zoom

* 시장이 원하는 기술에 대해 꾸준히 공부
* 문제의 해결 방법에 대한 생각