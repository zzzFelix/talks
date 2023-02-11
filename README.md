# slidev-monorepo

A template for a Turborepo with multiple slidev presentations that share dependencies.

## Install

`npm install`

## Build

`npm run build`

## Deploy

Use Vercel, Netlify, or other services to deploy the `dist` directory that contains the static apps.

## Preview

Go to an individual talk in the `/apps` directory and run:

 `npm run dev`

You can also run the command from the root directory—Turborepo will start the dev servers of all talks. Make sure to use different ports. `talk1` and `talk2` run on ports `3030` and `3040` by default.

## Demo

[https://slidev-monorepo-zzzfelix.vercel.app/talk1](https://slidev-monorepo-zzzfelix.vercel.app/talk1)

[https://slidev-monorepo-zzzfelix.vercel.app/talk2](https://slidev-monorepo-zzzfelix.vercel.app/talk2)