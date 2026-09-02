# ADR INVITATION V5.1 — PRODUCTION FOUNDATION

Perbaikan dari ZIP V5.0: source 36 template, Supabase schema + RLS + Storage, RSVP/guest data model, public slug model, payment Edge Function Midtrans/Xendit, automated tests, Android foundation, dan release signing configuration berbasis secret.

## Penting
`package-lock.json` sengaja tidak dipalsukan. Lingkungan ini tidak dapat mengakses npm registry; jalankan `npm install` sekali di PC/CI yang online untuk menghasilkan lockfile resmi, lalu commit lockfile tersebut.

Keystore release dan payment secret tidak disertakan. Buat/pegang secara aman di luar repository dan masukkan melalui secrets/gradle.properties.

## Setup
1. `npm install`
2. `npm test`
3. `npm run build`
4. Isi `.env` dari `.env.example` dan jalankan `supabase/migrations/001_init.sql`.
5. Deploy `supabase/functions/create-payment` dan set `MIDTRANS_SERVER_KEY` / `XENDIT_SECRET_KEY`.
6. `npm run android:sync` lalu `npm run android:debug` atau `npm run android:release`.
