# remindme.wiki deployment

- The GitHub repository at this root is the deployment source for Cloudflare.
- Cloudflare Workers deploys static assets using the root `wrangler.jsonc`. Run `npx wrangler deploy` from this repository root; no build command is needed.
- The website is in `janazah-guide/dist`; its detailed content rules are in `janazah-guide/AGENTS.md`.
- Track app files in this repository directly. Do not initialize nested Git repositories or add app folders as submodules.
- Publish the entire static directory so `/` and every sub-app remain available.
- When adding a sub-app, also add its menu item to `janazah-guide/dist/index.html`.
- `.openai` and `.sites-runtime` are local metadata for an earlier preview, not part of the Cloudflare deployment.
