# clif

Cross-platform CLI GIF maker based on JS+Web.

![](https://cldup.com/Iu3VmK9SVy.gif)

## Getting started

On OS X, install latest Xcode command line tools, even if you think you already have them:

```
xcode-select --install
```

Then, go through the Apple dialogue to download and install them. Now, you’re ready to install Surge’s version of clif with:

```sh
npm install -g @surge/clif
```

Note, you’ll need to be running npm@2.0.0 or greater to do this. You can check what version you’re using with:

```sh
npm --version
```

…and upgrade with:

```sh
sudo npm install -g npm
```

You can omit `sudo` if you are using Windows.

## How to use

Run

```sh
clif out.gif
```

type `exit` to finish and save the recording.

## Features

- Easy to install: `npm install -g clif`.
- Works on OSX and Linux.
- Small GIFs.
- High quality (anti-aliased fonts).
- Rendered with CSS/JS, customizable.
- Realtime parallel rendering.
- Frame aggregation and customizable FPS.
- Support for titles Terminal.app-style.

## How it works

clif builds mainly on four projects: `child_pty`, `term.js`
`omggif` and `phantomjs`.

`child_pty` is used to spawn a pseudo terminal from
which we can capture the entirety of input and output.

Each frame that's captured is asynchronously sent to
a `phantomjs` headless browser to render using `term.js`
and screenshot.

The GIF is composited with `omggif` and finally written
out to the filesystem.

## Options

```

  Usage: clif [options] <outfile>

  Options:

    -h, --help           output usage information
    -V, --version        output the version number
    -c, --cols <cols>    Cols of the term [90]
    -r, --rows <rows>    Rows of the term [30]
    -s, --shell <shell>  Shell to use [/bin/bash]
    -f, --fps <fps>      Frames per second [8]
    -q, --quality <q>    Frame quality 1-30 (1 = best|slowest) [5]

```

## Contributing

You can edit the styles in `lib/client.js` and the recompiling:

```sh
npm run compile
```

## TODO

- Substitute `phantom` with a terminal rendered on top
  of `node-canvas` or low-level graphic APIs.
  [terminal.js](https://github.com/Gottox/terminal.js) seems like a good
  candidate to add a `<canvas>` adaptor to.
- Should work on Windows with some minor tweaks.
- There's an issue with Node 0.12 and IO.js on Mac
  where stdout sometimes buffers for no reason `¯\_(ツ)_/¯`

## Credits

- Inspired by [KeyboardFire](https://github.com/KeyboardFire)'s [mkcast](https://github.com/KeyboardFire/mkcast).
- Borrows GIF palette neuquant indexing from
  [sole](https://github.com/sole)'s [animated_GIF.js](https://github.com/sole/Animated_GIF).

## License

MIT
