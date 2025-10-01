# FRN Store Theme

FRN Cubo's VTEX IO store theme used to power frncubo.store. It extends the VTEX Store Framework with custom PDP blocks and FRN-specific experiences while keeping compatibility with standard VTEX apps.

## Prerequisites

- Node.js LTS compatible with VTEX IO tooling
- Yarn 1.x
- VTEX IO Toolbelt (`vtex` CLI) authenticated in the target account

## Getting Started

1. Clone this repository and install dependencies.
   ```bash
   yarn
   ```
2. Log into VTEX and pick a development workspace.
   ```bash
   vtex login <account>
   vtex use <workspace>
   ```
3. Link the app to see it live in your workspace.
   ```bash
   vtex link
   ```
4. Navigate to `<workspace>--<account>.myvtex.com` to validate the storefront.

## Deploying

- Promote changes once validated: `vtex workspace promote`.
- Publish a new release when ready for production: `vtex deploy` or bump the version and run `vtex publish`.
- Keep the `CHANGELOG.md` aligned with the version declared in `manifest.json`.

## App Structure

- `manifest.json`: app metadata, builders, and dependencies.
- `store/blocks/`: VTEX Store Framework block trees (Home, PDP, minicart, etc.).
- `styles/`: global CSS and tokens consumed by the blocks.
- `docs/`: internal documentation and assets.

## Custom Blocks

This theme depends on `frncubo.frn-components`. Blocks exposed by that app can be referenced using the `vendor.app:block` syntax. For example, the PDP loads the custom block `frncubo.frn-components:teste` alongside standard VTEX blocks.

If a build fails with *"I couldn't find a block"*, confirm that:

- The dependency exposing the block is declared in `manifest.json`.
- The block ID matches the key defined in the dependency's `store` folder.
- You have the dependency installed or linked in the current workspace (`vtex deps list`).

## Customization

- Use [VTEX Site Editor](https://developers.vtex.com/docs/guides/site-editor-overview) for content-driven sections.
- Extend or override CSS handles in `styles/css` to change layout and look and feel.
- Add new blocks under `store/blocks` and reference them from your routes (`store/routes.json`).
- For reusable logic, publish it as part of `frncubo.frn-components` and consume it here.

## Troubleshooting

- **Link errors**: run `vtex whoami` to ensure the session is active, then retry `vtex link`.
- **Missing blocks**: check the dependency version and confirm the block exists in the source app.
- **CSS collisions**: the builder hub warns about duplicate CSS entries; prefer scoping styles with handles to avoid overrides.

## Useful Resources

- [Store Framework documentation](https://developers.vtex.com/docs/guides/store-framework-overview)
- [VTEX IO CLI reference](https://developers.vtex.com/docs/guides/vtex-io-documentation-toolbelt-commands)
- [VTEX Component Catalog](https://developers.vtex.com/docs/guides/store-framework-components)

