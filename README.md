# Portfolio Website

A minimal, production-ready portfolio site built with Astro and Tailwind CSS, served via NGINX in Docker.

## Tech Stack

- **Astro** — static site generation, zero JS by default
- **Tailwind CSS** — utility-first styling
- **NGINX** — lightweight static file server
- **Docker** — multi-stage containerized build

## Project Structure

```
├── src/
│   ├── components/      # Astro components (Hero, About, Skills, etc.)
│   ├── layouts/          # Base HTML layout
│   ├── pages/            # Route pages
│   └── styles/           # Global CSS
├── public/               # Static assets (favicon, images)
├── astro.config.mjs      # Astro configuration
├── tailwind.config.mjs   # Tailwind configuration
├── Dockerfile            # Multi-stage Docker build
├── nginx.conf            # NGINX server configuration
└── package.json
```

## Getting Started

### Prerequisites

- Node.js 18+
- npm
- Docker (optional, for containerized deployment)

### Local Development

```bash
# Install dependencies
npm install

# Start dev server (http://localhost:4321)
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

### Docker

```bash
# Build the image
docker build -t portfolio .

# Run the container
docker run -d -p 8080:80 --name portfolio portfolio
```

The site will be available at `http://localhost:8080`.

To stop:

```bash
docker stop portfolio && docker rm portfolio
```

## Customization

All content is defined as plain data at the top of each component file in `src/components/`. Edit the variables to replace placeholder content with your own:

| File              | What to edit                        |
| ----------------- | ----------------------------------- |
| `Hero.astro`      | Name, title, tagline                |
| `About.astro`     | Bio text, stats                     |
| `Skills.astro`    | Skill categories and items          |
| `Projects.astro`  | Project cards (title, desc, links)  |
| `Experience.astro`| Work history entries                |
| `Contact.astro`   | Email address, social links         |
| `Footer.astro`    | Copyright name                      |
| `Layout.astro`    | SEO meta tags, page title           |

## Performance Notes

- **Zero client-side JS frameworks** — only ~40 lines of vanilla JS for the navbar
- **Static HTML output** — no SSR, no hydration
- **Final Docker image** — ~25 MB (nginx:alpine + static files)
- **Gzip enabled** in NGINX for all text assets
- **Aggressive caching** for static assets (1 year), short cache for HTML (1 hour)
