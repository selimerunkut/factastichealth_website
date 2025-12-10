# System Patterns *Optional*

This file documents recurring patterns and standards used in the project.
It is optional, but recommended to be updated as the project evolves.
2025-12-10 06:43:54 - Log of updates made.

*

## Coding Patterns

* Markdown files with YAML frontmatter for metadata (layout, title, categories, tags, image).
* Kramdown Markdown syntax with `{:standalone}` for captioned images in figures.
* SCSS partials in `_sass/` for reusable styles (_stars.scss, _syntax.scss).

## Architectural Patterns

* Static site generation with Jekyll: collections for pages (`_pages/`), dated posts (`_posts/`).
* Headless CMS integration: Netlify CMS (`admin/config.yml`) for editing Markdown content.
* Local development: Docker Compose with official Jekyll image, volume mounts for source and bundle.
* Deployment: Netlify continuous deployment from Git.
* Frontend: Lunr.js for client-side search (`lunrsearchengine.js`), lazy loading images, Mediumish theme JS.

## Testing Patterns

* No dedicated testing framework identified.

2025-12-10 15:09:00 - Initial patterns documented from project structure analysis (_pages/, _posts/, _sass/, assets/js/, admin/).
