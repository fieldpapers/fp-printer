# Field Papers Printer

This repository contains (or will) Field Papers' atlas creation pipeline.

This pipeline involves outputting an atlas-specific HTML page containing page
breaks (as appropriate), intended for output as a PDF using
[wk\<html\>topdf](http://wkhtmltopdf.org/).

## Installation

[Install `wkhtmltopdf`.](http://wkhtmltopdf.org/downloads.html) The OS
X installer unfortunate side-effect of resetting permissions on some folders
within `/usr/local` (if you're using Homebrew).

## Printing

To create a PDF:

```bash
wkhtmltopdf http://host/path atlas.pdf
```

By default, this will produce A4-sized portrait output. To change the
orientation, use `-O Landscape`. To change the paper size, use `-s Letter`
(etc.).

## High Resolution Map Output

Standard images for the web are 72dpi. Retina images (@2x) are twice that, at
144dpi. Since we're generating output intended for print, we'd like to get to
300dpi if possible. Using standard tiles, we can offset by 2 zoom levels and
shrink the effective image size to 64px (substantially shrinking the size of
features and text). This can be done in Leaflet like so:

```javascript
L.tileLayer("http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
  tileSize: 64,
  zoomOffset: 2
}).addTo(map);
```

Retina tiles (512x512px) can target the same resolution and only offset by
a single zoom:

```javascript
L.tileLayer("http://{s}.tile.stamen.com/toner-lite/{z}/{x}/{y}@2x.png", {
  tileSize: 128,
  zoomOffset: 1
}).addTo(map);
```
