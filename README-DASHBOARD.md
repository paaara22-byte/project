# Smart Flood Control — Petropavl Akimat Dashboard

## Run the API server (port 3001)

```bash
npm install
npm start
```

## Run the dashboard (development, with hot reload)

In one terminal:

```bash
npm start
```

In another:

```bash
npm run dev:dashboard
```

Open **http://localhost:5173**. The Vite dev server proxies `/api` to `http://localhost:3001`.

## Production (serve dashboard from Express)

```bash
npm run build:dashboard
npm start
```

Then open **http://localhost:3001**.

## Backend API (used by the dashboard)

| Route | Method | Description |
|-------|--------|-------------|
| `/api/sensors` | GET | List sensors (id, name, lat, lng) |
| `/api/water-levels` | GET | Latest water level per sensor |
| `/api/ai-recommendations` | GET | Recent AI advice (`?limit=20`) |
| `/api/alerts` | GET | Active alerts above threshold (`?threshold=750`) |
| `/api/flood-zones` | GET | Zones with lat, lng, level_cm for map |
| `/api/notify` | POST | Simulate Telegram alert (`body: { message? }`) |

## Sensors table

For map markers and flood zones, add optional `lat` and `lng` (numeric) columns to your `sensors` table in Supabase. If missing, the dashboard places markers around Petropavl automatically.

## Dark / light mode

Use the sun/moon toggle in the header. Preference is not persisted (page refresh resets to light).
