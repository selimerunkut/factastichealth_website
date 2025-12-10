# Product Context

This file provides a high-level overview of the project and the expected product that will be created. Initially it is based upon projectBrief.md (if provided) and all other available project-related information in the working directory. This file is intended to be updated as the project evolves, and should be used to inform all other modes of the project's goals and context.
2025-12-10 06:43:54 - Initial creation.
2025-12-10 15:07:00 - Updated with README.md content (project overview, features, CMS details).
2025-12-10 15:07:30 - Updated with _config.yml details (technologies, plugins).
2025-12-10 15:08:00 - Updated with Gemfile and docker-compose.yml (confirmed plugins, local dev setup).

*

## Project Goal

* The primary goal is to host and manage the Factastichealth website, which includes publishing articles and pages.
* Ensure content can be managed both manually and via Netlify CMS.
* Provide a platform for health-related content, likely articles on fasting, yoga, autoimmune diseases, etc. (inferred from _posts directory contents)

## Key Features

*   **Content Management:** Articles and pages managed via Markdown files, with CRUD operations supported through Netlify CMS.
*   **Dynamic Categorization/Tagging:** Categories and tags are dynamically created based on their presence in articles.
*   **Date-Based Post Ordering:** Articles are displayed in reverse chronological order.
*   **Rich Media Support:** Images with captions supported via Kramdown's `{:standalone}` syntax.
*   **Deployment:** Utilizes Netlify for continuous deployment.
*   **Newsletter Integration:** Supports newsletter functionality via Netlify environment variables.
*   **Wordpress Migration Compatibility:** Legacy articles from Wordpress are integrated, maintaining original image URLs.

## Overall Architecture

The Factastichealth website is a static site generated using Jekyll. It is deployed on Netlify. Content can be authored directly in Markdown files within `_posts/` for articles and `_pages/` for static pages, or via the integrated Netlify CMS. Kramdown is used as the Markdown parser, supporting specific syntax for image captions. A `docker-compose.yml` suggests a containerized local development environment.

### Technologies Used (from _config.yml and Gemfile)
*   **Static Site Generator:** Jekyll (~>4)
*   **Markdown Processor:** Kramdown (with GFM input and Rouge for syntax highlighting)
*   **Jekyll Plugins:** jekyll-paginate, jekyll-sitemap, jekyll-feed, jekyll-seo-tag, jekyll-archives, webrick
*   **Deployment Platform:** Netlify
*   **Content Management System:** Netlify CMS
*   **Newsletter:** SMTP-based newsletter with Mailjet (in-v3.mailjet.com port 587)

### Local Development (from docker-compose.yml)
* Docker Compose service 'jekyll' using official `jekyll/jekyll` image
* Volumes: source code mount `./:/srv/jekyll`, bundle `./vendor/bundle/:/usr/local/bundle`
* Port mapping: 4000:4000
* Command: `jekyll serve --force_polling --drafts`