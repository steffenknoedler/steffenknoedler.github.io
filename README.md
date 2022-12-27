# assets-for-api-docs

This repo is used to host and serve static assets in support of
[docs.flutter.dev](https://docs.flutter.dev), as well as some manual tests that use
specially-crafted graphics.

Assets committed to this repo and pushed to GitHub are immediately
available for linking and reference.

## Adding new assets

In accordance with the [Flutter style guide](https://github.com/flutter/flutter/wiki/Style-guide-for-Flutter-repo#provide-illustrations-diagrams-or-screenshots),
assets submitted to this repository should be easily reproducible, e.g. by
running a Flutter app or a script. This makes it easier to update the asset in
the future, if needed. Check the existing diagrams (and their generation code)
in this repository to see examples. Avoid checking in just a static image file
(e.g. PNG, JPEG), without a way to regenerate and update it.

## URL structure

Reference the assets with this URL structure:

`https://flutter.github.io/assets-for-api-docs/assets/<library>/<asset>`

For example, an image named `app_bar.png` about `AppBar` from the
material library would go in the `assets/material/` directory and be at
`https://flutter.github.io/assets-for-api-docs/assets/material/app_bar.png`.

All asset files should be under the `assets` directory in an appropriate
subdirectory.

### Prerequisites

The `generate.dart` script works on macOS, Linux, and Windows, but it needs several prerequisites in order to run. On
Linux and macOS run `bin/generate`. On Windows, run `bin\generate.bat`.

To optimize PNG files, it needs `optipng`, which is available for macOS via Homebrew, and Linux via
apt-get, and Windows from the [optipng website](http://optipng.sourceforge.net/).

To convert animations into mp4 files, it needs `ffmpeg`, available for macOS via Homebrew and Linux
via apt-get, and for Windows from the [FFMPEG website](https://ffmpeg.org/download.html).

Both `optipng` and `ffmpeg` need to be in your path when you run the generate script.

`flutter`, `dart` (and when using an Android device, `adb`) commands also need to be available
in a directory in the `PATH` environment variable. (e.g. `PATH=~/<path_to_flutter>/flutter/bin/cache/dart-sdk/bin:~/Android/Sdk/platform-tools:$PATH`)

When using an Android device, be sure that the  `adb` command is the same as the one running
as a server (which is often started by your IDE, so use the same `adb` the IDE is running).

You cannot currently generate docs on an iOS device (although you can generate them on macOS).

## Optimization

Please consider optimization tools for assets.

For PNGs, we recommend `optipng`, using the following command line:

```bash
optipng -zc1-9 -zm1-9 -zs0-3 -f0-5 *.png
```

Be careful about applying this aggressively. In particular, files in
the `assets/tests` directory should not be optimized.

The automatic generation tool will automatically apply optimization to
the assets it generates.

## Issues

Please file any issues in the [main flutter repo](https://github.com/flutter/flutter/issues/new).

