# MIYORA MD Admin Panel — Vercel Frontend (No Login Screen)

## Deploy
1. Upload `index.html` and `vercel.json` to the root of a GitHub repository.
2. Import the repository into Vercel. Choose Framework Preset **Other**, no build command, output directory `.`.
3. The dashboard opens directly without an in-page login form. The default backend origin is configured in `index.html`; update `DEFAULT_BACKEND` if your backend URL changes.
4. Configure backend CORS to allow your Vercel domain.

## Security warning — read before deploying
Removing the login screen does **not** automatically remove authentication enforced by your backend. If backend endpoints require an admin token, data-changing features will return 401/403 until you configure a safe access method. Do not make admin endpoints publicly unauthenticated just because the dashboard is for personal use. Protect the Vercel deployment using an access-control layer available to your account, and keep owner authorization on the backend. Anyone who can open a public no-login admin page may otherwise be able to operate it if the backend allows unauthenticated requests.

## Channel removal
The Channel Manager Remove button calls `DELETE /code/api/admin/channels/:jid` with `x-confirm: yes`. The backend must implement this endpoint and persist removal from the reaction-channel configuration. If the route is missing or protected, the UI will show an error.

## Important
This ZIP contains the responsive frontend, not the bot backend/database. Features work only when corresponding backend routes exist and authorize the request. The frontend expects routes below `/code/api/admin` for stats, number analytics, system metrics, wallets/coins, channels, API keys, webhooks, alerts, and analytics.
