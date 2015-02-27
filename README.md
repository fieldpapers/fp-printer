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
