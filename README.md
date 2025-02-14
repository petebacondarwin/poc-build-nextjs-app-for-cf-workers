# [POC] Build Next.js app for cf workers

This monorepo includes a POC to see if it is possible to get a Next.js application built via `next build` (in standalone mode) to run in the Cloudflare workerd runtime.

> [!NOTE]
> The code here is built based on the amazing work done by @mhart in https://github.com/mhart/nextjs-commerce

## The repository

The repository contains two directories:

- `nextjs-worker-builder` containing a package that can be used to build Cloudflare workers compatible output from Next.js applications
- `next-apps` containing Next.js application that use the above mentioned builder (currently it only contains `api-nodejs-hello-world`)

## How to try out/develop in the repository

Install the dependencies:

```sh
pnpm i
```

build the worker with:

```sh
pnpm --filter nextjs-worker-builder build
```

or in watch mode with:

```sh
pnpm --filter nextjs-worker-builder build:watch
```

build and preview the worker for the `api-nodejs-hello-world` application:

```sh
pnpm --filter api-nodejs-hello-world preview:worker
```

> [!WARNING]
> In the `nextjs-worker-builder/src/build/build-worker/index.ts` file there are absolute filesystem paths (starting with `/Users/dario/Desktop/`)
> these clearly need to be removed, for now replace them with your respective absolute file paths.
