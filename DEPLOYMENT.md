# Portfolio Pro Deployment Guide

This guide provides detailed instructions on how to deploy your Portfolio Pro website to various hosting platforms.

## Table of Contents

1. [Build Process](#build-process)
2. [Deployment Options](#deployment-options)
   - [Netlify](#netlify)
   - [Vercel](#vercel)
   - [GitHub Pages](#github-pages)
   - [Firebase Hosting](#firebase-hosting)
   - [AWS Amplify](#aws-amplify)
3. [Custom Domain Setup](#custom-domain-setup)
4. [Environment Variables](#environment-variables)
5. [Performance Optimization](#performance-optimization)
6. [Troubleshooting](#troubleshooting)

## Build Process

Before deploying your portfolio, you need to build it for production. The build process optimizes your code, bundles your assets, and generates static files that can be served by any web server.

To build your portfolio for production, run:

```bash
npm run build
# or
yarn build
```

This will create a `dist` directory with the production-ready files.

To preview the production build locally, run:

```bash
npm run preview
# or
yarn preview
```

This will start a local server at `http://localhost:4173` (or another port if 4173 is already in use) that serves your production build.

## Deployment Options

### Netlify

Netlify is a popular platform for deploying static websites with continuous deployment, form handling, and other features.

#### Deploying to Netlify

**Option 1: Netlify CLI**

1. Install the Netlify CLI:

```bash
npm install -g netlify-cli
```

2. Login to your Netlify account:

```bash
netlify login
```

3. Initialize a new Netlify site:

```bash
netlify init
```

4. Follow the prompts to set up your site.

5. Deploy your site:

```bash
netlify deploy --prod
```

**Option 2: Netlify Dashboard**

1. Create an account on [Netlify](https://netlify.com) if you don't have one.

2. Click "New site from Git" and connect your repository.

3. Configure the build settings:
   - Build command: `npm run build` or `yarn build`
   - Publish directory: `dist`

4. Click "Deploy site".

#### Netlify Forms

Portfolio Pro includes a contact form that can be easily integrated with Netlify Forms:

1. Add the `netlify` attribute to your form in `src/components/sections/contact.jsx`:

```jsx
<form 
  onSubmit={form.handleSubmit(onSubmit)} 
  className="space-y-6"
  name="contact"
  netlify
>
```

2. Update the `onSubmit` function to use Netlify Forms:

```jsx
function onSubmit(values) {
  setIsSubmitting(true);
  
  const formData = new FormData();
  Object.entries(values).forEach(([key, value]) => {
    formData.append(key, value);
  });
  
  fetch('/', {
    method: 'POST',
    headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
    body: new URLSearchParams(formData).toString(),
  })
    .then(() => {
      toast({
        title: "Message sent!",
        description: "Thank you for your message. I'll get back to you soon.",
      });
      form.reset();
    })
    .catch((error) => {
      console.error('Error:', error);
      toast({
        title: "Error",
        description: "There was a problem sending your message. Please try again.",
        variant: "destructive",
      });
    })
    .finally(() => {
      setIsSubmitting(false);
    });
}
```

### Vercel

Vercel is a cloud platform for static sites and serverless functions, optimized for frontend frameworks.

#### Deploying to Vercel

**Option 1: Vercel CLI**

1. Install the Vercel CLI:

```bash
npm install -g vercel
```

2. Login to your Vercel account:

```bash
vercel login
```

3. Deploy your site:

```bash
vercel
```

4. For production deployment:

```bash
vercel --prod
```

**Option 2: Vercel Dashboard**

1. Create an account on [Vercel](https://vercel.com) if you don't have one.

2. Click "New Project" and import your repository.

3. Configure the build settings:
   - Framework Preset: Vite
   - Build Command: `npm run build` or `yarn build`
   - Output Directory: `dist`

4. Click "Deploy".

### GitHub Pages

GitHub Pages is a static site hosting service that takes files directly from a GitHub repository.

#### Deploying to GitHub Pages

1. Update `vite.config.js` with your repository name:

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import path from 'path'

export default defineConfig({
  plugins: [react()],
  base: '/your-repo-name/', // Replace with your repository name
  resolve: {
    alias: {
      '@': path.resolve(__dirname, './src'),
    },
  },
})
```

2. Create a `.github/workflows/deploy.yml` file for GitHub Actions:

```yml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
        
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 16
          
      - name: Install dependencies
        run: npm ci
        
      - name: Build
        run: npm run build
        
      - name: Deploy
        uses: JamesIves/github-pages-deploy-action@v4
        with:
          folder: dist
          branch: gh-pages
```

3. Push the changes to your GitHub repository:

```bash
git add .
git commit -m "Configure GitHub Pages deployment"
git push
```

4. GitHub Actions will automatically build and deploy your site to GitHub Pages.

5. Your site will be available at `https://yourusername.github.io/your-repo-name/`.

### Firebase Hosting

Firebase Hosting provides fast and secure hosting for your web app, static and dynamic content, and microservices.

#### Deploying to Firebase Hosting

1. Install the Firebase CLI:

```bash
npm install -g firebase-tools
```

2. Login to your Firebase account:

```bash
firebase login
```

3. Initialize your project:

```bash
firebase init hosting
```

4. Follow the prompts:
   - Select your Firebase project
   - Specify `dist` as your public directory
   - Configure as a single-page app: Yes
   - Set up automatic builds and deploys with GitHub: No (unless you want to)

5. Build your project:

```bash
npm run build
```

6. Deploy to Firebase:

```bash
firebase deploy --only hosting
```

### AWS Amplify

AWS Amplify is a set of tools and services that enables mobile and front-end web developers to build secure, scalable full-stack applications.

#### Deploying to AWS Amplify

1. Install the AWS Amplify CLI:

```bash
npm install -g @aws-amplify/cli
```

2. Configure the Amplify CLI:

```bash
amplify configure
```

3. Initialize your project:

```bash
amplify init
```

4. Add hosting:

```bash
amplify add hosting
```

5. Choose "Amazon CloudFront and S3" for hosting type.

6. Deploy your site:

```bash
amplify publish
```

## Custom Domain Setup

### Netlify Custom Domain

1. Go to your Netlify site dashboard.
2. Click "Domain settings" or "Set up a custom domain".
3. Enter your domain name and click "Verify".
4. Follow the instructions to configure your DNS settings.

### Vercel Custom Domain

1. Go to your Vercel project dashboard.
2. Click "Settings" > "Domains".
3. Enter your domain name and click "Add".
4. Follow the instructions to configure your DNS settings.

### GitHub Pages Custom Domain

1. Go to your GitHub repository.
2. Click "Settings" > "Pages".
3. Under "Custom domain", enter your domain name and click "Save".
4. Create a `CNAME` file in the `public` directory with your domain name:

```
yourdomain.com
```

5. Configure your DNS settings as instructed by GitHub.

### General DNS Configuration

For most custom domains, you'll need to configure your DNS settings with your domain registrar:

1. **A Record**: Point your root domain to your hosting provider's IP address.
2. **CNAME Record**: Point your www subdomain to your hosting URL.
3. **TXT Record**: Verify domain ownership (if required).

Example DNS configuration:

| Type  | Name | Value                   |
|-------|------|-------------------------|
| A     | @    | 192.0.2.1               |
| CNAME | www  | yourusername.github.io  |
| TXT   | @    | verification-code       |

## Environment Variables

If your portfolio uses environment variables (e.g., for API keys or service configurations), you'll need to configure them on your hosting platform.

### Netlify Environment Variables

1. Go to your Netlify site dashboard.
2. Click "Site settings" > "Build & deploy" > "Environment".
3. Click "Edit variables" and add your environment variables.

### Vercel Environment Variables

1. Go to your Vercel project dashboard.
2. Click "Settings" > "Environment Variables".
3. Add your environment variables.

### GitHub Pages Environment Variables

For GitHub Pages, environment variables need to be included in your GitHub Actions workflow:

```yml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    env:
      VITE_API_KEY: ${{ secrets.API_KEY }}
    steps:
      # ... rest of your workflow
```

Then, add your secrets in your GitHub repository settings:
1. Go to your GitHub repository.
2. Click "Settings" > "Secrets" > "Actions".
3. Click "New repository secret" and add your secrets.

## Performance Optimization

To ensure your portfolio loads quickly and performs well, consider these optimizations:

### Image Optimization

1. Compress and resize images before adding them to your project.
2. Use modern image formats like WebP.
3. Implement lazy loading for images:

```jsx
<img 
  src="/images/your-image.jpg" 
  alt="Description" 
  loading="lazy" 
  className="..."
/>
```

### Code Splitting

Vite automatically handles code splitting, but you can optimize it further by using dynamic imports for large components:

```jsx
import React, { lazy, Suspense } from 'react';

const LargeComponent = lazy(() => import('./components/LargeComponent'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LargeComponent />
    </Suspense>
  );
}
```

### Preloading Critical Assets

Add preload links for critical assets in your `index.html`:

```html
<link rel="preload" href="/fonts/your-font.woff2" as="font" type="font/woff2" crossorigin>
<link rel="preload" href="/images/hero-image.jpg" as="image">
```

### Caching Strategies

Configure caching headers for your assets to improve load times for returning visitors:

**Netlify**

Create a `netlify.toml` file in your project root:

```toml
[[headers]]
  for = "/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/index.html"
  [headers.values]
    Cache-Control = "public, max-age=0, must-revalidate"
```

**Vercel**

Create a `vercel.json` file in your project root:

```json
{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=31536000, immutable"
        }
      ]
    },
    {
      "source": "/index.html",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=0, must-revalidate"
        }
      ]
    }
  ]
}
```

## Troubleshooting

### Common Deployment Issues

#### 404 Errors on Page Refresh

If you're experiencing 404 errors when refreshing pages, you need to configure your hosting provider to handle client-side routing:

**Netlify**

Create a `_redirects` file in the `public` directory:

```
/* /index.html 200
```

**Vercel**

Vercel handles this automatically for most frameworks.

**GitHub Pages**

Create a `404.html` file in the `public` directory that redirects to your index.html:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Redirecting...</title>
  <script>
    sessionStorage.redirect = location.href;
  </script>
  <meta http-equiv="refresh" content="0;URL='/'">
</head>
<body>
</body>
</html>
```

Then add this script to your `index.html`:

```html
<script>
  (function() {
    var redirect = sessionStorage.redirect;
    delete sessionStorage.redirect;
    if (redirect && redirect !== location.href) {
      history.replaceState(null, null, redirect);
    }
  })();
</script>
```

#### Build Failures

If your build is failing, check the following:

1. Ensure all dependencies are correctly installed.
2. Check for any syntax errors or import issues.
3. Verify that your environment variables are correctly set.
4. Look at the build logs for specific error messages.

#### Missing Assets

If assets like images or fonts are missing:

1. Check that the paths are correct and use relative paths.
2. Ensure the assets are in the correct directory (usually `public`).
3. Verify that the assets are being included in the build.

#### Performance Issues

If your site is loading slowly:

1. Run a Lighthouse audit to identify performance bottlenecks.
2. Optimize images and other assets.
3. Implement code splitting and lazy loading.
4. Consider using a CDN for faster content delivery.

This completes the deployment guide for Portfolio Pro. By following these instructions, you can deploy your portfolio to various hosting platforms and ensure it performs well for your visitors.