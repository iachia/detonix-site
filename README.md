# detonix.app

Public pages of Detonix: support and privacy policy, in Italian (root) and English (`en/`).

The files in `public/` are generated, do not edit them by hand. They come from the app's own
strings in the private Detonix repository (`pnpm site`, ADR-0023), so the policy on the web and
the one inside the app always say the same thing.

## Publishing

`public/` is served on https://detonix.app/ by a static-assets-only Cloudflare Worker named
`detonix-site` (`wrangler.jsonc`). Nothing deploys on push yet: after a change to `public/` lands on
`main`, deploy it from the repository root with

```sh
npx wrangler@4.156.0 deploy
```

with `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` set in the environment. The token needs
Workers Scripts edit on the account; the custom domain is attached once, outside this command.
