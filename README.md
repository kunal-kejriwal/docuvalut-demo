# DocuVault Demo

A file manager UI built on top of [APIEngine](https://theapiengine.com) — demonstrating how to use the File Storage API to list, preview, and download files in a polished Next.js app.

![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js) ![APIEngine](https://img.shields.io/badge/Powered%20by-APIEngine-6d28d9) ![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-38bdf8?logo=tailwindcss) ![License](https://img.shields.io/badge/license-MIT-green)

---

## Features

- Browse all uploaded files with grid and list views
- Quick Access section showing the 4 most recently modified files
- Filter by type — Documents, Images, Videos, Audios
- Search files by name
- Sort by name, date modified, or size
- Open files inline in a new tab
- Force-download any file
- Live storage usage meter synced from your APIEngine plan
- Fully responsive layout

## Tech Stack

- [Next.js 14](https://nextjs.org) (App Router, Client Components)
- [Tailwind CSS](https://tailwindcss.com)
- [Framer Motion](https://www.framer.com/motion/) for animations
- [Font Awesome](https://fontawesome.com) for file-type icons
- [APIEngine](https://theapiengine.com) File Storage API as the backend

---

## Prerequisites

- An [APIEngine](https://theapiengine.com) account on the **Starter plan or higher** (File Storage is not available on the Free plan)
- An APIEngine API key — generate one from your dashboard under **API Keys**
- Node.js 18+

---

## Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/kunal-kejriwal/docuvalut-demo.git
cd docuvalut-demo
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

```bash
cp .env.local.example .env.local
```

Open `.env.local` and fill in your values:

```env
NEXT_PUBLIC_APIENGINE_BASE_URL=https://api.theapiengine.com
NEXT_PUBLIC_APIENGINE_API_KEY=your_api_key_here
```

### 4. Run locally

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) and click **View Files**.

---

## Deploying to Vercel

1. Import the repository at [vercel.com/new](https://vercel.com/new)
2. Under **Environment Variables**, add:
   - `NEXT_PUBLIC_APIENGINE_BASE_URL` → `https://api.theapiengine.com`
   - `NEXT_PUBLIC_APIENGINE_API_KEY` → your API key
3. Click **Deploy**

Vercel auto-detects Next.js — no build configuration needed.

---

## Project Structure

```
docuvault-demo/
├── app/
│   ├── page.tsx            # Landing page
│   └── files/
│       └── page.tsx        # Fetches file list from APIEngine, renders DocuVault
├── components/
│   └── docuvault.tsx       # Main UI component (sidebar, grid/list, open/download)
├── lib/
│   └── apiengine.ts        # Typed fetch wrapper (attaches X-API-Key header)
└── .env.local.example      # Environment variable template
```

## API Endpoints Used

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/v1/files/` | List all files + storage usage for the authenticated user |
| `GET` | `/api/v1/files/<id>/download/` | Stream or force-download a file |

Authentication uses the `X-API-Key` header on every request.

---

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `NEXT_PUBLIC_APIENGINE_BASE_URL` | Yes | Base URL of your APIEngine instance |
| `NEXT_PUBLIC_APIENGINE_API_KEY` | Yes | Your APIEngine API key |

> **Note:** Both variables are prefixed `NEXT_PUBLIC_` so they are available in the browser. Do not store sensitive backend secrets here.

---

## License

MIT
