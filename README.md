# TripAI — 회원가입 API·화면 연동과 문화행사 정렬 개선

**송석주 · songsj27 | 개인 기여 포트폴리오**

React · Vite · Spring Boot · MyBatis · MariaDB

## 프로젝트 소개

서울 문화행사를 먼저 선택하고, 행사 시간에 맞춰 음식점·카페를 배치하는 팀 프로젝트입니다. 팀 서비스는 규칙 기반 일정 생성, AI 결과 검증, 지도 표시와 일정 편집을 제공합니다.

- [팀 원본 코드와 실행 방법](https://github.com/jnnxeo/MINI_PROJECT_1_Local_Culture_Tour_Guide)
- [제가 작성한 PR](https://github.com/jnnxeo/MINI_PROJECT_1_Local_Culture_Tour_Guide/pulls?q=is%3Apr+author%3Asongsj27)

## 개인 기여

| 작업 | 구현 내용 | 증빙 |
| --- | --- | --- |
| 회원가입 화면 | 이메일·비밀번호·약관 검증, 항목별 오류 표시, 요청 중 중복 제출 방지 | [PR #12](https://github.com/jnnxeo/MINI_PROJECT_1_Local_Culture_Tour_Guide/pull/12) |
| 회원가입 API·실제 연동 | 비밀번호 암호화 저장, 중복 이메일 409 처리, 프런트 Mock 제거 및 실제 API 연결 | [PR #35](https://github.com/jnnxeo/MINI_PROJECT_1_Local_Culture_Tour_Guide/pull/35) |
| 인증 화면 흐름 | 로그인·회원가입 공통 헤더, 화면 이동과 로그인 사진 표시 정리 | [PR #48](https://github.com/jnnxeo/MINI_PROJECT_1_Local_Culture_Tour_Guide/pull/48) |
| 월별 행사 정렬 | 선택 월에 시작하는 행사 우선 노출, 장기 행사 후순위 배치 및 관련 테스트 수정 | [PR #77](https://github.com/jnnxeo/MINI_PROJECT_1_Local_Culture_Tour_Guide/pull/77) |

## 문제와 해결

### Mock 화면을 실제 회원가입으로 연결

프런트와 백엔드의 성공 응답 필드가 다르면 가입이 성공해도 화면에서는 실패로 처리할 수 있습니다.

회원가입 API의 응답을 명세의 `data.memberId`로 통일하고, 프런트 Mock 분기를 제거했습니다. 실제 요청의 201 응답, DB 저장 결과와 중복 이메일의 409 응답을 함께 확인했습니다. 구현과 당시 검증 기록은 PR #35에 있습니다.

### 해당 월의 새 행사를 찾기 어려운 목록 개선

오래된 상설 행사가 먼저 표시되는 문제를 해결하기 위해 선택 월에 시작하는 행사를 우선 정렬했습니다. 기존 행사와 전체 조회 건수는 유지하면서 정렬 조건과 Mapper 테스트를 수정했습니다.

## 검증과 기여 범위

- PR #35: 실제 회원가입 201·중복 이메일 409·DB 저장 확인 기록
- PR #48: 프런트 빌드 및 로그인·회원가입 화면 이동 확인 기록
- PR #77: 월별 정렬 조건과 관련 테스트 변경

위 내용은 개발 당시 PR의 기록이며, 이 문서를 작성하면서 애플리케이션 테스트를 재실행한 결과는 아닙니다.

작성 PR은 5개이며 4개가 병합됐습니다. 초기 React·Vite 환경 구성 [PR #5](https://github.com/jnnxeo/MINI_PROJECT_1_Local_Culture_Tour_Guide/pull/5)는 미병합으로, 반영된 구현에 포함하지 않았습니다.

AI 일정 생성·지도·전체 서비스는 팀 결과이며, 개인 기여는 위 작업으로 구분합니다.

## 출처

이 저장소는 개인 기여 소개 문서입니다. 실제 코드·실행 방법·팀 문서는 원본 저장소를 참고해 주세요. 원저작자와 협업 기록은 원본 커밋·PR 링크로 유지합니다.
