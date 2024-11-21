<!-- markdownlint-disable MD033 MD041 -->

<div align="center">

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/S6S8L8OOP)
[![爱发电](https://img.shields.io/badge/%E7%88%B1%E5%8F%91%E7%94%B5_Afdian-946CE6?style=for-the-badge)](https://ifdian.net/a/SharpIce)

</div>

## Usage

### Install

```bash
npm add --save-dev svg-to-vue-loader vue-loader @vue/compiler-sfc # Npm
yarn add -D svg-to-vue-loader vue-loader # Yarn
pnpm add -D svg-to-vue-loader vue-loader # Pnpm
```

### Config

```typescript
// webpack.config.ts
import type webpack from 'webpack';
import vueLoaderPlugin from 'vue-loader/lib/plugin';
import type svgToVueLoaderOptions from 'svg-to-vue-loader/options';

export default {
  // ...
  // support cache
  cache: {
    type: 'filesystem',
  },
  module: {
    rules: [
      {
        test: /\.svg$/,
        use: [
          {
            use: [
              'vue-loader',
              {
                loader: 'svg-to-vue-loader',
                options: {
                  // Your options here
                } satisfies svgToVueLoaderOptions,
              },
            ],
          },
        ],
      },
    ],
  },
  plugins: [new vueLoaderPlugin()],
  // ..
} satisfies webpack.Configuration;
```

or

```javascript
// webpack.config.ts
import vueLoaderPlugin from 'vue-loader/lib/plugin';

/**
 * @type {import('webpack').Configuration}
 */
export default {
  // ...
  // support cache
  cache: {
    type: 'filesystem',
  },
  module: {
    rules: [
      {
        test: /\.svg$/,
        use: [
          {
            loader: 'psvg-to-vue-loader',
            use: [
              'vue-loader',
              {
                loader: 'svg-to-vue-loader',
                /** @type {import('svg-to-vue-loader/options')} */
                options: {
                  // Your options here
                },
              },
            ],
          },
        ],
      },
    ],
  },
  plugins: [new vueLoaderPlugin()],
  // ..
};
```
