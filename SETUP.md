# Setup Guide - Dompet Keluarga

Panduan lengkap untuk setup aplikasi Dompet Keluarga dari awal.

## Prerequisites

1. Node.js v16 atau lebih tinggi
2. npm atau yarn
3. Akun Google
4. Akun Firebase (gratis)

## Step-by-Step Setup

### 1. Clone Repository

```bash
git clone https://github.com/yourusername/dompet-keluarga-pub.git
cd dompet-keluarga-pub
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Setup Firebase Project

1. Pergi ke [Firebase Console](https://console.firebase.google.com/)
2. Klik "Add project" atau "Create a project"
3. Masukkan nama project (contoh: `dompet-keluarga-prod`)
4. Aktifkan Google Analytics (opsional)
5. Tunggu project selesai dibuat

### 4. Enable Firebase Authentication

1. Di Firebase Console, buka menu **Authentication**
2. Klik tab **Sign-in method**
3. Enable **Google** sign-in provider
4. Tambahkan email support jika diperlukan
5. Save

### 5. Setup Firestore Database

1. Di Firebase Console, buka menu **Firestore Database**
2. Klik **Create database**
3. Pilih **Start in production mode** (rules akan di-update nanti)
4. Pilih location: **asia-southeast2 (Jakarta)** atau terdekat
5. Tunggu database selesai dibuat

### 6. Deploy Firestore Rules

1. Install Firebase CLI jika belum:
```bash
npm install -g firebase-tools
```

2. Login ke Firebase:
```bash
firebase login
```

3. Setup Firebase project configuration:
```bash
cp .firebaserc.example .firebaserc
```
   - Edit `.firebaserc` dan ganti `your-firebase-project-id` dengan project ID Anda

4. Initialize Firebase di project (opsional jika sudah ada .firebaserc):
```bash
firebase init
```
   - Pilih **Firestore** dan **Hosting**
   - Pilih existing project yang sudah dibuat
   - Accept default files (firestore.rules, firestore.indexes.json)
   - Set public directory ke `dist`
   - Configure as single-page app: **Yes**

4. Deploy Firestore rules:
```bash
firebase deploy --only firestore:rules
```

### 7. Setup Environment Variables

1. Copy template environment file:
```bash
cp .env.example .env
```

2. Dapatkan Firebase Config:
   - Di Firebase Console, buka **Project Settings** (gear icon)
   - Scroll ke bagian **Your apps**
   - Klik icon **</>** (Web)
   - Register app dengan nickname (contoh: "Dompet Keluarga Web")
   - Copy configuration values

3. Edit file `.env` dan isi dengan nilai dari Firebase:
```env
VITE_FIREBASE_API_KEY=AIzaSy...
VITE_FIREBASE_AUTH_DOMAIN=your-project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your-project-id
VITE_FIREBASE_STORAGE_BUCKET=your-project.firebasestorage.app
VITE_FIREBASE_MESSAGING_SENDER_ID=123456789
VITE_FIREBASE_APP_ID=1:123456789:web:abc123
VITE_FIREBASE_MEASUREMENT_ID=G-ABC123XYZ
VITE_APP_ID=your-project-id
```

**PENTING**: 
- File `.env` tidak akan ter-commit ke git (sudah ada di `.gitignore`)
- Jangan pernah share file `.env` di public

### 8. Run Development Server

```bash
npm run dev
```

Aplikasi akan berjalan di `http://localhost:5173`

### 9. Test Application

1. Buka browser dan akses `http://localhost:5173`
2. Klik tombol **Login dengan Google**
3. Login dengan akun Google Anda
4. Coba buat transaksi atau dompet baru
5. Verifikasi data tersimpan di Firestore Console

### 10. Build untuk Production

```bash
npm run build
```

Build output akan ada di folder `dist/`

### 11. Deploy ke Firebase Hosting (Opsional)

```bash
firebase deploy
```

Aplikasi akan live di `https://your-project.firebaseapp.com`

## Troubleshooting

### Error: "Firebase config is not defined"
- Pastikan file `.env` sudah dibuat dan diisi dengan benar
- Restart development server setelah mengubah `.env`

### Error: "Permission denied" saat akses Firestore
- Pastikan Firestore rules sudah di-deploy
- Verifikasi user sudah login
- Check Firebase Console > Firestore > Rules

### Error: "Auth domain not authorized"
- Di Firebase Console > Authentication > Settings
- Tambahkan domain yang digunakan ke "Authorized domains"
- Untuk development: `localhost`
- Untuk production: domain Anda

### Error saat build
- Clear cache: `rm -rf node_modules dist`
- Install ulang: `npm install`
- Build ulang: `npm run build`

## Development Tips

1. **Hot Reload**: Vite mendukung fast refresh, perubahan langsung terlihat
2. **Console Logs**: Check browser console untuk debugging
3. **Firestore Console**: Monitor data real-time di Firebase Console
4. **Network Tab**: Check network requests untuk troubleshooting API

## Production Checklist

Sebelum deploy ke production:

- [ ] Environment variables sudah diset dengan benar
- [ ] Firestore rules sudah di-deploy dan tested
- [ ] Firebase Authentication sudah di-configure
- [ ] Authorized domains sudah ditambahkan
- [ ] Build berhasil tanpa error: `npm run build`
- [ ] Test aplikasi di production build: `npm run preview`
- [ ] Firebase project sudah menggunakan Blaze plan (jika perlu)
- [ ] Setup Firebase App Check untuk security (recommended)
- [ ] Enable error monitoring (Firebase Crashlytics)

## Security Best Practices

1. **Environment Variables**: Jangan commit `.env` ke repository
2. **Firestore Rules**: Test rules dengan Firebase Rules Simulator
3. **API Keys**: Restrict API keys di Google Cloud Console
4. **HTTPS**: Selalu gunakan HTTPS di production
5. **App Check**: Enable Firebase App Check untuk produksi
6. **Backup**: Setup automatic Firestore backup

## Support

Jika menemui masalah:
1. Check [Issues](https://github.com/yourusername/dompet-keluarga-pub/issues) di GitHub
2. Buat issue baru dengan detail error
3. Sertakan browser & OS yang digunakan

---

Happy coding! 💚
