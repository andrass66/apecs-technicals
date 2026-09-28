# APECS Technical Question Bank — GitHub Pages 세팅 가이드

## 폴더 구성
```
index.html            ← 사이트 (매주 안 건드림)
admin.html            ← 운영자 암호화 도구 (문제 내용 없음, 공개돼도 안전)
robots.txt            ← 검색엔진 차단
data/manifest.json    ← 주차 목록
data/week03.enc.json  ← 암호화된 문제 (지금은 샘플 11문항)
```

## 처음 한 번: 사이트 올리기 (약 10분)
1. github.com 가입 → 오른쪽 위 **+** → **New repository**
   - 이름: 예) `apecs-technicals` (이름이 URL에 들어감)
   - **Public** 선택 (무료 Pages 조건. 문제는 암호화돼 있어서 괜찮음)
   - **Create repository**
2. 새 저장소 화면에서 **uploading an existing file** 클릭
3. 이 zip을 푼 **안의 파일과 `data` 폴더를 통째로** 드래그 → **Commit changes**
   - `index.html`이 저장소 맨 위에 보여야 함 (폴더 안에 한 번 더 들어가 있으면 안 됨)
4. 저장소 **Settings → Pages**
   - Source: **Deploy from a branch** / Branch: **main**, 폴더 **/(root)** → **Save**
5. 1–2분 뒤 같은 화면 위쪽에 링크가 뜸: `https://<아이디>.github.io/apecs-technicals/`
6. 링크 열어서 비밀번호 입력 → 샘플 문제가 나오면 성공

## 매주: 새 주차 추가 (약 3분)
1. Claude Project에서 **/내보내기** → `weekNN.json` 다운로드 (평문. **GitHub에 올리지 말 것**)
2. 사이트 링크 뒤에 `/admin.html` 붙여서 열기
3. ① 파일 선택 → **Validate** (에러 0개 확인) → ② 비밀번호 두 번 → **Encrypt & download**
4. GitHub 저장소 → `data` 폴더 → **Add file → Upload files** → `weekNN.enc.json` 올리기
5. `data/manifest.json` 클릭 → 연필(✏️) → admin 화면 ③에 나온 줄을 목록에 추가 → **Commit**
   ```json
   {
     "weeks": [
       { "week": 3, "file": "week03.enc.json", "title": "..." },
       { "week": 4, "file": "week04.enc.json", "title": "..." }
     ]
   }
   ```
   (줄 사이 쉼표 주의. 마지막 줄 뒤에는 쉼표 없음)
6. 1–2분 뒤 반영. 동료들은 새로고침만 하면 됨

## 샘플 데이터 교체
Week 3 실제 문제를 만들면 같은 이름 `week03.enc.json`으로 덮어쓰면 됩니다 (manifest 수정 불필요).

## 비밀번호를 바꾸고 싶을 때
모든 주차가 같은 비밀번호여야 합니다. admin.html에서 **모든 `weekNN.json`을 한꺼번에 선택**해 새 비밀번호로 다시 암호화 → 전부 덮어쓰기.
동료들은 다음 접속 때 새 비밀번호를 한 번 입력하면 됩니다.

## 알아둘 점
- 진도는 **각자 기기 브라우저**에 저장됩니다 (폰과 노트북은 따로). 브라우저 데이터를 지우면 초기화.
- 비밀번호를 아는 사람은 누구나 볼 수 있습니다. 새면 위 방법으로 교체하세요.
- 평문 `weekNN.json`은 운영자 컴퓨터와 Claude Project에만 둡니다.
