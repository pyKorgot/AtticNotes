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

## CI

GitHub Actions workflow is defined in `.github/workflows/ci.yml`.

It runs on pushes to `main` and on pull requests, and checks:

- dependency installation
- ESLint
- Astro build

## Deployment Notes

The project builds to static output in `dist/`, so it can be deployed to:

- Vercel
- Netlify
- Cloudflare Pages
- a self-hosted VPS serving `dist/` through Caddy or another static web server

## License

License is not defined yet.

If you plan to open-source the code while keeping the writing and visual assets protected, a good next step is:

- `MIT` for code
- separate rights notice for posts and images
