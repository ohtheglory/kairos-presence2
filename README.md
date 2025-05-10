# kairos-presence2
// 앱/layout.tsx

기본 함수 RootLayout 내보내기({
 아이들.
}: {
 아이들: 반응하세요.리액트노드
}) {
 반품 (
 <html lang="en">
 <body className="bg-흰색 텍스트-검은색 글꼴-sans">
 {아이들}
 </body>
 </html>
 )
}


// lib/supabase.ts

'@supabase/supabase-js'에서 {createC라이언트} 가져오기;

const supabaseUrl = process.env.문자열로서 NEXT_Public_SUPabase_URL;
콘스탑베이스AnonKey = process.env.문자열로서 NEXT_Public_SUPABASE_ANON_KEY;

export const supabase = createCentral(supabaseUrl, supabase)아논키);


// 테일윈드.config.ts

'tailwindcss'에서 {구성} 유형 가져오기;

구성 구성: 구성 = {
 콘텐츠: ['/app/**/*.{js,ts,jsx,tsx}'],
 테마: {
 확장: {},
 },
 플러그인: [],
};

기본 구성 내보내기;


// 유틸리티/index.ts

내보내기 함수 형식Date(날짜: 문자열): 문자열 {
 const d = 새 날짜(날짜);
 d.LocaleDateString('ko-KR')으로 돌아가기, {
 연도: 'numeric',
 한 달: '길다',
 낮: 'numeric',
 });
}


// 패키지.제이슨

{
 "이름": "카이로스-presence",
 "버전": "1.0.0",
 "scripts": {
 "dev": "다음 개발자",
 "build": "다음 빌드",
 "시작": "다음 시작"
 },
 "의존성": {
 "@supabase/supabase-js": "^2.39.7",
 "다음": "14.1.3",
 "react": "18.2.0",
 "react 돔": "18.2.0"
 },
 "개발 종속성": {
 "tailwindcss": "^3.4.1",
 "autop 리픽서": "^10.4.15",
 "postcss": "^8.4.24",
 "타자기": "^5.3.3"
 }
}


// next.config.js

/** @type {import('next').NextConfig} */
const nextConfig = {
 reactStricMode: true,
 swcMinify: true,
};

module.exports = nextConfig;
