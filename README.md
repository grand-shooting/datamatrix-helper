# DataMatrix Helper

Static web page that reads a GS1 DataMatrix (camera, photo or pasted scanner text),
splits its GS1 Application Identifiers and draws any valid EAN-13 as a scannable barcode.

Live site: https://grand-shooting.github.io/datamatrix-helper/

## How it works

- Everything runs in the browser; no image or frame is uploaded.
- Decoding uses [zxing-wasm](https://github.com/Sec-ant/zxing-wasm) 3.1.4, vendored as
  `zxing-reader.js` + `zxing_reader.wasm` so the site has no runtime CDN dependency
  (only IBM Plex fonts come from Google Fonts).
- On SUL labels, `(91)` is the UID, `(92)` an internal EAN-13 and `(93)` the SKU.

## Deploy

GitHub Pages serves the `main` branch root (`.nojekyll` disables Jekyll).
Live camera scanning needs HTTPS, which Pages provides.

## Updating zxing-wasm

```sh
npm install zxing-wasm@<version>
cp node_modules/zxing-wasm/dist/iife/reader/index.js zxing-reader.js
cp node_modules/zxing-wasm/dist/reader/zxing_reader.wasm .
```

## Licenses

Third-party notices are in [THIRD_PARTY_LICENSES](THIRD_PARTY_LICENSES).
