# 🌍 TravelPath

> 여행 사진으로 시작하는 스마트한 여행 기록 관리

![TravelPath Banner](https://via.placeholder.com/1200x400/6366f1/ffffff?text=TravelPath+-+Smart+Travel+Memory+Management)

## 📋 프로젝트 소개

**TravelPath**는 스마트폰으로 촬영한 여행 사진의 메타데이터(EXIF)를 자동으로 분석하여 시간대별 여행 경로를 시각화하고, 추억을 아름답게 정리·공유할 수 있는 반응형 웹 애플리케이션입니다.

### ✨ 핵심 기능

- 📸 **스마트 사진 업로드**: 드래그앤드롭으로 간편한 다중 파일 업로드
- 🗺️ **자동 경로 생성**: GPS 좌표와 시간 데이터 기반 여행 동선 자동 시각화
- 📍 **인터랙티브 지도**: 클릭 가능한 마커와 실시간 사진 미리보기
- 🏛️ **장소 정보**: 자동 장소명 인식 및 식당·관광지 정보 제공
- 📄 **PDF 내보내기**: 아름다운 레이아웃의 여행 앨범 생성
- 📱 **완벽한 반응형**: 모바일 우선 설계로 어디서든 편리하게

## 🚀 빠른 시작

### 필수 요구사항

- Node.js 18.17.0 이상
- pnpm (권장 패키지 매니저)
- PostgreSQL 데이터베이스

### 설치 및 실행

```bash
# 저장소 클론
git clone https://github.com/your-username/travelpath.git
cd travelpath

# 의존성 설치
pnpm install

# 환경 변수 설정
cp .env.example .env.local
# .env.local 파일을 열어 필요한 값들을 설정하세요

# 데이터베이스 마이그레이션
npx prisma migrate dev
npx prisma generate

# 개발 서버 실행
pnpm dev
```

개발 서버가 실행되면 [http://localhost:3000](http://localhost:3000)에서 애플리케이션을 확인할 수 있습니다.

## 🛠️ 기술 스택

### Frontend
- **Next.js 15** - React 프레임워크 (App Router)
- **TypeScript** - 타입 안전성
- **TailwindCSS** - 유틸리티 기반 스타일링
- **ShadCN/UI** - 재사용 가능한 UI 컴포넌트
- **Zustand** - 상태 관리

### Backend
- **Next.js API Routes** - 서버리스 API
- **Prisma** - 데이터베이스 ORM
- **PostgreSQL** - 관계형 데이터베이스
- **NextAuth.js** - 인증 시스템

### 핵심 라이브러리
- **react-dropzone** - 파일 업로드
- **exif-js / piexifjs** - EXIF 메타데이터 추출
- **Kakao Maps API** - 지도 시각화
- **@react-pdf/renderer** - PDF 생성
- **sharp** - 서버사이드 이미지 처리

## 📐 프로젝트 구조

```
travelpath/
├── app/                      # Next.js App Router
│   ├── (auth)/              # 인증 관련 페이지
│   ├── dashboard/           # 대시보드
│   ├── trips/               # 여행 상세 페이지
│   ├── api/                 # API 엔드포인트
│   └── globals.css          # 글로벌 스타일
├── components/              # 재사용 가능한 컴포넌트
│   ├── ui/                  # ShadCN UI 컴포넌트
│   ├── maps/                # 지도 관련 컴포넌트
│   ├── photos/              # 사진 관련 컴포넌트
│   └── layout/              # 레이아웃 컴포넌트
├── lib/                     # 유틸리티 함수
│   ├── auth.ts              # 인증 설정
│   ├── db.ts                # 데이터베이스 설정
│   ├── exif.ts              # EXIF 처리
│   └── utils.ts             # 공통 유틸리티
├── prisma/                  # Prisma 스키마
├── public/                  # 정적 파일
├── types/                   # TypeScript 타입 정의
└── tests/                   # 테스트 파일
```

## 🌟 주요 특징

### 🤖 자동화된 여행 기록
- EXIF 데이터 자동 추출로 수동 입력 최소화
- 시간순 자동 정렬 및 경로 생성
- 지리적 클러스터링을 통한 스마트한 장소 그룹핑

### 🎨 직관적인 사용자 경험
- 드래그앤드롭 파일 업로드
- 인터랙티브 지도와 갤러리 연동
- 모바일 우선 반응형 디자인

### 📊 풍부한 시각화
- 여행 경로 라인 및 마커 표시
- 사진 썸네일 오버레이
- 시간대별/장소별 정보 표시

### 🔐 안전한 데이터 관리
- NextAuth.js 기반 인증 시스템
- 개인정보 보호 중심 설계
- 안전한 파일 저장 및 관리

## 📱 스크린샷

| 대시보드 | 여행 상세 |
|---------|----------|
| ![Dashboard](https://via.placeholder.com/400x300/6366f1/ffffff?text=Dashboard) | ![Trip Detail](https://via.placeholder.com/400x300/8b5cf6/ffffff?text=Trip+Detail) |

| 사진 업로드 | PDF 내보내기 |
|------------|-------------|
| ![Photo Upload](https://via.placeholder.com/400x300/06b6d4/ffffff?text=Photo+Upload) | ![PDF Export](https://via.placeholder.com/400x300/10b981/ffffff?text=PDF+Export) |

## 🔧 개발 가이드

### 환경 설정

```env
# .env.local
DATABASE_URL="postgresql://username:password@localhost:5432/travelpath"
NEXTAUTH_SECRET="your-nextauth-secret"
NEXTAUTH_URL="http://localhost:3000"
KAKAO_MAP_API_KEY="your-kakao-maps-api-key"
GOOGLE_PLACES_API_KEY="your-google-places-api-key"
VERCEL_BLOB_READ_WRITE_TOKEN="your-vercel-blob-token"
```

### 개발 명령어

```bash
# 개발 서버 실행
pnpm dev

# 빌드
pnpm build

# 테스트 실행
pnpm test

# 린팅
pnpm lint

# 타입 체크
pnpm type-check

# 데이터베이스 관리
npx prisma studio
npx prisma migrate dev
npx prisma db push
```

## 🧪 테스트

```bash
# 단위 테스트
pnpm test:unit

# 통합 테스트
pnpm test:integration

# E2E 테스트
pnpm test:e2e

# 커버리지 확인
pnpm test:coverage
```

## 🚀 배포

### Vercel 배포 (권장)

1. GitHub 저장소를 Vercel과 연결
2. 환경 변수 설정
3. 자동 배포 완료

```bash
# 로컬에서 빌드 테스트
pnpm build
pnpm start
```

### 기타 플랫폼

- **Netlify**: `netlify.toml` 설정 필요
- **AWS**: Amplify 또는 EC2 배포 가능
- **Docker**: `Dockerfile` 제공

## 📊 성능 지표

- ⚡ **페이지 로딩 속도**: < 3초
- 🖼️ **이미지 처리**: 50장 동시 업로드 지원
- 📱 **모바일 성능**: Lighthouse 90점 이상
- 🗺️ **지도 렌더링**: 부드러운 60fps

## 🗺️ 로드맵

### Phase 1 - MVP (현재)
- [x] 기본 사진 업로드 및 EXIF 추출
- [x] 지도 시각화 및 경로 생성
- [x] 기본 사용자 인터페이스
- [ ] PDF 내보내기 기능
- [ ] 사용자 인증 시스템

### Phase 2 - 향상된 기능
- [ ] AI 기반 사진 분류
- [ ] 소셜 공유 기능
- [ ] 오프라인 지원 (PWA)
- [ ] 다국어 지원

### Phase 3 - 고급 기능
- [ ] 실시간 여행 추적
- [ ] AR 기반 정보 표시
- [ ] 모바일 앱 (React Native)
- [ ] API 개방

## 🤝 기여하기

TravelPath 프로젝트에 기여해주셔서 감사합니다! 

### 기여 방법

1. 저장소를 포크합니다
2. 새로운 브랜치를 생성합니다 (`git checkout -b feature/amazing-feature`)
3. 변경사항을 커밋합니다 (`git commit -m 'Add amazing feature'`)
4. 브랜치에 푸시합니다 (`git push origin feature/amazing-feature`)
5. Pull Request를 생성합니다

### 개발 가이드라인

- 코드 스타일: ESLint + Prettier 설정을 따릅니다
- 커밋 메시지: [Conventional Commits](https://conventionalcommits.org/) 규칙을 사용합니다
- 테스트: 새로운 기능에는 반드시 테스트를 작성합니다
- 문서화: README 및 코드 주석을 업데이트합니다

## 📝 라이선스

이 프로젝트는 [MIT License](LICENSE)를 따릅니다.

## 👥 개발팀

- **메인 개발자**: [@your-username](https://github.com/your-username)
- **기여자들**: [Contributors](https://github.com/your-username/travelpath/contributors)

## 🙏 감사의 말

이 프로젝트는 다음 오픈소스 프로젝트들의 도움으로 만들어졌습니다:

- [Next.js](https://nextjs.org/) - React 프레임워크
- [Prisma](https://prisma.io/) - 데이터베이스 ORM
- [ShadCN/UI](https://ui.shadcn.com/) - UI 컴포넌트 라이브러리
- [TailwindCSS](https://tailwindcss.com/) - CSS 프레임워크
- [Kakao Maps](https://apis.map.kakao.com/) - 지도 서비스

## 📧 문의

프로젝트에 대한 질문이나 제안사항이 있으시면 언제든지 연락해주세요:

- 이메일: your-email@example.com
- 이슈: [GitHub Issues](https://github.com/your-username/travelpath/issues)
- 토론: [GitHub Discussions](https://github.com/your-username/travelpath/discussions)

---

<div align="center">
  <p>Made with ❤️ by TravelPath Team</p>
  <p>
    <a href="#top">⬆️ 맨 위로</a>
  </p>
</div> 