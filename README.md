# FitLog

Responsive personal food diary with Home, Entry, and Data pages. Local use stores entries in this browser. When configured for hosted use, the server syncs logs and custom foods to `data/food-logs.json` in this private repository.

## Deploy

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https%3A%2F%2Fgithub.com%2FAditya-Maity%2FFinal-FoodFit)

This launches the Render setup for the Node web service defined in `render.yaml`. Connect Render to your GitHub account and grant it access to this private repository. During setup, enter the requested login password and a GitHub fine-grained access token scoped to this repo with Contents read/write permission. The username is `aditya maity`; use the password you want for the hosted login. Keep the token secret and never commit it.

Once deployed, Render provides a public `onrender.com` address. The free web service can sleep after inactivity and may take a little time to wake. Each saved diary update is committed to this private GitHub repo, so it will appear in `data/food-logs.json` and in repository history. Treat the repo as sensitive because it contains personal nutrition records.

## Run on this PC

Install Node.js 18 or newer, copy `.env.example` to `.env`, set your login details, then run `npm start` and visit `http://localhost:3001`. The `.env` file is local and must never be committed.

Food lookup searches USDA FoodData Central, then Open Food Facts, and can offer a Google Search link when nutrition matches are unavailable. Google API results require a Custom Search API key and search engine ID. Food recognition is not connected.