# Weekly Review — 여행 관리 CRUD

## Deployment

Vercel 배포 URL: https://week05oss-fvpe.vercel.app/

## Key Learning

1. DOM으로 HTML 요소를 찾고 생성하여 화면을 변경하는 방법을 배웠습니다.
2. Event로 버튼 클릭과 Form 제출을 처리하고, Validation으로 잘못된 입력을 막았습니다.
3. Array로 데이터를 관리하고, 데이터 변경 후 `renderTrips()`로 화면을 갱신했습니다.

## CRUD Service

- 주제: 여행 관리
- Field: `id`(고유 번호), `title`(여행 이름), `destination`(여행지), `startDate`(출발일), `budget`(예산), `status`(상태)
- Create: 입력값 검증 후 `push()`로 여행을 추가합니다. ID는 `nextId`로 생성합니다.
- Read: `renderTrips()`에서 Array를 순회하여 표의 행과 셀을 생성합니다.
- Update: 수정 버튼으로 기존 값을 Form에 표시하고, 검증 후 `find()`로 찾은 객체의 값을 변경합니다.
- Delete: `confirm()`으로 확인한 뒤 `filter()`로 해당 여행을 Array에서 제외하고 화면을 갱신합니다.

Create와 Update 모두 여행 이름 2글자 이상, 여행지 필수, 출발일 필수, 예산이 숫자이고 0 이상인지 검증합니다.

## JavaScript

- `querySelector()`: 입력창, Form, 목록 요소를 찾습니다.
- `addEventListener()`: 클릭과 제출 이벤트에 실행할 함수를 등록합니다.
- `createElement()` / `appendChild()`: 목록과 표의 요소를 만들고 화면에 붙입니다.
- `split()` / `trim()`: DOM 실습에서 쉼표로 입력을 나누고 앞뒤 공백을 제거합니다.
- Array의 `push()`, `forEach()`, `find()`, `filter()`: 데이터 추가, 순회, 검색, 삭제에 사용합니다.
- `renderTrips()`: 현재 Array를 기준으로 표를 다시 만드는 함수입니다.

## AI / Search Usage

- Tool: OpenAI Codex
- Purpose: DOM, 콜백 함수, Array CRUD, Validation, CSS 적용과 오류 해결 방법을 질문했습니다.
- Used: 단계별 코드 예시를 참고해 적용했습니다. AI가 삭제 갱신 오류 수정, README 작성도 도왔으며, 기존 CSS 변경을 내용별 커밋으로 나누고 커밋 메시지를 수정했습니다.
- What I Learned: 문자열과 DOM 요소의 차이, 함수의 매개변수 범위, Array 변경 후 화면 갱신이 필요한 이유를 이해했습니다.

## Problem & Solution

- `<li>`에 `split()`을 사용해 오류가 발생했습니다. 문자열인 `input.value`를 나눈 뒤 항목마다 `<li>`를 생성하도록 변경했습니다.
- 수정 시 새 여행이 추가됐습니다. `editingId`로 추가와 수정 처리를 구분했습니다.
- `renderTrips()`가 자신을 반복 호출해 오류가 발생했습니다. 호출을 삭제 이벤트 안으로 옮겼습니다.
- 삭제 버튼에 빨간색이 적용되지 않았습니다. CSS와 연결되는 `delete-button` 클래스를 지정했습니다.

## Reflection

Array의 데이터 변경과 화면 변경은 별개이며, `renderTrips()`로 연결해야 한다는 점을 배웠습니다. 새로고침하면 초기 데이터로 돌아가는 이유가 메모리에만 저장하기 때문임을 이해했고, 이후에는 데이터를 유지하는 방법도 알아보고 싶습니다.
