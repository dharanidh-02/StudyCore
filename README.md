# StudyCore V2

StudyCore is an AI-powered study companion that turns course PDFs into topic summaries, practice questions, YouTube resources, and interactive PhET simulations.

## Features

- PDF uploads up to 50 MB
- Gemini-powered topic extraction and question generation
- MCQ and short-answer practice
- YouTube video recommendations
- Keyword-matched PhET simulations
- Voice Q&A, study history, and daily challenges
- Dark and light themes
- Automatic fallback generation when Gemini is unavailable

## Stack

- React 18 and TypeScript
- Vite
- Wouter
- TanStack Query
- Tailwind CSS and Radix UI
- Express and Node.js
- Google Gemini
- Multer and `pdf-parse`
- Drizzle ORM and PostgreSQL

## Project structure

```text
client/src/
  components/  UI, PDF, video, voice, and layout components
  hooks/       React hooks
  lib/         API and utility helpers
  pages/       Dashboard, topics, history, simulations, challenge

server/
  index.ts     Express server entry point
  routes.ts    REST API and PDF/AI processing
  storage.ts   In-memory storage implementation
  vite.ts      Development and production frontend serving

shared/
  schema.ts    Database and shared TypeScript schemas
```

## Requirements

- Node.js 20+
- npm
- Google Gemini API key
- YouTube Data API key for video search
- PostgreSQL only if persistent storage is implemented

## Local setup

```bash
git clone https://github.com/dharanidh-02/StudyCore.git
cd StudyCore
npm install
```

Configure environment variables:

```bash
export GEMINI_API_KEY="your-gemini-api-key"
export YOUTUBE_API_KEY="your-youtube-api-key"
```

Start the application:

```bash
npm run dev
```

Open `http://localhost:5000`. The server defaults to port `5000`; set `PORT` to override it.

## Commands

```bash
npm run dev       # Start development server
npm run check     # Run TypeScript checks
npm run build     # Build client and server
npm run start     # Start production build
npm run db:push   # Push the Drizzle schema to PostgreSQL
```

Database commands require:

```bash
export DATABASE_URL="postgresql://user:password@host/database"
```

## Important implementation note

PostgreSQL tables are defined in `shared/schema.ts`, and Drizzle is configured in `drizzle.config.ts`. However, the current runtime uses `server/storage.ts`'s `MemStorage`, so uploaded documents and generated study data are held in memory and lost when the server restarts.

## License

MIT, as declared in `package.json`.
