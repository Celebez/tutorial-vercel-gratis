# 🚀 Tutorial Website Gratis di Vercel

> **Cara deploy website statis / dinamis GRATIS di Vercel — 3 metode berbeda**

![Proses deploy ke Vercel — GIF animasi](https://raw.githubusercontent.com/Celebez/tutorial-vercel-gratis/main/assets/deploy-demo.gif)

---

## 📋 Daftar Isi

- [Apa itu Vercel?](#apa-itu-vercel)
- [Prasyarat](#prasyarat)
- [Cara Deploy](#cara-deploy)
  - [Metode 1: Via Hermes Agent (Terminal)](#metode-1-deploy-via-hermes-agent-terminal)
  - [Metode 2: Via GitHub](#metode-2-deploy-via-github)
  - [Metode 3: Langsung via Vercel CLI](#metode-3-deploy-langsung-via-vercel-cli)
- [Contoh Project](#contoh-project)
- [Tips & Trik](#tips--trik)

---

## Apa itu Vercel?

**Vercel** adalah platform cloud modern untuk deploy website statis, serverless functions, dan aplikasi frontend secara gratis.

| Fitur | Keterangan |
|-------|------------|
| 💰 Harga | **Gratis** — 100GB bandwidth/bulan |
| 🚀 Kecepatan | Global CDN (Edge Network) |
| 🌐 Domain | `*.vercel.app` gratis + custom domain |
| 🧩 Stack | Next.js, React, Vue, HTML/CSS/JS (statis) |
| ⚡ Serverless | Functions di `api/` folder |

> **Kenapa pilih Vercel?** Karena gratisan, cepet, support GitHub + CLI.

---

## Prasyarat

| No | Item | Keterangan |
|----|------|------------|
| 1 | Akun Vercel | Daftar di [vercel.com](https://vercel.com) — email atau GitHub |
| 2 | Node.js | Opsional — `node -v` untuk CLI |
| 3 | Git | Opsional — kalau mau via GitHub |
| 4 | Hermes Agent | Opsional — deploy langsung dari sini |

---

## Cara Deploy

Ada **3 metode** yang bisa dipake. Pilih sesuai nyaman:

### Metode 1: Deploy via Hermes Agent (Terminal)

> Deploy **langsung dari terminal** — nggak perlu buka browser.

**Step 1:** Login Vercel dari CLI

```bash
npm install -g vercel
vercel login
```

**Step 2:** Arahkan ke folder project

```bash
cd /path/to/your-project
```

**Step 3:** Deploy langsung

```bash
vercel --prod
```

**Step 4:** Selesai!

```
✅ Production — https://project-ku.vercel.app
```

---

### Metode 2: Deploy via GitHub

> Push ke GitHub → Vercel auto-build.

**Step 1:** Buat repo baru

```bash
mkdir my-awesome-site && cd my-awesome-site
git init
echo "<h1>Halo Dunia!</h1>" > index.html
```

**Step 2:** Push ke GitHub

```bash
git add . && git commit -m "first commit"
git remote add origin https://github.com/USER/REPO.git
git push -u origin main
```

**Step 3:** Import ke Vercel

1. Buka [vercel.com/new](https://vercel.com/new)
2. Pilih **Import Git Repository**
3. Cari repo kamu
4. Klik **Deploy**

**Step 4:** Selesai — setiap push ke `main` auto-deploy.

---

### Metode 3: Deploy Langsung via Vercel CLI

> Upload langsung — tanpa GitHub.

```bash
npm install -g vercel
vercel login
vercel        # interactive
vercel --prod # production
```

Output:
```
Vercel CLI 28.16.0
? Set up and deploy "./your-project"? [Y/n] Y
? Which scope do you want to deploy? user
? Link to existing project? No
? What's your project's name? my-awesome-site
  🔗  Linked to vercel.com/user/my-awesome-site
  🚀  Deployed to production (https://my-awesome-site.vercel.app) [1s]
```

---

## Contoh Project

### `index.html`

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>Website Gratis - Vercel</title>
</head>
<body>
    <h1>🚀 Website Gratis di Vercel</h1>
    <p>Deploy dalam 5 detik — tanpa bayar</p>
    <span>✅ Deployed via Vercel</span>
</body>
</html>
```

### `vercel.json`

```json
{
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```

---

## Tips & Trik

- **Custom Domain:** `vercel domains add yourdomain.com` → set A record ke `76.76.21.21`
- **Environment Variables:** `vercel env add VAR_NAME`
- **Serverless Functions:** file di `api/hello.js` — auto deploy

| Metode | Cocok buat |
|--------|-----------|
| Hermes Agent | Dev langsung |
| GitHub | Production / tim |
| CLI | Testing |

---

**Buat oleh [Celebez](https://github.com/Celebez)**