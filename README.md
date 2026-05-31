# myanmar-script

Utilities and LaTeX package for typesetting Myanmar (Burmese) script.

## Overview

This repository provides a small LaTeX package and documentation to help typeset
Myanmar (Burmese) text in XeLaTeX and LuaLaTeX. The package offers font helpers,
numeral conversion, and basic localization hooks.

## Contents

- `myanmar-script.dtx` — documented source (docstrip + package implementation)
- `myanmar-script.sty` — package file generated from the `.dtx`
- `myanmar.sty` — an alternative package wrapper
- `docs/manual.tex` — longer manual source for the package
- `examples/` — example documents demonstrating usage

## Requirements

- XeLaTeX or LuaLaTeX (XeTeX recommended for font support)
- latexmk (recommended) or your preferred TeX build tool
- A modern TeX distribution (MiKTeX or TeX Live) with `fontspec` and `expl3`

## Build documentation

To build the package documentation (PDF) using the provided driver, run:

```bash
latexmk -xelatex myanmar-script.tex
```

If you prefer to build directly from the `.dtx`, you can run:

```bash
latexmk -xelatex myanmar-script.dtx
```

Note: The `.dtx` is both the documented source and the implementation. If you
encounter docstrip errors during build, try the driver `myanmar-script.tex`.

## Usage

In your document preamble:

```latex
\usepackage{myanmar-script}
% then use the provided commands/environments (see the manual)
```

Check `examples/example.tex` for a minimal usage example.

## Contributing

Contributions and bug reports are welcome. Please open issues or pull
requests describing the change and how to reproduce any problems.

## License

This project is released under the terms of the included `LICENSE` file.

## Contact

For questions, open an issue or contact the maintainer via the repository.
# The `myanmar-script` Package

`myanmar-script` is a small LaTeX package that provides helpers for Unicode
Myanmar-script typesetting with XeLaTeX and LuaLaTeX. Its scope is intentionally
limited: font selection, simple inline/block text wrappers, digit conversion,
and a basic Burmese localization hook.

The package is written as a documented LaTeX source package. The main source is
`myanmar.dtx`, and `myanmar.ins` extracts the generated `myanmar-script.sty` file with
DocStrip.

## Status

This package is deliberately minimal. It focuses on basic font handling and
small utilities for Burmese (Myanmar) text. More advanced language- or
typography-specific features are not implemented in this release.

## Features

- Unicode-first Myanmar (Burmese) text input.
- XeLaTeX and LuaLaTeX support through `fontspec`.
- Engine check that stops compilation under pdfLaTeX.
- Built-in font choices for common Myanmar fonts.
- Inline command for short Myanmar text.
- Environment for paragraph or block Myanmar text.
- Arabic digit to Myanmar digit conversion (simple replacement).
- Basic Burmese names for a few LaTeX document strings.
- DocStrip package layout with `myanmar.dtx` and `myanmar.ins`.

## Requirements

You need a modern TeX distribution such as MiKTeX or TeX Live with:

- LaTeX2e
- `expl3`
- `l3keys2e`
- `iftex`
- `xparse`
- `fontspec`
- XeLaTeX or LuaLaTeX

You also need at least one supported Myanmar font installed on your system.

Supported package font options are:

- `font=noto` for `Noto Sans Myanmar`
- `font=pyidaungsu` for `Pyidaungsu`
- `font=myanmartext` for `Myanmar Text`
- `font=myanmar-text` for `Myanmar Text` (alias)
- `font=padauk` for `Padauk`
- `font=tharlon` for `Tharlon`

The default is `font=noto`.

## Important Engine Note

This package does not support pdfLaTeX. Myanmar shaping requires a Unicode
engine and OpenType font handling.

Use one of:

```sh
xelatex file.tex
lualatex file.tex
```

If you use LaTeX Workshop in VS Code, configure the project to use XeLaTeX or
LuaLaTeX. A local `latexmkrc` can force `latexmk` to use XeLaTeX:

```perl
$pdf_mode = 5;
$pdflatex = 'xelatex -interaction=nonstopmode -halt-on-error %O %S';
$xelatex = 'xelatex -interaction=nonstopmode -halt-on-error %O %S';
```

## Repository Layout

```text
myanmar/
|-- README.md
|-- LICENSE
|-- .gitignore
|-- latexmkrc
|-- myanmar.dtx
|-- myanmar.ins
|-- myanmar-script.sty
|-- .github/
|   |-- .github.code-workspace
|   `-- FUNDING.yml
|-- docs/
|   |-- manual.tex
|   `-- manual.pdf
|-- examples/
|   `-- example.tex
`-- source/
```

File roles:

- `README.md` is this guide.
- `LICENSE` contains the repository license.
- `.gitignore` excludes generated LaTeX build files.
- `latexmkrc` configures `latexmk` to use XeLaTeX.
- `myanmar.dtx` is the documented package source.
- `myanmar.ins` extracts `myanmar-script.sty` from `myanmar.dtx`.
- `myanmar-script.sty` is the generated package file used by LaTeX documents.
- `.github/` contains repository metadata.
- `docs/manual.tex` is a standalone manual source.
- `docs/manual.pdf` is the generated manual PDF.
- `examples/example.tex` is a small usage example.
- `source/` is reserved for future font, language, mapping, or data files.

## Installation

From the package directory, extract the package file:

```sh
latex myanmar.ins
```

This generates:

```text
myanmar-script.sty
```

For local testing, keep `myanmar-script.sty` beside the document you are compiling, or
compile from this repository root so TeX can find it.

For a user-level installation, copy the generated `myanmar-script.sty` into a local
TeX tree. For example:

```text
texmf/tex/latex/myanmar-script/myanmar-script.sty
```

Then refresh the filename database if your TeX distribution requires it.

## Basic Usage

```tex
% !TeX program = xelatex
\documentclass{article}

\usepackage[font=noto, language=burmese]{myanmar-script}

\begin{document}

English text.

\textmyanmar{မြန်မာစာ}

\begin{myanmar}
မြန်မာစာ စမ်းသပ်ခြင်း။
\end{myanmar}

Myanmar number: \myanmarnumber{2026}

\end{document}
```

Compile with:

```sh
xelatex your-file.tex
```

or:

```sh
lualatex your-file.tex
```

## Package Options

Options are passed with key-value syntax:

```tex
\usepackage[font=noto, language=burmese]{myanmar}
```

### `font`

Selects the Myanmar font family.

```tex
\usepackage[font=noto]{myanmar-script}
\usepackage[font=pyidaungsu]{myanmar-script}
\usepackage[font=myanmartext]{myanmar-script}
\usepackage[font=myanmar-text]{myanmar-script}
\usepackage[font=padauk]{myanmar-script}
\usepackage[font=tharlon]{myanmar-script}
```

Available values:

| Value | Font name |
| --- | --- |
| `noto` | `Noto Sans Myanmar` |
| `pyidaungsu` | `Pyidaungsu` |
| `myanmartext` | `Myanmar Text` |
| `myanmar-text` | `Myanmar Text` |
| `padauk` | `Padauk` |
| `tharlon` | `Tharlon` |

Default:

```tex
font=noto
```

### `language`

This package currently only implements a `language=burmese` localization
hook. Other language-specific behavior is not implemented in this release and
the package does not claim full support for Shan, Mon, S'gaw Karen, or other
Myanmar-script variants.

Default:

```tex
language=burmese
```

## Commands

### `\textmyanmar{...}`

Typesets short inline Myanmar text with the selected Myanmar font.

```tex
This is inline Myanmar: \textmyanmar{မြန်မာစာ}.
```

Use this command inside English paragraphs, headings, captions, table cells, and
other short text runs.

### `myanmar` environment

Typesets a block of Myanmar text with the selected Myanmar font.

```tex
\begin{myanmar}
မြန်မာစာသည် မြန်မာနိုင်ငံ၏ ရုံးသုံးဘာသာစကားဖြစ်သည်။
\end{myanmar}
```

Use this for paragraphs or longer blocks where the whole region should use the
Myanmar font.

### `\myanmarnumber{...}`

Converts Arabic digits in the argument to Myanmar digits.

```tex
\myanmarnumber{2026}
```

Expected output:

```text
၂၀၂၆
```

The current implementation performs a direct digit replacement for `0` through
`9`. Non-digit text is not specially parsed.

## Localization

If `language=burmese` is selected, the package defines basic Burmese names for
a small set of common LaTeX document strings (e.g. `\contentsname`,
`\figurename`). This is intentionally limited and not a full localization
package.

## Example Document

The repository includes:

```text
examples/example.tex
```

Build it from the repository root with:

```sh
latexmk examples/example.tex
```

or directly with XeLaTeX:

```sh
xelatex examples/example.tex
```

If `latexmkrc` is present, `latexmk` should use XeLaTeX automatically.

## Generating Documentation

The package source is documented in `myanmar.dtx`. After extracting
`myanmar-script.sty`, generate the package documentation with XeLaTeX:

```sh
latex myanmar.ins
xelatex myanmar.dtx
```

For cross-references and index data, you may need additional runs:

```sh
xelatex myanmar.dtx
makeindex -s gind.ist myanmar.idx
makeindex -s gglo.ist -o myanmar.gls myanmar.glo
xelatex myanmar.dtx
xelatex myanmar.dtx
```

## Development Workflow

Edit the documented source:

```text
myanmar.dtx
```

Regenerate the package:

```sh
latex myanmar.ins
```

Test the example:

```sh
latexmk examples/example.tex
```

Clean generated files when needed:

```sh
latexmk -C examples/example.tex
```

If auxiliary files were created in the repository root, remove them with your
editor's cleanup command or with a shell cleanup command appropriate for your
platform.

## Troubleshooting

### `The myanmar package requires XeLaTeX or LuaLaTeX`

You are compiling with pdfLaTeX. Change your engine to XeLaTeX or LuaLaTeX.

For direct compilation:

```sh
xelatex file.tex
```

For `latexmk`:

```sh
latexmk -xelatex file.tex
```

### `fontspec` errors

`fontspec` only works with XeLaTeX and LuaLaTeX. If you see a `fontspec` error
under pdfLaTeX, switch engines.

### Font not found

Install the selected font, or choose another package font option.

```tex
\usepackage[font=pyidaungsu]{myanmar}
```

On Windows, after installing a new font, restart your editor or terminal so the
TeX engine can see the updated system font list.

### Myanmar text appears as boxes

The selected font may not contain Myanmar glyphs, or the document may not be
using the package command/environment for Myanmar text. Try a known Myanmar font
such as `Noto Sans Myanmar`, `Pyidaungsu`, `Myanmar Text`, `Padauk`, or
`Tharlon`.

### Myanmar shaping looks wrong

Use XeLaTeX or LuaLaTeX and an OpenType Myanmar font with proper shaping support.
For LuaLaTeX, the package requests HarfBuzz rendering. XeLaTeX may report a
warning that the HarfBuzz renderer option is LuaTeX-only; that warning is
expected and does not stop compilation.

### LaTeX Workshop keeps using pdfLaTeX

Select a XeLaTeX recipe in VS Code, or add a project `.vscode/settings.json`
that uses `latexmk -xelatex`. You can also keep the magic comment at the top of
your document:

```tex
% !TeX program = xelatex
```

### `Nothing to do` after a failed build

`latexmk` may be remembering an older failed run. Clean auxiliary files and
rebuild:

```sh
latexmk -C examples/example.tex
latexmk examples/example.tex
```

## Known Limitations

- The package currently exposes five named font choices, plus the
  `myanmar-text` alias for `myanmartext`.
- Language-specific behavior for Shan, Mon, and S'gaw Karen is not yet fully
  implemented.
- Numeral conversion is a simple digit replacement.
- Localization is currently basic and focused on Burmese.
- The package does not yet provide line breaking, hyphenation, or dictionary
  support for Myanmar languages.

## License

This repository is released under the MIT License. See `LICENSE` for the full
license text.

## Minimal Test

Use this document to check that your setup works:

```tex
% !TeX program = xelatex
\documentclass{article}
\usepackage[font=noto, language=burmese]{myanmar-script}

\begin{document}
\textmyanmar{မြန်မာစာ}

\myanmarnumber{1234567890}
\end{document}
```

Compile it with:

```sh
xelatex test.tex
```
