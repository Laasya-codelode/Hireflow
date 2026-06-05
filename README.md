# Hireflow — AI Job Search Assistant MVP

Resume analysis, ATS scoring, and cover letter generation 

## Setup

### 1. Install dependencies
```bash
npm install
```

### 2. Add your API key
```bash
cp .env.example .env.local
# Edit .env.local and add your Anthropic API key
# Get one at https://console.anthropic.com
```

### 3. Run dev server
```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

---

## Project structure

```
src/
  pages/
    index.tsx          — Landing page
    app.tsx            — Main app (resume input + results)
    api/
      analyze.ts       — Claude API: ATS score + rewrite + cover letter
      parse-pdf.ts     — PDF text extraction
  components/
    ScoreRing.tsx      — Animated ATS score circle
    ResultTabs.tsx     — Tabs: rewritten resume / cover letter / tips
  styles/
    globals.css        — Tailwind + custom fonts/animations
```

## How it works

1. User uploads/pastes resume + job URL or description
2. `/api/parse-pdf` extracts text from PDF uploads
3. `/api/analyze` sends both to Claude with a structured prompt
4. Claude returns JSON: ATS score, missing keywords, rewritten resume, cover letter, tips
5. Frontend renders results in tabbed UI with copy buttons

## Extending the MVP

- **Auth**: Add NextAuth.js for user accounts + usage limits
- **Job matching**: Integrate Adzuna or JSearch API to surface matching jobs
- **Interview prep**: Add a chat interface for mock interview Q&A
- **Payments**: Add Stripe for Pro tier ($19/mo)
- **History**: Store past analyses in PostgreSQL (Supabase or Railway)

## Deployment

Deploy to Vercel in one command:
```bash
npx vercel
```
Add `ANTHROPIC_API_KEY` to your Vercel environment variables.
