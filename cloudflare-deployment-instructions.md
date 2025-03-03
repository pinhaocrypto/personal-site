# Deploying with Cloudflare Pages

## Table of Contents

- [Configuration](#configuration)
  - [Step 1. Set up the environment](#step-1-set-up-the-environment)
  - [Step 2. Set up the project locally](#step-2-set-up-the-project-locally)
  - [Step 3. Run Next.js locally in development mode](#step-3-run-nextjs-locally-in-development-mode)
  - [Step 4. Deploy to production](#step-4-deploy-to-production)

## Deploying with Cloudflare Pages

### Step 1. Set up the environment

Create a Cloudflare account if you don't already have one at [dash.cloudflare.com](https://dash.cloudflare.com/sign-up).

### Step 2. Set up the project locally

[Clone the repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) to your local machine. Once cloned, run the following command from the project's root directory:

```bash
npm install
```

Create a `.env.local` file in the root directory to add your Sanity credentials:

```
NEXT_PUBLIC_SANITY_PROJECT_ID="Your Sanity Project Id"
NEXT_PUBLIC_SANITY_DATASET="Your Sanity Dataset"
SANITY_API_WRITE_TOKEN="Your Sanity API Write Token"
SANITY_API_READ_TOKEN="Your Sanity API Read Token"
```

### Step 3. Run Next.js locally in development mode

```bash
npm install && npm run dev
```

When you run this development server, the changes you make in your frontend and studio configuration will be applied live using hot reloading.

Your personal website should be up and running on [http://localhost:3000](http://localhost:3000)! You can create and edit content on [http://localhost:3000/studio](http://localhost:3000/studio).

### Step 4. Deploy to production

There are two methods to deploy your site to Cloudflare Pages:

#### Option 1: Direct deployment

Install Wrangler (Cloudflare's CLI tool) if you haven't already:

```bash
npm install wrangler --global
```

Then, build and deploy your site:

```bash
npm run deploy
```

#### Option 2: Git integration

1. Push your code to a GitHub or GitLab repository
2. Log in to the [Cloudflare dashboard](https://dash.cloudflare.com/)
3. Navigate to **Workers & Pages** > **Create application** > **Pages** > **Connect to Git**
4. Select your repository
5. Configure your build settings:
   - Build command: `npm run build`
   - Build output directory: `.next`
   - Environment variables: Add your Sanity credentials here

Cloudflare Pages will now build and deploy your Next.js app automatically on every push to your main branch.

After deployment, your site will be available at a `*.pages.dev` domain. You can also configure a custom domain in the Cloudflare dashboard.
