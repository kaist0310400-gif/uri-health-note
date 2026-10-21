# 우리집 건강노트

가족이 함께 걸음·수면·체중·운동·식단을 기록하고, 건강검진·병력·병원 진료기록을 바탕으로
맞춤 식단, 휴식·회복 점수, 내일 관리 코멘트를 받는 건강관리 웹앱입니다. (정책제도 3기 포트폴리오)

## 구성

| 파일 | 역할 |
|---|---|
| `index.html` | 화면 전체 (가족 한눈에, 오늘 기록, 운동·식단, 맞춤 식단, 건강검진, BMI·칼로리, 건강 정보) |
| `runtime.js` | 데이터 저장 계층. Supabase가 설정되면 Supabase에 저장하고 실시간으로 공유, 아니면 브라우저(localStorage)에 저장 |
| `config.js` | Supabase 주소와 공개(anon) 키 |
| `supabase.sql` | Supabase 테이블·보안 규칙(RLS)·예시 데이터 |
| `vercel.json` | Vercel 정적 배포 설정 |

## 데이터와 보안

- 아빠·엄마·딸 기록은 모두 가상의 예시이며 읽기 전용입니다. 날짜는 접속한 날에 맞춰 자동으로 옮겨집니다.
- 방문자마다 무작위 방문자 ID가 생기고, 그 방문자의 기록은 `members/v_…` 공간에만 쓸 수 있습니다.
- 로그인이 없는 공개 데모라 다른 방문자도 기록을 볼 수 있습니다. 실제 건강 정보는 넣지 마세요.

## 배포 순서

1. Supabase 프로젝트를 만들고 SQL Editor에서 `supabase.sql` 전체를 실행합니다.
2. Project Settings → API의 Project URL과 anon public 키를 `config.js`에 넣습니다. (service_role 키는 절대 넣지 마세요)
3. Vercel에서 이 저장소를 Import → Framework Preset: Other → Deploy.

`config.js`를 비워 두면 브라우저 저장 데모 모드로 동작합니다.
