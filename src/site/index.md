---
title: NMA 11ty Test Site
subtitle: A demo static generated site using Eleventy via a starter project scaffold called Eleventy One.
layout: layouts/base.njk
---


## Notable Features for this Demo Test Site

This site uses the following:

- An [Eleventy](https://11ty.io) starter project (template/skeleton site) called [Eleventy One](https://github.com/philhawksworth/eleventyone)
- A date format filter for Nunjucks based on [Luxon](https://moment.github.io/luxon)
- A tiny CSS pipeline with PostCSS
- A tiny inline JS pipeline. (<a href="#" class="btn-log">Test a console.log message</a>)
- A JS [search index](/search.json) generator
- [Netlify Dev](https://www.netlify.com/products/dev) for testing [Netlify redirects](https://netlify.com/docs/redirects/)
- Serverless (FaaS) development pipeline with [Netlify Dev](https://www.netlify.com/products/dev) and [Netlify Functions](https://www.netlify.com/products/functions)

## Notes

Advantages:

- [Eleventy](https://11ty.io) is a super fast, simple, and powerful SSG.

Disdvantages:

- This demo/test site is not setup with a CMS, therefore it requires a web dev to edit markdown files directly to update the site. However, [Netlify CMS](https://www.netlifycms.org/) could be added.

## Example Post pages

The pages found in in the posts

<ul class="listing">
{%- for page in collections.post -%}
  <li>
    <a href="{{ page.url }}">{{ page.data.title }}</a> -
    <time datetime="{{ page.date }}">{{ page.date | dateDisplay("LLLL d, y") }}</time>
  </li>
{%- endfor -%}
</ul>

## External API data source ready

The following links were sourced from [hawksworx.com](https://www.hawksworx.com/feed.json) and pre-rendered at build time.

<ul class="listing">
{%- for item in hawksworx.entries.slice(0,5) -%}
  <li>
    <a href="{{ item.link }}">{{ item.title }}</a>
  </li>
{%- endfor -%}
</ul>


## Tech Details and Prerequisites

- [Node and NPM](https://nodejs.org/)

## To Run locally

```bash
# clone the repo locally
git clone https://github.com/kccnma/eleventy-test1

# install the dependencies
npm install

# External data sources can be stashed locally
npm run seed

# It will then be available locally for building with
npm run start
```

## Optional: Add Netlify Helpers
Netlify Dev adds the ability to use Netlify redirects, proxies, and serverless functions.

```bash
# install the Netlify CLI in order to get Netlify Dev
npm install -g netlify-cli

# run a local server with some added Netlify sugar in front of Eleventy
netlify dev
```

A serverless functions pipeline is included via Netlify Dev. By running `netlify dev` you'll be able to execute any of your serverless functions directly like this:

- [/.netlify/functions/hello](/.netlify/functions/hello)
- [/.netlify/functions/fetch-joke](/.netlify/functions/fetch-joke)

### Redirects and proxies

Netlify's Redirects API can provide friendlier URLs as proxies to these URLs.

- [/api/hello](/api/hello)
- [/api/fetch-joke](/api/fetch-joke)




