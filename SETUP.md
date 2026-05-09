# SIGNALIST - Setup Guide

## Quick Start

This project has been freshly cloned with all commit history removed. You can now make this your own and contribute as the sole contributor.

### Step 1: Configure Git (Optional but Recommended)

If you haven't already configured Git globally, set your name and email:

```bash
git config user.name "Your Name"
git config user.email "your.email@example.com"
```

To set this only for this project (local config):

```bash
git config --local user.name "Your Name"
git config --local user.email "your.email@example.com"
```

### Step 2: Environment Variables Setup

The project includes two environment files:

- **`.env.example`** - Reference file with all variables and descriptions
- **`.env`** - Your local configuration (ignored by Git)

#### Required Setup:

1. **MongoDB Atlas** (Database)
   - Go to https://www.mongodb.com/cloud/atlas
   - Create a free account and cluster
   - Get your connection string
   - Add it to `.env` as `MONGODB_URI`

2. **Finnhub API** (Stock Data)
   - Register at https://finnhub.io/register (free tier available)
   - Copy your API key
   - Add it to `.env` as `FINNHUB_API_KEY`

3. **Google Gemini** (AI Features)
   - Go to https://aistudio.google.com/apikey
   - Create a new API key
   - Add it to `.env` as `GEMINI_API_KEY`

4. **Gmail SMTP** (Email Notifications)
   - Use your Gmail account
   - Create an App Password: https://support.google.com/accounts/answer/185833
   - Add credentials to `.env`:
     - `NODEMAILER_EMAIL=your-gmail@gmail.com`
     - `NODEMAILER_PASSWORD=<app-password>`

5. **Better Auth Secret** (Authentication)
   - Generate a random secret:
     ```bash
     openssl rand -base64 32
     ```
   - Add it to `.env` as `BETTER_AUTH_SECRET`

6. **Inngest** (Optional - Background Jobs)
   - Sign up at https://www.inngest.com/ for free
   - Get your event key and signing key
   - Add to `.env` if you want to use Inngest for scheduled tasks

### Step 3: Install Dependencies

```bash
npm install
```

### Step 4: Run Development Server

```bash
npm run dev
```

Open http://localhost:3000 in your browser.

### Step 5: Run Inngest (Optional - for email jobs)

In a separate terminal:

```bash
npx inngest-cli@latest dev
```

This enables scheduled email notifications and AI-powered daily summaries.

---

## Project Structure

- **`/app`** - Next.js 15 App Router with authentication and protected routes
- **`/components`** - Reusable React components (UI, forms, widgets)
- **`/database`** - MongoDB/Mongoose schemas and connection
- **`/lib/actions`** - Server actions for API calls and database operations
- **`/lib/inngest`** - Background job definitions (email, cron tasks)
- **`/lib/better-auth`** - Authentication configuration
- **`/public`** - Static assets, icons, images

---

## Key Features

✅ Real-time stock market dashboard with TradingView widgets  
✅ Stock search with Finnhub integration  
✅ Personalized watchlist with live price updates  
✅ Email/password authentication  
✅ AI-powered daily market summaries via Google Gemini  
✅ Automated email notifications with Nodemailer  
✅ Dark-themed UI with Tailwind CSS  
✅ Type-safe with TypeScript  

---

## Available Scripts

```bash
npm run dev      # Start development server with Turbopack
npm run build    # Build for production
npm start        # Start production server
npm run lint     # Run ESLint
```

---

## Troubleshooting

**Port 3000 already in use?**
```bash
npm run dev -- -p 3001
```

**MongoDB connection error?**
- Verify your connection string in `.env`
- Check MongoDB Atlas IP whitelist includes your machine
- Ensure your username/password are correct

**Finnhub API not working?**
- Verify your API key is active
- Check rate limits: https://finnhub.io/docs/api/rate-limits

**Email not sending?**
- Confirm Gmail App Password (not regular password)
- Check your Gmail account allows less secure app access
- Verify `NODEMAILER_EMAIL` matches Gmail account

---

## Next Steps

1. Update `.env` with your API keys and credentials
2. Run `npm install`
3. Start development with `npm run dev`
4. Begin building features!

---

## Tech Stack

- **Frontend**: Next.js 15, React 19, TypeScript, Tailwind CSS
- **Backend**: Next.js Server Components, Server Actions
- **Database**: MongoDB Atlas + Mongoose
- **APIs**: Finnhub (stocks), Google Gemini (AI), TradingView (charts)
- **Auth**: Better Auth (email/password)
- **Email**: Nodemailer (Gmail SMTP)
- **Background Jobs**: Inngest
- **Deployment**: Vercel-ready

---

**Ready to contribute?** Just commit your changes and push to your own GitHub repository!
