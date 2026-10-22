# FitLog

Responsive personal food log with Home, Entry, and Data pages. Food entries and goals are saved in this browser's local storage. Food lookup searches USDA FoodData Central, then Open Food Facts, and falls back to Google Search when no nutrition match is found. Google web results are shown as links; verify nutrition values before logging. Food recognition is not connected.

## Start

Install Node.js 18 or newer. Copy `.env.example` to `.env`, set your login details, then start FitLog with `npm start` and open `http://localhost:3001`. The `.env` file is local and must never be committed.

Google's Custom Search JSON API integration is optional. It requires both an API key and a Programmable Search Engine ID. Set `GOOGLE_CSE_API_KEY` and `GOOGLE_CSE_ID` in the helper's PowerShell session before starting `node server.js`. The API is closed to new customers and scheduled for discontinuation on January 1, 2027; without those credentials, FitLog provides a regular Google Search link instead. See the [Google API guide](https://developers.google.com/custom-search/v1/overview).

The local website uses local browser storage for meals; it does not upload your diary to a cloud database.


## Hosting

FitLog can run as a Node.js web service on Render or Railway. Connect the GitHub repository, use `npm install` as the build command and `npm start` as the start command, then set `FITLOG_USERNAME` and a strong `FITLOG_PASSWORD` in the host's environment settings. Do not use the sample password for an internet-accessible deployment.

Food logs and custom foods stay in browser local storage unless GitHub repository storage is configured. To sync between devices, set `FITLOG_GITHUB_REPO`, `FITLOG_GITHUB_BRANCH`, and `FITLOG_GITHUB_TOKEN` in the hosting service. Use a fine-grained token scoped only to this private repository with Contents read/write access. The backend then stores `data/food-logs.json` in the repository on each saved change. Each save creates a Git commit, so previous log versions remain in repository history. Never put the token in source code or commit `.env`.

