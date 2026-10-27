# KAOMI iAO 2027 Congress Guide

제34회 대한구강악안면임플란트학회 춘계국제종합학술대회 안내 웹앱.
2027년 3월 13–14일 · 한국과학기술회관 B1 ST Center.

## 구현 내용
- 행사 포스터와 10개 안내 메뉴
- 미확정 콘텐츠의 준비 중 표시
- 오시는 길 Google Maps 지도
- 관리자 메뉴 추가, 순서 변경, 공개 여부, 안내문 및 링크 편집
- Cloudflare D1 콘텐츠 저장 및 동시 수정 충돌 확인

## 실행
Node.js 22.13 이상이 필요합니다.

```sh
npm ci
npm run build
node --import ./scripts/sites-env.mjs ./node_modules/wrangler/bin/wrangler.js d1 execute DB --local --config dist/server/wrangler.json --persist-to .wrangler/state --file drizzle/0000_mean_dust.sql
npm run dev
```

관리자 이메일은 런타임 환경변수 ADMIN_EMAIL로 설정합니다. 로컬 개발에서는 git에서 제외된 .dev.vars에 ADMIN_EMAIL=seedy@sites.test 를 설정하고 로컬 로그인 경로를 사용합니다. 운영 환경은 Sites 인증 헤더와 D1 바인딩에 의존합니다. 다른 호스팅으로 이전할 경우 인증과 저장소 연결을 별도로 설정해야 합니다.

## 저장과 배포
이 저장소는 소스코드 보관용입니다. GitHub Pages만으로 관리자와 데이터베이스 기능이 실행되지는 않습니다. 비밀 환경설정, 로컬 데이터베이스, 설치된 의존성 및 빌드 결과는 커밋하지 않습니다.

초기 화면은 확인했으며 관리자 저장·권한에 대한 전체 검증 및 온라인 배포는 아직 완료되지 않았습니다.
