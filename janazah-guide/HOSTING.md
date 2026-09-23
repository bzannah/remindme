# remindme.wiki

Deploy the contents of `dist` as the website's public root. The whole directory is the site:

- `/` serves `dist/index.html`, the plain menu of apps.
- `/janaza` serves `dist/janaza/index.html`. Directory-index hosting may normalize this to `/janaza/`.

For Cloudflare Pages Direct Upload, upload the `dist` folder or a ZIP of its contents. The homepage must be at the upload root. There is no build, server, database, or API to configure.

The homepage uses system fonts. The Janaza page contains its own styles and JavaScript and loads Google Fonts with system fallbacks.

## Cloudflare Pages with GitHub

The deployment repository is `bzannah/remindme`. The `janazah-guide` folder contains ordinary tracked files; it is not a Git submodule.

Use these build settings:

- Production branch: `main`
- Framework preset: `None`
- Root directory: `janazah-guide`
- Build command: `exit 0`
- Build output directory: `dist`

If the root directory is left blank, use `janazah-guide/dist` as the build output directory instead.

See [Cloudflare's static HTML guide](https://developers.cloudflare.com/pages/framework-guides/deploy-anything/).

## Adding another app

1. Create `dist/<route>/index.html` and place its assets in the same route directory.
2. Add one descriptive link to the list in `dist/index.html`, targeting `/<route>`.
3. Keep the homepage limited to app links, with no header, banner, introduction, or footer.
4. Deploy the full `dist` directory so all existing apps stay available.

The canonical URLs use `https://remindme.wiki/`. Connecting the domain is a separate hosting configuration step.
