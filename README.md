[![Website](https://img.shields.io/badge/dmtn--302-lsst.io-brightgreen.svg)](https://dmtn-302.lsst.io)
[![CI](https://github.com/lsst-dm/dmtn-302/actions/workflows/ci.yaml/badge.svg)](https://github.com/lsst-dm/dmtn-302/actions/workflows/ci.yaml)

# IVOA Identifier Usage at the Rubin Observatory

## DMTN-302

The IVOA define a standard URI scheme to reference individual datasets. In this document we will define how these IVOA Identifiers will be formed for Butler datasets and possibly object catalog IDs.

**Links:**

- Publication URL: https://dmtn-302.lsst.io
- Alternative editions: https://dmtn-302.lsst.io/v
- GitHub repository: https://github.com/lsst-dm/dmtn-302
- Build system: https://github.com/lsst-dm/dmtn-302/actions/


## Build this technical note

You can clone this repository and build the technote locally if your system has Python 3.11 or later:

```sh
git clone https://github.com/lsst-dm/dmtn-302
cd dmtn-302
make init
make html
```

Repeat the `make html` command to rebuild the technote after making changes.
If you need to delete any intermediate files for a clean build, run `make clean`.

The built technote is located at `_build/html/index.html`.

## Publishing changes to the web

This technote is published to https://dmtn-302.lsst.io whenever you push changes to the `main` branch on GitHub.
When you push changes to a another branch, a preview of the technote is published to https://dmtn-302.lsst.io/v.

## Editing this technical note

The main content of this technote is in `index.md` (a Markdown file parsed as [CommonMark/MyST](https://myst-parser.readthedocs.io/en/latest/index.html)).
Metadata and configuration is in the `technote.toml` file.
For guidance on creating content and information about specifying metadata and configuration, see the Documenteer documentation: https://documenteer.lsst.io/technotes.
