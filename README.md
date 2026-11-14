# jargha
game
DUO QUEST - Cloudflare deployment project

This version is adapted for Cloudflare Workers + Durable Objects. It does not use Express or Socket.IO.

Deploy using Cloudflare Workers Builds (Git integration):
1. Create a GitHub account if needed.
2. Create a new empty GitHub repository named duo-quest.
3. Upload the contents of this project (not the containing parent folder) to the repository.
4. In Cloudflare dashboard, go to Workers & Pages > Create > Import a repository.
5. Connect GitHub and select duo-quest.
6. Framework preset: None.
7. Build command: leave blank (or `npm install` if the dashboard requires a build command).
8. Deploy command: `npx wrangler deploy`.
9. Save and deploy.

Wrangler config declares the Durable Object binding and its SQLite migration. Cloudflare provisions the Durable Object class when deployed.

After deployment, Cloudflare provides a workers.dev URL. Open it on both phones. Choose Arun on one, Suzala on the other, and enter the same room code (DUO26).

Important:
- This is an early playable prototype, not a production-hardened game.
- Multiplayer state is currently held in the Durable Object's memory; if the room is evicted or the Worker is redeployed, the match may reset.
- For production, add persistent room state, reconnection handling, rate limits, and stronger validation.
- Cloudflare account and GitHub authorization are required. Cloudflare dashboard labels can change.
