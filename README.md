# Svelte Demonstrator and Starter App Template

This is a project template for [Svelte 3](https://svelte.dev) apps.

It is both a Component Demonstrator and also an App Starter Template for Svelte.

## Demonstration

For a demonstration see [svelte-component-demo.surge.sh](http://svelte-component-demo.surge.sh/).

## What is contains

TL;DR; This looks pretty, but does nothing useful.


It is client side only - deploy it to AWS S3 or surge or elsewhere, or run it locally using npm run dev - no server (eg Sapper, Express, NodeJS) is required.

A few components are implemented - enough to get a simple website/app started.

Components implemented include -
- Nav Bar with dropdowns & icons
- Mega Menu with 3 columns & icons
- Chips
- Testimonial type cards
- Cards
- Toast with timed auto hide
- Modal dialog
- Forms - this needs more work
- Tables - optionally striped
- Tabs
- Side Curtain (with optional menu) that slides in and out, with option to slide page across
- Popup on click and Tooltip (with fade in & auto hide)
- Callout
- Badge
- Hero banner
- Footer
- Box
- Section
- Container
- Star Rating

The components are mostly responsive. There is no grid/flexbox implemented - choose your own.  All the above are easily customised - the relevant CSS and HTML and JS are all grouped together in a single file - thanks svelte! Just delete the components and pages that you don't need.

The CSS variables are in /public/global.css and all other CSS is local to each component. This project is more about getting components to work, rather than styling them.

The project file structure separates components from the pages.

The only other dependency is the [svero router](https://github.com/kazzkiq/svero). Routes are defined in /Routes.svelte

However, [fontawesome](https://fontawesome.com) and [materialdesignicons](https://materialdesignicons.com) and also [FeatherIcons](https://feathericons.com) are all used - the only reason for doing so is to demonstrate that there is no particular dependency on any of them. Remove the links from public/index.html if desired.


*Note that you will need to have [Node.js](https://nodejs.org) installed.*

The whole project deployed comes in at close to 200K - that includes a 100K Hero image.

## Get started

Clone the source for this Demo from [github](https://github.com/keithj2780/svelte-starter-app)

```bash
git clone https://github.com/keithj2780/svelte-starter-app
```

Install the dependencies...

```bash
cd svelte-starter-app
npm install
```

...then start webpack:

```bash
npm run dev
```

Navigate to [localhost:8080](http://localhost:8080). You should see the app running. Edit a components or pages file in `src/pages` or `src/components`, save it, and the page should reload with your changes.


## Generate a production build

```bash
npm run build
```


## Deploying to the web

Sync to AWS with 
```
aws s3 sync ./public/ s3://$MY-BUCKET --acl public-read
```

or to [now](https://zeit.co/now) or [surge.sh](https://surge.sh)
