# detonix.app

Public pages of Detonix and of its second game, Detonix: Gran Finale: support and privacy
policy, in Italian and English.

| Pages | Italian | English | Built by |
| --- | --- | --- | --- |
| Detonix | `/`, `/privacy/` | `/en/`, `/en/privacy/` | `pnpm site` in `iachia/detonix` (ADR-0023 there) |
| Detonix: Gran Finale | `/gran-finale/`, `/gran-finale/privacy/` | `/en/gran-finale/`, `/en/gran-finale/privacy/` | `pnpm site` in `iachia/detonix-gran-finale` (ADR-0025 there) |

The files in `public/` are generated, do not edit them by hand. They come from each app's own
strings, so the policy on the web and the one inside the app always say the same thing. Each
game's builder writes only its own pages: copy its `dist-site/` over `public/`.

## Publishing

`public/` is served on https://detonix.app/ by a static-assets-only Cloudflare Worker named
`detonix-site` (`wrangler.jsonc`). Nothing deploys on push yet: after a change to `public/` lands on
`main`, deploy it from the repository root with

```sh
npx wrangler@4.156.0 deploy
```

with `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` set in the environment. The token needs
Workers Scripts edit on the account; the custom domain is attached once, outside this command.
