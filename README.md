# factastichealth website

Priamry deployment:

https://vigorous-hawking-a51951.netlify.app/

Alternative deployment:

https://admiring-edison-538e61.netlify.app/

# Categories and tags

Categories and tags are added ad-hoc.  If an article has a tag, the tag
exists and a tag page is created.  If a tag is removed from every
article, the tags gets removed and the tag page is never created.  Same
for categories.

# Post order

Posts are ordered by date, from newer to older.

# Images with captions

For Kramdown (the Markdown parser) to recognize images as figures with
captions, this special syntax is required:

```markdown
Surrounding text

![Image caption](/image/url.jpg){:standalone}

More text

```

The `{:standalone}` part signals Kramdown to create a `<figure>` HTML
element with a caption.

For Netlify CMS, add an image and turn the editor into Markdown mode so
you can add the standalone syntax.



# Netlify CMS

Visit https://factastichealth.com/admin/ and login with Github account
to edit site contents.  To configure this:

* Visit Settings > Access Control on Netlify's panel
* Install Github as an OAuth Provider

More documentation here:

* https://www.netlifycms.org/docs/github-backend/
* https://docs.netlify.com/visitor-access/oauth-provider-tokens/#using-an-authentication-provider

Currently, there's a [bug preventing
spaces](https://github.com/netlify/netlify-cms/issues/4646) on the tags
and categories fields.  For the time being, tags and categories with
spaces can be edited manually.

# Adding articles manually

## Blog

Create a file `_posts/aaaa-mm-dd-downcase-title-without-spaces.md`.
`aaaa-mm-dd` is the publication date, for instance `2021-03-31`.  After
that comes the "slug" which acts as the URL, so an article entitled "The
Power of Fasting and Why am I Doing It" has a slug of
`the-power-of-fasting-and-why-am-i-doing-it` and its URL will be
https://factastichealth.com/the-power-of-fasting-and-why-am-i-doing-it/.

Template for new files:

```
---
layout: post
categories:
- Category
- Category 2
title: Article title
tags:
- Tag
- Tag 2
image: /path/to/file.jpg
---

Markdown content
```

The `.md` extension is important for Netlify CMS to be able to edit
articles.  `.markdown` won't work.

## Pages

Pages are files under `_pages/slug.md`, without a date.

```
---
layout: page
title: Page title
footer: true
---

Markdown content
```

The `footer` field is used to determine if a page is linked from the
footer or not.

# Wordpress migration

Articles that existed on Wordpress have an `id` field to match them to
the `posts` table.  Images were downloaded on the `wp-content/`
directory so they keep their URLs.

# Newsletter

Configure [Netlify
environment](https://app.netlify.com/sites/vigorous-hawking-a51951/settings/deploys#environment)
with:

```bash
JEKYLL_NEWSLETTER_FROM
JEKYLL_NEWSLETTER_TO
JEKYLL_NEWSLETTER_USERNAME
JEKYLL_NEWSLETTER_PASSWORD
```
# netlify build simulation
`docker compose run --rm jekyll sh -c "bundle install && JEKYLL_ENV=production bundle exec jekyll build"`

# command to generate uuid for the pages
`uuidgen | tr '[:upper:]' '[:lower:]'`

# local development

`docker compose up -d`

## check browser:
http://0.0.0.0:4000/

## show build logs
`docker-compose logs jekyll `