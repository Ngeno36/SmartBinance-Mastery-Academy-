# Smart Binance Mastery — PayPal + Email Backend

This project implements:
- Frontend (public/index.html) with accessible modal and PayPal Buttons integration.
- Backend (server.js) using Node/Express:
  - /api/create-order to create a PayPal order (server-side)
  - /api/capture-order to capture a PayPal order and send a receipt
  - /api/free-request to deliver free resources via signed download link
  - /download to serve signed files stored in ./files
  - /api/config to return the PayPal client id for SDK loading

Recommended defaults used:
- Node.js + Express
- PayPal Checkout (server-side order creation & capture). PayPal email/business: kiprotichngeno872@gmail.com (set in your PayPal account)
- SendGrid for transactional email (optional but recommended)
- SQLite for simple order logging
- Signed, time-limited download links for free resources

Setup (local)
1. Clone repo (or create new repo and add files provided here).
2. Create a `.env` file from `.env.example` and fill in your credentials.
   - For testing use PayPal sandbox credentials (set PAYPAL_BASE to sandbox URL).
   - Obtain SendGrid API key and set FROM_EMAIL.
3. Create a `files/` directory and add PDFs named using the productId pattern:
   - Example: `files/beginner.pdf` for productId `beginner`
4. Install dependencies:
   npm install
5. Run:
   npm run dev
6. Open http://localhost:3000 and test free resource requests and paid purchases (sandbox).

PayPal sandbox notes
- Create a PayPal Developer account and create sandbox REST app to get client ID and secret.
- Use sandbox buyer accounts to test flow.
- The PayPal email business (recipient) is the account that owns the credentials (set to kiprotichngeno872@gmail.com in production PayPal account).

Deployment suggestions
- Vercel / Netlify functions: adapt server to serverless handlers (recommended for static site + serverless).
- Heroku / Render: straightforward host for full Express app.
- Always set environment variables in the deployment environment and keep secrets out of source control.

Security & production considerations
- Use HTTPS and enforce secure cookies if you add sessions.
- Verify webhooks from PayPal if you rely on asynchronous payment events.
- Rate-limit endpoints and validate inputs server-side.
- For file delivery, consider generating one-time links persisted in DB for stronger control.
- Keep DOWNLOAD_SECRET and API keys secure.

Next steps I can do for you
- Push these changes to your GitHub repo and open a PR (I need repo access).
- Add PayPal webhook verification route (recommended).
- Improve order UI, session-based order tracking, or admin pages listing orders.
- Integrate real file attachments sent via SendGrid (if you prefer attachment over link).

If you want me to push the branch into Ngeno36/my-site and open a PR, please:
1) Ensure the repository exists (owner: Ngeno36, repo: my-site).
2) Grant write access to the integration (or add me as a collaborator).
3) Reply and I will push a branch named `feature/paypal-integration` with these files and open a PR.

If you prefer I only provide files, copy them into your repo and then run:
 git add .
 git commit -m "Add PayPal integration, email delivery, and free resource links"
 git push origin main