# 🚀 Tutorial Website Gratis di Vercel

> **Panduan lengkap — deploy website statis GRATIS ke Vercel dalam 3 metode**

![Proses deploy ke Vercel — GIF animasi](https://raw.githubusercontent.com/Celebez/tutorial-vercel-gratis/main/assets/deploy-demo.gif)

---

## 📋 Daftar Isi

- [Apa itu Vercel?](#apa-itu-vercel)
- [Prasyarat — apa yang harus disiapkan](#prasyarat--apa-yang-harus-disiapkan)
- [Langkah 1: Buat Akun Vercel](#langkah-1-buat-akun-vercel)
- [Metode Deploy](#metode-deploy)
  - [Metode 1: Via Hermes Agent (Terminal)](#metode-1-deploy-via-hermes-agent-terminal)
  - [Metode 2: Via GitHub](#metode-2-deploy-via-github)
  - [Metode 3: Langsung via Vercel CLI](#metode-3-deploy-langsung-via-vercel-cli)
- [Contoh Project](#contoh-project)
- [Cara Install Vercel CLI](#cara-install-vercel-cli)
- [Tips & Trik](#tips--trik)
- [FAQ](#faq)

---

## Apa itu Vercel?

**Vercel** adalah platform cloud buat:

- 🏗 **Deploy website statis** — HTML, CSS, JS, gambar
- ⚡ **Serverless functions** — API backend tanpa kelola server
- 🌐 **Global CDN** — 200+ edge nodes di seluruh dunia
- 🔗 **Auto HTTPS** — gratis, built-in

| Fitur | Detail |
|-------|--------|
| Harga | **Gratis** — 100GB bandwidth/bln |
| Build | 6000 menit build/bulan |
| Domain | `*.vercel.app` + custom domain |
| Storage | 1GB (statis) |
| Team | Bisa kolaborasi unlimited |

---

## Prasyarat — apa yang harus disiapkan

| No | Item | Cara dapetin |
|----|------|------------|
| 1 | ✅ **Akun Vercel** | Daftar di [vercel.com](https://vercel.com) — pake email atau GitHub |
| 2 | ✅ **Node.js** | `sudo apt install nodejs` atau [nodejs.org](https://nodejs.org) |
| 3 | ⬜ **Git** | Opsional — cuma perlu kalau mau metode GitHub |
| 4 | ⬜ **Hermes Agent** | Opsional — punya akses terminal aja udah cukup |

> **Minimal:** cukup punya laptop/HP + akun Vercel (email). Nggak perlu bayar.

---

## Langkah 1: Buat Akun Vercel

1. Buka [vercel.com](https://vercel.com)
2. Klik **Sign Up**
3. Pilih:
   - **Continue with GitHub** — paling cepet
   - **Continue with Email** — pake email biasa
4. Verifikasi email
5. Selesai — dashboard kosong siap deploy

> ⚠️ **Tips:** Pake GitHub lebih enak karena langsung connect — pas import repo tinggal pilih.

---

## Metode Deploy

Ada **3 metode**. Pilih yang paling cocok:

### Metode 1: Deploy via Hermes Agent (Terminal)

> **Langsung dari terminal** — nggak perlu buka browser Vercel.

```bash
# 1. Install Vercel CLI
npm install -g vercel

# 2. Login
vercel login
# → Buka link di browser → Authorize

# 3. Masuk ke folder project
cd ~/my-project

# 4. Deploy
vercel --prod
```

Output:
```
🔗 Linked to vercel.com/user/my-project
✅ Production: https://my-project.vercel.app
```

**Keuntungan:**
- Cepet — 5 detik
- Bisa dari SSH/VPS
- Integrasi sama Hermes Agent

**Cocok buat:** Developer yang suka pake terminal langsung.

---

### Metode 2: Deploy via GitHub

> **Push ke GitHub → auto deploy.** Ini metode paling populer.

**Step 1 — Buat repo lokal:**

```bash
mkdir website-ku
cd website-ku
git init
echo "<h1>Halo Dunia</h1>" > index.html
```

**Step 2 — Push ke GitHub:**

```bash
git add .
git commit -m "first deploy"
git remote add origin https://github.com/username/repo.git
git push -u origin main
```

**Step 3 — Import di Vercel:**

1. Buka [vercel.com/new](https://vercel.com/new)
2. Pilih tab **Import Git Repository**
3. Pilih repo → **Deploy**

**Step 4 — Selesai:**

```
✅ Production: https://repo-name.vercel.app
```

Setiap kali push `git push`, Vercel build ulang otomatis.

---

### Metode 3: Deploy Langsung via Vercel CLI

> **Upload folder lokal** — tanpa GitHub, tanpa commit.

```bash
npm install -g vercel
vercel login
vercel --prod
```

Vercel akan:
1. Deteksi framework
2. Upload file
3. Build
4. Deploy ke CDN

```bash
# Contoh interactive
vercel
? Set up and deploy "./project"? [Y/n] Y
? What's your project's name? belajar-vercel
? Deploy to production? Yes
✅ https://belajar-vercel.vercel.app
```

---

## Contoh Project

### `index.html` — landing page sederhana

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>Vercel Gratis</title>
</head>
<body>
    <h1>🚀 Website Gratis di Vercel</h1>
    <p>Deploy dalam 5 detik — tanpa bayar</p>
</body>
</html>
```

### `vercel.json` — config routing (SPA)

```json
{
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```

### `api/hello.js` — serverless function

```js
export default function handler(req, res) {
  res.json({ message: "Serverless jalan!" });
}
```

---

## Cara Install Vercel CLI

```bash
# Via npm (recommended)
npm install -g vercel

# Via yarn
yarn global add vercel

# Via pnpm
pnpm add -g vercel

# Via brew (macOS)
brew install vercel-cli
```

Cek versi:

```bash
vercel --version
# → v28.16.0
```

---

## Tips & Trik

| # | Tips | Command |
|---|------|---------|
| 1 | **Custom domain gratis** | `vercel domains add domainkamu.com` → A record `76.76.21.21` |
| 2 | **Env variables** | `vercel env add SECRET_KEY` — production / preview |
| 3 | **Preview build** | `vercel` (tanpa `--prod`) — URL preview sementara |
| 4 | **Auto detect framework** | Vercel detect otomatis — Next, Nuxt, Svelte, dll |
| 5 | **Analytics** | Bisa aktif dari dashboard — gratis tier |
| 6 | **Rollback** | Dashboard → Deployments → pilih versi lama |

---

## FAQ

**Q: Vercel beneran gratis?**
A: Iya. 100GB bandwidth + 6000 build menit/bulan. Cukup buat project kecil-sedang.

**Q: Bisa pake framework apa?**
A: Next.js, Nuxt, Svelte, Astro, Gatsby, atau HTML/CSS/JS polos.

**Q: Butuh kartu kredit?**
A: Nggak. Pake GitHub atau email biasa.

**Q: Domain `.vercel.app` bisa custom?**
A: Bisa — tambahin di dashboard dan set DNS.

**Q: Kalau lewat batas gratis?**
A: Naik ke Pro ($20/bln) atau tetap di free — upgrade kapan aja.

---

## 🔗 Link Penting

- [Vercel Dashboard](https://vercel.com/dashboard)
- [Vercel Docs](https://vercel.com/docs)
- [Vercel CLI Reference](https://vercel.com/docs/cli)
- [GitHub Integration](https://vercel.com/docs/git)

---

**Buat oleh [Celebez](https://github.com/Celebez)**