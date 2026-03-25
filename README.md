# Harmonize

A music-based dating app that matches users based on their Spotify listening habits. Users sign in with Spotify, build a profile around their music taste, and swipe on potential matches the algorithm surfaces. When two people mutually like each other, they get a match notification and can connect.

## Features

- Sign in with Spotify OAuth
- Profile built around your actual listening history and top artists
- Swipe interface to browse potential matches
- Compatibility algorithm that scores users by music taste overlap
- Mutual match notifications
- Match management and history

## Tech Stack

| Layer | Tech |
|---|---|
| Framework | Next.js |
| Auth | NextAuth.js with Spotify OAuth |
| Database | PostgreSQL |
| Migrations | Knex.js |
| Containerization | Docker |
| Language | JavaScript |

## Getting Started

### Prerequisites

- Node.js 18+
- PostgreSQL
- A Spotify Developer app (free at developer.spotify.com)

### Spotify Setup

1. Go to the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Create a new app
3. Set the redirect URI to `http://localhost:3000/api/auth/callback/spotify`
4. Copy your Client ID and Client Secret

### Installation

```bash
# 1. Clone the repo
git clone https://github.com/MohammadAbbas393/Harmonize-Music-Based-Dating-App
cd Harmonize-Music-Based-Dating-App

# 2. Install dependencies
npm install

# 3. Set up environment variables
cp .env.example .env.local
```

Fill in your `.env.local`:

```env
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your_random_secret
SPOTIFY_CLIENT_ID=your_spotify_client_id
SPOTIFY_CLIENT_SECRET=your_spotify_client_secret
DATABASE_URL=postgres://postgres:postgres@localhost:5432/postgres
```

Generate a secret:

```bash
openssl rand -base64 32
```

### Database Setup

```bash
# Run migrations
npx knex migrate:latest

# Seed sample users
npx knex seed:run --specific=sample_user_data.js

# Seed sample swipes (run after users)
npx knex seed:run --specific=sample_swipes_data.js
```

### Running Locally

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Common Issues

- **OAuthCallback error** - make sure the redirect URI in your Spotify app exactly matches `http://localhost:3000/api/auth/callback/spotify`
- **Watchpack error** - clear the Next.js cache with `rm -rf .next` and restart
- **Foreign key errors on seed** - always run the users seed before the swipes seed

