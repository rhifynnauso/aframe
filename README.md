# A-Frame Core

![travis](https://travis-ci.org/aframevr/aframe-core.svg)

> There are currently plans for this repository to be the canonical [`aframe`](https://github.com/aframevr/aframe).

A-Frame is a library for creating virtual reality web experiences.

- **Virtual Reality**: Drop in the library and have a WebVR scene within a few lines of markup.
- **Based on the DOM**: Manipulate with JavaScript, use with your favorite [libraries and frameworks](https://github.com/aframevr/awesome-aframe).
- **[Entity-Component System](https://aframe.io/docs/core/)**: Use the entity-component system for better composability and flexibility.

Find out more:

- [Guide](https://aframe.io/docs/guide/)
- [Docs](https://aframe.io/docs/core/)
- [Examples](https://aframe.io/examples/)

### Usage

Install from npm:

    npm install aframe-core

Then require:

    require('aframe-core');

## Local Installation and Development

To work locally:

    git clone https://github.com/aframevr/aframe-core.git
    cd aframe-core
    npm install

To start the local development server:

    npm start

And fire up __[http://localhost:9001](http://localhost:9001)__!

### Running Tests

After [cloning and installing](#local-installation-and-development), to run tests:

    npm test

## Browser Console Logging

To see helpful logs, warnings, and errors, enable logging from the console of your favorite developer tools:

    localStorage.logs = 1

To disable:

    localStorage.logs = 0

## Maintainers

Ensure you have [cloned the repo and installed the dependencies](#local-installation-and-development).

### Developing Alongside Projects

While making changes to `aframe-core` and testing with another project, link the projects together.

#### Linking

When you are in the directory of your __`aframe-core`__ repo checkout:

    npm link

When you are in the directory of your __`aframe`__ repo checkout:

    npm link aframe-core

#### Unlinking

`npm unlink` when you are done testing things and want to use the npm-published versions, not your versions that are locally linked.

From your __`aframe-core`__ directory:

    npm unlink

From your __`aframe`__ directory:

    npm unlink aframe-core

### Publishing to [npm](https://www.npmjs.com/)

To increment the preminor version of the package (e.g., `0.1.19` to `0.1.20`) and create a git tag (e.g., `v0.1.20`):

    npm run release:bump

___NOTE:___ npm versions __cannot__ be unpublished.

Once the package is 100% ready to go, to push the new version to npm (e.g., `0.1.20`) and to the new tag to GitHub (e.g., `v0.1.20`):

    npm run release:push

## Updating `dist` Files

    npm run dist
    git commit -am 'Bump dist'

## Publishing to GitHub Pages

To publish to __https://aframevr.github.io/aframe-core/__:

    npm run ghpages

To publish to __https://your_username.github.io/aframe-core/__:

    npm run ghpages your_username

## License

This program is free software and is distributed under an [MIT License](LICENSE).
