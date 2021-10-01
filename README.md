# material-ui course with Next.js

https://www.udemy.com/course/implement-high-fidelity-designs-with-material-ui-and-reactjs/

## How to use

Download the example [or clone the repo](https://github.com/mui-org/material-ui):

```sh
curl https://codeload.github.com/mui-org/material-ui/tar.gz/master | tar -xz --strip=2  material-ui-master/examples/nextjs
cd nextjs
```

Install it and run:

```sh
npm install
npm run dev
```

## Fix issue
- replace justifyContent= by justifyContent=  (Grid component props renaming)
- rename import { createMuiTheme } from "@material-ui/core/styles"; into import { createTheme } from "@material-ui/core/styles";
- next.config.js : Since version 10.0.0, Next.js has a built-in Image Component and Automatic Image Optimization
https://stackoverflow.com/questions/68008498/nextjs-typeerror-unsupported-file-type-undefined-after-update-to-v-11
https://maxrohde.com/2021/07/25/next-js-11-images-with-static-export/
--> yarn add next-optimized-images file-loader img-loader url-loader ignore-loader extracted-loader next-compose-plugins
--> remove its content:

    ```const withPlugins = require("next-compose-plugins");
    const optimizedImages = require("next-optimized-images");

    module.exports = withPlugins([
    [
        optimizedImages,
        {
        /* config for next-optimized-images */
        }
    ]

    // your other plugins here
    ]);```

--> Replace with

```/* eslint-disable @typescript-eslint/no-var-requires */
/* eslint-disable @typescript-eslint/no-unused-vars */
/* eslint-disable @typescript-eslint/explicit-function-return-type */
const withPlugins = require('next-compose-plugins');
const optimizedImages = require('next-optimized-images');

const nextConfig = {
  webpack: (config, options) => {
    return config;
  },
  eslint: {
    // ESLint managed on the workspace level
    ignoreDuringBuilds: true,
  },
  images: {
    disableStaticImages: true,
  },
};

const config = withPlugins(
  [
    [
      optimizedImages,
      {
        // optimisation disabled by default, to enable check https://github.com/cyrilwanner/next-optimized-images
        optimizeImages: false,
      },
    ],
  ],
  nextConfig
);

module.exports = config;```

- update _document.js : replace html tag by Html tag 
- move meta view port from _document.js into _app.js
- fix Header.js > route.seleselectedIndex  --> route.selectedIndex
