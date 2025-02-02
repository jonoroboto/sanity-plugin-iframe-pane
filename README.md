# sanity-plugin-iframe-pane

> This is a **Sanity Studio v3** plugin.
> For the v2 version, please refer to the [v2-branch](https://github.com/sanity-io/sanity-plugin-iframe-pane/tree/studio-v2).

Display any URL in a View Pane, along with helpful buttons to Copy the URL or open in a new tab.

Accepts either a string or an async function to resolve a URL based on the current document.

![Iframe View Pane](https://user-images.githubusercontent.com/9684022/144389599-496e1e50-62a7-4d5c-903a-889885eb8aab.png)

## Installation

```
npm install --save sanity-plugin-iframe-pane
```

or

```
yarn add sanity-plugin-iframe-pane
```

## Usage

This is designed to be used as a [Component inside of a View](https://www.sanity.io/docs/structure-builder-reference#c0c8284844b7).

```js
// ./src/deskStructure.js
import Iframe from 'sanity-plugin-iframe-pane'

// ...all other list items

S.view
  .component(Iframe)
  .options({
    // Required: Accepts an async function
    url: (doc) => resolveProductionUrl(doc),
    // OR a string
    url: `https://sanity.io`,
    // Optional: Set the default size
    defaultSize: `mobile`, // default `desktop`
    // Optional: Add a reload button, or reload on new document revisions
    reload: {
      button: true, // default `undefined`
      revision: true, // boolean | number. default `undefined`. If a number is provided, add a delay (in ms) before the automatic reload on document revision
    },
    // Optional: Pass attributes to the underlying `iframe` element:
    // See https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe
    attributes: {
      allow: 'fullscreen' // string, optional
      referrerPolicy: 'strict-origin-when-cross-origin' // string, optional
      sandbox: 'allow-same-origin' // string, optional
    }
  })
  .title('Preview')
```

## License

MIT-licensed. See LICENSE.

## Develop & test

This plugin uses [@sanity/plugin-kit](https://github.com/sanity-io/plugin-kit)
with default configuration for build & watch scripts.

See [Testing a plugin in Sanity Studio](https://github.com/sanity-io/plugin-kit#testing-a-plugin-in-sanity-studio)
on how to run this plugin with hotreload in the studio.

### Release new version

Run ["CI & Release" workflow](https://github.com/sanity-io/sanity-plugin-iframe-pane/actions/workflows/main.yml).
Make sure to select the studio-v3 branch and check "Release new version".

Semantic release will only release on configured branches, so it is safe to run release on any branch.
