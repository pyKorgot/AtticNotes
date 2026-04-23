# Attic Notes

Attic Notes is a personal blog built with Astro.

The project is designed as a quiet archive for notes, experiments, project traces, and short texts, with a paper-and-ink visual style, RSS, sitemap, and basic SEO already in place.

## Stack

- Astro 6
- TypeScript (`strict`)
- MD and MDX content collections
- ESLint for linting
- GitHub Actions for CI

## Features

- custom paper-themed UI with light and dark modes
- blog posts stored in `src/content/blog`
- typed content schema with `draft`, `tags`, `featured`, and `heroImage`
- RSS feed
- sitemap generation
- canonical URLs and Open Graph metadata
- structured data for blog posts

## Requirements

- Node.js `>=22.12.0`
- npm

## Local Development

Install dependencies:

```sh
npm install
```

Start the dev server:

```sh
npm run dev
```

The site will be available at `http://localhost:4321`.

## Scripts

| Command | Description |
| :-- | :-- |
| `npm run dev` | Start local Astro dev server |
| `npm run lint` | Run ESLint |
| `npm run check` | Run `astro check` |
| `npm run build` | Run `astro check` and build to `dist/` |
| `npm run preview` | Preview the production build locally |

## Project Structure

```text
.
├── .github/workflows/   # CI workflows
├── public/              # static public files
├── src/
│   ├── assets/          # images used by the site and posts
│   ├── components/      # shared Astro components
│   ├── content/         # blog content collections
│   ├── layouts/         # page and post layouts
│   ├── pages/           # routes
│   ├── styles/          # global styles and theme tokens
│   └── consts.ts        # global site metadata
├── astro.config.mjs
├── eslint.config.mjs
├── package.json
└── tsconfig.json
```

## Content

Posts live in `src/content/blog` as `.md` or `.mdx` files.

The current content schema includes:

- `title`
- `description`
- `pubDate`
- `updatedDate`
- `draft`
- `tags`
- `featured`
- `heroImage`

Draft posts are excluded from the blog index and RSS.

## SEO

The project already includes:

- canonical URLs
- Open Graph and Twitter metadata
- `robots.txt`
- `sitemap-index.xml`
- `rss.xml`
- `BlogPosting` structured data for post pages

Production URL is configured as `https://attic-notes.site`.

## CI/CD

GitHub Actions workflows are defined in `.github/workflows/ci.yml` and `.github/workflows/deploy.yml`.

`CI` runs on pushes to `master` and on pull requests, and checks:

- dependency installation
- ESLint
- Astro build

`Deploy` runs on pushes to `master` and via manual `workflow_dispatch`. It:

- builds the site in GitHub Actions
- uploads `dist/` as an artifact
- deploys the artifact to a VPS over SSH with `rsync`
- targets the `production` environment

### Deployment Secrets

Configure these GitHub environment secrets for `production`:

- `SSH_HOST` - VPS hostname or IP
- `SSH_PORT` - SSH port, usually `22`
- `SSH_USER` - deploy user on the server
- `SSH_PRIVATE_KEY` - private key allowed to write to the deploy directory
- `SSH_KNOWN_HOSTS` - output of `ssh-keyscan -p <port> <host>`
- `DEPLOY_PATH` - directory served by Caddy, for example `/var/www/attic-notes`

## Deployment Notes

The project builds to static output in `dist/`, so it can be deployed to:

- Vercel
- Netlify
- Cloudflare Pages
- a self-hosted VPS serving `dist/` through Caddy or another static web server

For the current setup, the recommended self-hosted layout is:

- Caddy serves files from `/var/www/attic-notes`
- GitHub Actions deploys `dist/` into that directory with `rsync --delete`

## License

License is not defined yet.

If you plan to open-source the code while keeping the writing and visual assets protected, a good next step is:

- `MIT` for code
- separate rights notice for posts and images
