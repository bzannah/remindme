# remindme.wiki

- This is a plain static website. Publish `dist` as the public root.
- Keep `/` as a simple menu of links only. Do not add a visible heading, header, banner, introduction, footer, or app cards unless requested.
- Whenever adding a new sub-app at a route, also add its descriptive menu link to `dist/index.html` in the same change. Preserve the existing menu items and routes.
- Each top-level app lives in `dist/<route>/index.html`. Use root-relative menu URLs such as `/janaza`.
- Verify the homepage link and direct app URL after route changes. No build step or dependencies are required.
- The Janaza page's transliterations are visually primary, and every takbir has a border around its full content. Preserve this presentation unless the user changes it.
