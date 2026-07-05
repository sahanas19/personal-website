# Personal Website

My personal website — built with [Astro](https://astro.build) and [Tailwind CSS](https://tailwindcss.com), deployed to Cloudflare Pages at [sahana.cc](https://sahana.cc).

## Local development

```
npm install
npm run dev
```

Visit `http://localhost:4321`.

```
npm run build      # build to dist/
npm run preview    # preview the production build locally
```

## Project structure

- `src/layouts/Layout.astro` — shared HTML shell, fonts, meta tags
- `src/components/` — `Nav`, `Hero`, `About`, `Projects`, `Contact`, `Footer`
- `src/pages/index.astro` — composes the components into the homepage
- `src/styles/global.css` — Tailwind import + theme tokens

## Customizing

Edit the placeholder content in `src/components/`:

- `Hero.astro` — tagline
- `About.astro` — bio paragraph
- `Projects.astro` — the `projects` array (title, description, link)
- `Contact.astro` — the `links` array (email, GitHub, LinkedIn, etc.)

## Deployment (Cloudflare Pages via GitHub Actions)

Every push to `main` triggers [.github/workflows/deploy.yml](.github/workflows/deploy.yml), which builds the site and deploys it to Cloudflare Pages using [`cloudflare/pages-action`](https://github.com/cloudflare/pages-action).

**One-time setup** (do this once, from your own terminal — not shared with anyone):

1. **Create a Cloudflare API token**: Cloudflare dashboard → My Profile → API Tokens → Create Token → use the "Edit Cloudflare Workers" template or a custom token with `Account.Cloudflare Pages: Edit` permission.
2. **Find your Account ID**: shown in the right sidebar of any zone overview page in the Cloudflare dashboard (e.g. the `sahana.cc` overview page).
3. **Create the Pages project** (one time):
   ```
   CLOUDFLARE_API_TOKEN=<token> CLOUDFLARE_ACCOUNT_ID=<account-id> npx wrangler pages project create personal-website --production-branch=main
   ```
4. **Add the secrets to the GitHub repo** (prompts hide input, nothing is echoed or stored in shell history):
   ```
   gh secret set CLOUDFLARE_API_TOKEN --repo sahanas19/personal-website
   gh secret set CLOUDFLARE_ACCOUNT_ID --repo sahanas19/personal-website
   ```
5. Push to `main` — the Action builds and deploys automatically. Check progress under the repo's **Actions** tab.
6. **Connect the custom domain**: Cloudflare dashboard → Workers & Pages → `personal-website` project → Custom domains → Add `sahana.cc` (and `www.sahana.cc` if desired). Since the domain's zone already lives in the same Cloudflare account, DNS and SSL are configured automatically.
