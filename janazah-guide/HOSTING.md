# remindme.wiki

Deploy the contents of `dist` as the website's public root. The whole directory is the site:

- `/` serves `dist/index.html`, the plain menu of apps.
- `/janaza` serves `dist/janaza/index.html`. Directory-index hosting may normalize this to `/janaza/`.

The site is deployed as static assets on Cloudflare Workers. There is no build, application server, database, or API to configure.

The homepage uses system fonts. The Janaza page contains its own styles and JavaScript and loads Google Fonts with system fallbacks.

## Cloudflare Workers with GitHub

The deployment repository is `bzannah/remindme`. The `janazah-guide` folder contains ordinary tracked files; it is not a Git submodule.

Use these build settings:

- Production branch: `main`
- Worker name: `remindme`
- Root directory: `/` (the repository root)
- Build command: leave empty
- Deploy command: `npx wrangler deploy`

The root `wrangler.jsonc` selects `./janazah-guide/dist` as the assets directory. It deploys both the homepage and every app route together. No Worker script is needed.

For a local configuration check, run `npx wrangler deploy --dry-run` from the repository root.

See [Cloudflare's static assets guide](https://developers.cloudflare.com/workers/static-assets/).

## Alternative: Cloudflare Pages Direct Upload

Upload the `dist` folder or a ZIP of its contents. The homepage must be at the upload root. The Workers configuration is not needed for this alternative.

## Adding another app

1. Create `dist/<route>/index.html` and place its assets in the same route directory.
2. Add one descriptive link to the list in `dist/index.html`, targeting `/<route>`.
3. Keep the homepage limited to app links, with no header, banner, introduction, or footer.
4. Deploy the full `dist` directory so all existing apps stay available.

The canonical URLs use `https://remindme.wiki/`. Connecting the domain is a separate hosting configuration step.
