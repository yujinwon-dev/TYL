[toc]

# Sectioning Elements

- 종류

  - section
  - article
  - nav
  - aside

- 지켜야 할 룰

  - 어떤 섹션을 나누려면, 그 단원의 주제가 필요함

    -> Sectioning element 내에는 **반드시 heading 태그를 작성**해야 함(눈에 안 보일지라도)
    
    -> 꼭 가장 바깥 맨 위에 heading 태그를 작성해야 하는 건 아님. 위치는 중요하지 않음

---

- header
  - 문서/sectioning element의 도입부를 나타낼 때는 header 사용
- nav
  - 문서 간에 이동할 수 있는 요소/메뉴를 포함하는 경우에 사용
- main
  - **하나의 html 문서에서 단 한 개의 main**만 사용 가능
  - 본문 구조상 가장 핵심적인 컨텐츠를 묶어줄 때 사용
  - sectioning element 아니어서 heading 태그는 필수가 아님
- section
  - 가장 만만하게 사용할 수 있는 sectioning element
  - 논리적으로 완결성 있는 집합체에 대해 div와 같은 용도로 사용 가능
- article
  - 뉴스 기사, 블로그, 피드처럼 정보 컨텐츠로서 논리적으로 완결성 있는 경우. 독립적으로 존재해도 정보로서 의미가 있는 경우

- footer
  - 하단부를 나타낼 때. 그 뉘앙스를 더 살리고자 할 때 사용

- aside
  - section으로도 가능하지만, article처럼 의미를 살려주기 위함
  - 본문 내용과 직접적으로 연관이 없는 분리된 내용을 마크업할 때 사용
  - 사이드바 혹은 배너/위젯 광고 마크업 시 사용

---

- 마크업 과정

1. 논리적 집합에 따라 구획 나누기
2. 적합한 sectioning element 선택
3. 각각의 섹션 마크업
