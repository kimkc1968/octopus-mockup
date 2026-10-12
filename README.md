# 옥토퍼스 운영콘솔 목업

바로고 **옥토퍼스(Octopus)** — 딜리버리 마스터용 운영콘솔 목업.

**[kimkc1968.github.io/octopus-mockup](https://kimkc1968.github.io/octopus-mockup/)**

## 저장소 구조

```text
index.html        운영콘솔 본체 — 단일 HTML (372KB)
logo/             배달대행사 로고 — barogo · moaline · dilver
store_logo/       브랜드 로고 — burgerking · mcdonalds · starbucks · oliveyoung · yogibaedal
bank_logo/        은행 로고 — shinhan
font/             PretendardVariable.woff2 + LICENSE.txt (OFL 1.1)
.nojekyll         Jekyll 빌드 비활성화
```

빌드 과정 없는 자체 완결형 단일 페이지입니다. HTML·CSS·JS가 `index.html` 한 파일에 들어 있고, 참조는 전부 상대경로라 저장소 루트든 하위 폴더든 그대로 동작합니다.

## 화면 구조

사이드바 메뉴로 전환하는 SPA입니다. 각 화면은 `<section id="v-{key}">` 하나에 대응하고, 해시 라우팅(`#orders`)으로 직접 접근할 수 있습니다.

| 그룹 | 화면 | key |
| --- | --- | --- |
| 운영 | 대시보드 | `dashboard` |
| | 책임 권역 | `zone` |
| | 주문 현황 · 라이더 관제 | `orders` |
| 정산·수익 | 수익 | `revenue` |
| | 구상권 | `recourse` |
| | 정산 (세금계산서) | `settlement` |
| | 출금 | `settle` |
| 분석 | 완료 주문 | `completed` |
| | 통계 | `stats` |
| 관리 | 상점 등록 | `register` |
| | 담당 상점 · 오픈 | `shops` |
| | 서브계정 | `subaccount` |

화면별 CSS는 `#v-{key}` 로 스코프되어 서로 간섭하지 않습니다.

## 개발 명세 오버레이

우하단 **「개발 명세 보기」** 버튼으로 켭니다. 화면 위에 고정 레이어가 깔리고 기능 영역마다 번호 핀이 붙습니다. 핀을 누르면 해당 기능의 명세가 패널로 열립니다.

- 화면을 조작해 DOM이 바뀌면 핀 위치도 따라갑니다
- 패널 탭 — **화면 명세** / **공통 규칙** / **확인 필요**(미결정 항목)

## 외부 의존성

카카오맵 JavaScript SDK **하나**뿐입니다. 폰트·이미지·스크립트는 전부 저장소 안에 있습니다.

`orders`·`zone` 두 화면이 지도를 씁니다. JavaScript 키는 도메인 화이트리스트로 동작하므로 [Kakao Developers](https://developers.kakao.com) → 앱 설정 → 플랫폼 → Web → **사이트 도메인**에 아래가 등록되어 있어야 지도가 뜹니다.

```text
https://kimkc1968.github.io
```

## 배포

GitHub Pages — `main` / `(root)`. `index.html` 을 교체하고 push 하면 반영됩니다.

## 데이터

전부 더미이며 기준일은 **2026-10-07(수)** 로 고정되어 있습니다. 서버가 없어 발행·출금 등의 동작은 메모리 상태만 바꾸고 새로고침하면 초기화됩니다.
