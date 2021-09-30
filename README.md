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
