# MAPLE-LEDGER GitHub Pages + Google Sheets 구조 문서 v49

- 작성 시각: 2026-06-24 01:43 KST
- HTML: v49
- Apps Script: v16 권장

## 구조 요약

```text
GitHub Pages index.html
→ Apps Script Web App
→ Google Sheets
→ JSON 응답
→ 브라우저 화면 갱신
```

## v49 API 변경

메소 구매 기록 삭제를 위해 Apps Script에 다음 action을 추가합니다.

```text
deleteMesoPurchase
```

요청 예시:

```text
?action=deleteMesoPurchase&id=<meso_purchase_id>
```

Apps Script는 `MesoPurchases` 시트에서 id가 일치하는 행을 삭제하고 다음 형태를 반환해야 합니다.

```json
{ "ok": true }
```

## v49 프론트 변경

OCR 기록은 더 이상 무조건 잔액 보정으로만 저장하지 않습니다.

```text
잔액 보정 자동
수입
지출
```

선택한 타입에 따라 카테고리와 코멘트를 지정한 뒤 `addRecord`로 저장합니다.

## 배포 구조

```text
DEPLOY/index.html → GitHub 저장소 루트 index.html
APPS_SCRIPT/apps-script-v16-meso-purchase-delete.gs → Apps Script 전체 교체
```
