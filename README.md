# A statically generated blog example using Next.js and Webiny

This example showcases Next.js's [Static Generation](https://nextjs.org/docs/basic-features/pages) feature using [Webiny](https://webiny.com/) as the data source.
## Demo

[https://next-blog-webiny.vercel.app/](https://next-blog-webiny.vercel.app/)

## Deploy your own

Deploy the example using [Vercel](https://vercel.com?utm_source=github&utm_medium=readme&utm_campaign=next-example):

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/git/external?repository-url=https://github.com/vercel/next.js/tree/canary/examples/cms-webiny&project-name=cms-webiny&repository-name=cms-webiny&env=PREVIEW_API_SECRET,WEBINY_API_SECRET,NEXT_PUBLIC_WEBINY_API_URL,NEXT_PUBLIC_WEBINY_PREVIEW_API_URL&envDescription=Required%20to%20connect%20the%20app%20with%20Webiny&envLink=https://vercel.link/cms-webiny-env)

### Related examples

- [WordPress](/examples/cms-wordpress)
- [DatoCMS](/examples/cms-datocms)
- [Sanity](/examples/cms-sanity)
- [TakeShape](/examples/cms-takeshape)
- [Prismic](/examples/cms-prismic)
- [Contentful](/examples/cms-contentful)
- [Strapi](/examples/cms-strapi)
- [Agility CMS](/examples/cms-agilitycms)
- [Cosmic](/examples/cms-cosmic)
- [ButterCMS](/examples/cms-buttercms)
- [Storyblok](/examples/cms-storyblok)
- [GraphCMS](/examples/cms-graphcms)
- [Kontent](/examples/cms-kontent)
- [Umbraco Heartcore](/examples/cms-umbraco-heartcore)
- [Builder.io](/examples/cms-builder-io)

## How to use

Execute [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app) with [npm](https://docs.npmjs.com/cli/init) or [Yarn](https://yarnpkg.com/lang/en/docs/cli/create/) to bootstrap the example:

```bash
npx create-next-app --example cms-webiny cms-webiny-app
# or
yarn create next-app --example cms-webiny cms-webiny-app
```
### Step 1. Set up a Webiny project

Follow the [Webiny docs](https://www.webiny.com/docs/tutorials/install-webiny) to install a Webiny project on your cloud hosting provider.

If you get stuck or have any questions, please [join the community](http://webiny-community.slack.com "Webiny slack channel") and reach out for some help.

Once you have an app up and running click into the "HeadlessCMS" app, click on *models* and add the following models and fields:

#### Authors

- A `text` field with the value "name"
- A `text` field with the value "slug" (optionally add a validator using this regex which will make sure you have valid urls: `^(?!.*--)[a-z0-9\-]+$`)
- a `files` field with the value "picture"

#### Posts

- A `text` field with the value "title"
- A `text` field with the value "slug" (optionally use the regex above as a validator)
- A `files` field with the value "featured image"
- A `rich text` field with the value "body"
- A `reference` field with the value "Author"

Next, choose *API Keys* in the sidebar. Add an API key with any name and description. Select "Headless CMS" and choose a Custom access level for all content model groups with the values `read` and `preview`. Save the API token and the Token itself will be revealed.

You will be able to use the same API token for both published and draft posts.

### Step 2. Set up environment variables

Copy the `.env.local.example` file to `.env.local`, then set the variables as follows:

- `PREVIEW_API_SECRET` can be any random string (but avoid spaces), like `MY_SECRET` - this is used for [Preview Mode](https://nextjs.org/docs/advanced-features/preview-mode).
- WEBINY_API_SECRET this will be your security token generated in Webiny
- You can find the values for `NEXT_PUBLIC_WEBINY_API_URL` and `NEXT_PUBLIC_WEBINY_PREVIEW_API_URL` two ways: From your local webiny project root, run `yarn webiny info`, alternatively go to *API Playground* in the sidebar. At the top of the graphQL explorer are four tabs, one for each of our APIs, and you'll see both the Read API and the Preview API on those tabs. The URL for your environment is just below the tab. ([More info here if you get stuck](https://www.webiny.com/docs/headless-cms/basics/graphql-api))

### Step 3. Run Next.js in development mode

Inside the Next.js app directory, run:

```bash
npm install
npm run dev

# or

yarn install
yarn dev
```

Your blog should be up and running on [http://localhost:3000](http://localhost:3000)!

The best place to debug is inside the `fetchAPI` function in `lib/api.js`. If you need help, you can post on [GitHub discussions](https://github.com/vercel/next.js/discussions).

### Step 4. Try preview mode

If you go to the `/posts/draft` page on localhost, you won't see this post because it’s not published. However, if you use the **Preview Mode**, you'll be able to see the change ([Documentation](https://nextjs.org/docs/advanced-features/preview-mode)).

To enable the Preview Mode, go to this URL:

```
http://localhost:3000/api/preview?secret=<secret>&slug=draft
```

- `<secret>` should be the string you entered for `PREVIEW_API_SECRET`.
- `<slug>` should be the post's `slug` attribute.

You should now be able to see the draft post. To exit the preview mode, you can click **Click here to exit preview mode** at the top.

To add more preview pages, create a post and set the **status** as `draft`.

### Step 6. Deploy on Vercel

You can deploy this app to the cloud with [Vercel](https://vercel.com?utm_source=github&utm_medium=readme&utm_campaign=next-example) ([Documentation](https://nextjs.org/docs/deployment)).

#### Deploy Your Local Project

To deploy your local project to Vercel, push it to GitHub/GitLab/Bitbucket and [import to Vercel](https://vercel.com/new?utm_source=github&utm_medium=readme&utm_campaign=next-example).

**Important**: When you import your project on Vercel, make sure to click on **Environment Variables** and set them to match your `.env.local` file.

#### Deploy from Our Template

Alternatively, you can deploy using our template by clicking on the Deploy button below.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/git/external?repository-url=https://github.com/vercel/next.js/tree/canary/examples/cms-webiny&project-name=cms-webiny&repository-name=cms-webiny&env=PREVIEW_API_SECRET,WEBINY_API_SECRET,NEXT_PUBLIC_WEBINY_API_URL,NEXT_PUBLIC_WEBINY_PREVIEW_API_URL&envDescription=Required%20to%20connect%20the%20app%20with%20Webiny&envLink=https://vercel.link/cms-webiny-env)
# Notes

This blog-starter uses [Tailwind CSS](https://tailwindcss.com) [(v3.0)](https://tailwindcss.com/blog/tailwindcss-v3).
