---
title: Production
editLink: true
---

# Production

## Building for production

Running the `build` script will generate production-ready assets through Vite. Their linking is handled by the [directives](/guides/development#directives), so no further action is required.

By default, assets are built in `public/build`. If you used Laravel Mix, you may be used to have them generated in `public` directly. With Vite, this isn't directly possible since the build directory is emptied. I believe this restriction is great, as having the assets in their own directory makes it easier to work with them.

You can change the build path in the [configuration](/guide/configuration), but it is best to keep the default, unless you have a specific requirement.

## `ASSET_URL` environment variable

Laravel's default `asset` helper makes use of the `ASSET_URL` environment variable to generate an asset link. This is particularly useful if assets are stored in a cloud-based storage such as S3, which is the case with [Laravel Vapor](https://docs.vapor.build/1.0/projects/deployments.html#assets).

The Vite NPM helper takes the `ASSET_URL` environment variable into account and injects it in Vite's `base` configuration option in order to properly link the assets in production.