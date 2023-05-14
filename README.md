# test-nextjs-chrome-extension

- nextjs로 chrome-extension 개발 테스트

## How to create a Chrome extension with Next.js

- `npx create-next-app@latest --experimental`
  - project name : test-nextjs-chrome-extension
  - option은 알아서 하고싶은데로...
    - Typescript : No
    - ESLint : No
    - Tailwind CSS : No
    - src/ directory : No
    - App Router : No
    - import alias : No
- `cd test-nextjs-chrome-extension`
- `npm install --save-dev @types/chrome`
- write `public/manifest.json`

```
{
  "name": "Next.js Chrome Extension Test",
  "description": "just for test",
  "version": "1.0",
  "manifest_version": 3,
  "action": {
    "default_title": "Next.js Browser Extension Demo",
    "default_popup": "index.html"
  }
}
```

- add `images.unoptimized=true` to next.config.js

```
/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
  images: {
    unoptimized: true,
  },
};

module.exports = nextConfig;
```

- modify `styles/globals.css`
  - addd `html, body { max-width: 500 }`
- `npx next build`
- `npx next export`
- `mv ./out/_next ./out/next && cd ./out && grep -rli '_next' * | xargs -I@ sed -i '' 's|/_next|/next|g' @;`
- import `out` directory to chrome://extensions

## development

- develop something
- `npx next build`
- `npx next export`
- `mv ./out/_next ./out/next && cd ./out && grep -rli '_next' * | xargs -I@ sed -i '' 's|/_next|/next|g' @;`

---

This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.js`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
