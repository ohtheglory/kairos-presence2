<!-- kairos-app.zip 폴더 구조 복사본 (압축 해제 형태) --><!-- 1. app/page.tsx --><!-- Create file: app/page.tsx -->'use client'; import { useEffect } from 'react'; export default function Home() { useEffect(() => { console.log('Welcome to Kairos Presence'); }, []); return ( <main className="flex h-screen items-center justify-center bg-white"> <h1 className="text-3xl font-bold">Kairos Presence</h1> </main> ); }

<!-- 2. app/layout.tsx --><!-- Create file: app/layout.tsx -->import './globals.css'; export const metadata = { title: 'Kairos Presence', description: 'A spiritual rhythm sensing app', }; export default function RootLayout({ children }: { children: React.ReactNode }) { return ( <html lang="en"> <body>{children}</body> </html> ); }

<!-- 3. lib/supabase.ts --><!-- Create file: lib/supabase.ts -->import { createClient } from '@supabase/supabase-js'; const supabaseUrl = process.env.NEXT_PUBLIC_SUPABASE_URL!; const supabaseAnonKey = process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!; export const supabase = createClient(supabaseUrl, supabaseAnonKey);

<!-- 4. tailwind.config.ts --><!-- Create file: tailwind.config.ts -->import type { Config } from 'tailwindcss'; const config: Config = { content: ['./app/**/*.{js,ts,jsx,tsx}'], theme: { extend: {} }, plugins: [], }; export default config;

<!-- 5. utils/index.ts --><!-- Create file: utils/index.ts -->export function formatTime(date: Date) { return date.toISOString(); }

<!-- 6. package.json --><!-- Create file: package.json -->{ "name": "kairos-app", "version": "1.0.0", "scripts": { "dev": "next dev", "build": "next build", "start": "next start" }, "dependencies": { "@supabase/supabase-js": "^2.0.0", "next": "14.0.0", "react": "18.2.0", "react-dom": "18.2.0", "tailwindcss": "^3.0.0" }, "devDependencies": { "autoprefixer": "^10.4.0", "postcss": "^8.4.0", "typescript": "^5.0.0" } }

<!-- 7. next.config.js --><!-- Create file: next.config.js -->/** @type {import('next').NextConfig} */ const nextConfig = {}; module.exports = nextConfig;

