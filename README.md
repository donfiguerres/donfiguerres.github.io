# donfiguerres GitHub Pages

This is the repo for my personal website at GitHub Pages.

## Requirements

- Hugo Extended 0.161.1+
- Go 1.23+
- Node.js 20 (see .nvmrc)

## Cloning

```sh
git clone https://github.com/donfiguerres/donfiguerres.github.io.git
cd donfiguerres.github.io
nvm use
hugo mod tidy
hugo mod npm pack
npm ci
```

## TODO

- Dark mode
- Add post
  - How I set up my repo to work on Github Pages
  - Why switch to Hugo
