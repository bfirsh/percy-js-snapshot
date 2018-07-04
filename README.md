# percy-js-snapshot

Percy visual testing for Google Puppeteer.

## Install

```
$ npm install percy-js-snapshot --dev
```

## Usage

```js
import { Percy, FileSystemAssetLoader } from 'percy-js-snapshot';

// Create a Percy client
const percy = new Percy({
    loaders: [
        new FileSystemAssetLoader({
            // Path to find assets that the HTML links to
            buildDir: './dist',
            // A prefix to add to linked assets if they are in a different directory (e.g. /public/)
            mountPath: '/'
        })
    ]
});

// Start a Percy build
await percy.startBuild();

// Generate the HTML you want to snapshot. This might be reading a file from
// disk, or jsdom.serializeDocument(document) on a JSDOM document.
const content = ...;

// Take a snapshot
await percy.snapshot('Snapshot of example.com', '/', content);

// Tell Percy we're finished taking snapshots
await percy.finalizeBuild();
```

# Acknowledgements

This package was originally forked from [percy-puppeteer](https://github.com/GitbookIO/percy-puppeteer), created by [Samy Pessé](https://twitter.com/SamyPesse) from [GitBook](https://www.gitbook.com/). Thank you Samy!
