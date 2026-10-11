# UniConnect Deployment — ANURAG UNIVERSITY

Deployment configuration for the two other repositories:

| Repo | What | Hosted on |
|---|---|---|
| `uniconnect-frontend` | HTML/CSS/JS client | GitHub Pages (auto, via Actions) |
| `uniconnect-backend` | Java Spring Boot API | Render (Docker) |
| `uniconnect-deployment` (this) | `render.yaml`, `docker-compose.yml`, steps | — |

## Steps
1. **Backend** — edit `render.yaml` (replace `YOUR_GITHUB_USERNAME`), push this repo, then on
   [render.com](https://render.com): *New → Blueprint* → select this repo. Copy the service URL,
   e.g. `https://uniconnect-backend.onrender.com`.
2. **Frontend** — in `uniconnect-frontend`: *Settings → Pages → Source: GitHub Actions*, then add the
   Actions variable `API_URL = https://uniconnect-backend.onrender.com/api`. Push to `main` (or re-run the workflow).
3. Open `https://YOUR_GITHUB_USERNAME.github.io/uniconnect-frontend/`.

Free Render services sleep when idle; the first request can take ~30–60 s. Without `DB_URL` the data
lives in memory and resets on restart — attach a PostgreSQL database for real use.

## Local
`docker compose up --build` (needs `../uniconnect-backend`), then serve the frontend folder and set `config.js` to `http://localhost:8080/api`.
