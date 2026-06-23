# MAPLE-LEDGER 작업 인수인계 문서 v49

- 작성 시각: 2026-06-24 01:43 KST
- 최신 HTML: v49
- 최신 Apps Script: v16 권장
- 배포 확인 URL: https://hossea123456789-design.github.io/MAPLE-LEDGER/?v=49

## v49 변경 요약

1. OCR 파서 개선
   - `1071억`을 `107억`으로 오인식하는 문제 수정
   - 1000억 이상 억 단위를 정상값으로 유지
   - 기존 테스트 케이스와 신규 1071억 테스트 통과

2. OCR 기록 방식 확장
   - 기본값은 `잔액 보정 자동`
   - 사용자가 `수입` 또는 `지출`을 직접 선택 가능
   - 선택한 타입별 카테고리 선택 가능
   - OCR 기록용 코멘트 입력 가능

3. 메소 구매 삭제 UX 개선
   - 삭제 버튼 클릭 시 화면에서 즉시 제거
   - 삭제 중 중복 클릭 방지
   - 실패 시 기존 목록 복구
   - Apps Script v16의 `deleteMesoPurchase` action 필요

4. 제공 방식
   - 요청에 따라 직접 HTML 개별 배포보다 ZIP 중심 제공
   - ZIP 내부 `DEPLOY/index.html`을 GitHub 루트 `index.html`로 사용

## 적용 순서

1. ZIP 압축 해제
2. `DEPLOY/index.html`을 GitHub `MAPLE-LEDGER` 저장소 루트의 `index.html`로 덮어쓰기
3. `APPS_SCRIPT/apps-script-v16-meso-purchase-delete.gs`를 Apps Script에 전체 복사
4. Apps Script 저장 후 새 버전 배포
5. `?v=49`로 확인

## 검증 완료

- node --check 통과
- OCR 파서 테스트 통과
- 이벤트 대상 id 검사 통과
