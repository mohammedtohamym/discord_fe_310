# Render deployment instructions

Use these exact values in the Render dashboard for a Static Site deployment (recommended).

1. Create a new service → Static Site

2. Fill these fields:

- Build Command:
  npm ci && npm run build

- Publish Directory:
  build

- Start Command:
  (leave empty)

3. Environment variables (set in Service → Environment → Environment Variables)

- REACT_APP_API_BASE_URL
  Example: https://api.example.com/api

- REACT_APP_SOCKET_SERVER_URL
  Example: https://sockets.example.com

- REACT_APP_TURN_SERVERS
  Example (one-line JSON array):
  [{"urls":"turn:turn.example.com:3478","username":"turnuser","credential":"turnpass"}]

4. Node version

- The project prefers Node 18. Render will respect `.nvmrc` or `package.json` engines. If the build fails, set Node version to 18 in the service settings.

5. Troubleshooting

- If you see OpenSSL/ERR_OSSL_EVP_UNSUPPORTED during build, either:
  - Ensure Node 18 is selected for the service, or
  - Add environment variable: NODE_OPTIONS = --openssl-legacy-provider

6. Quick local test before deploy

```bash
npm ci
npm run build
npx serve -s build -l 3000
# open http://localhost:3000
```
