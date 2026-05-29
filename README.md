# The `myanmar` Package

`myanmar` is a LaTeX package for Unicode Myanmar-script typesetting with
XeLaTeX and LuaLaTeX. It provides a small, modern interface for selecting a
Myanmar font, writing inline or block Myanmar text, converting Arabic digits to
Myanmar digits, and applying basic Burmese document-string localization.

The package is written as a documented LaTeX source package. The main source is
`myanmar.dtx`, and `myanmar.ins` extracts the generated `myanmar.sty` file with
DocStrip.

## Status

This package is currently an early package skeleton. The core user interface is
present, but language-specific typography and localization beyond Burmese are
still minimal.

## Features

- Unicode-first Myanmar text input.
- XeLaTeX and LuaLaTeX support through `fontspec`.
- Engine check that stops compilation under pdfLaTeX.
- Built-in font choices for common Myanmar fonts.
- Inline command for short Myanmar text.
- Environment for paragraph or block Myanmar text.
- Arabic digit to Myanmar digit conversion.
- Basic Burmese names for common LaTeX document strings.
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
|-- myanmar.sty
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
- `myanmar.ins` extracts `myanmar.sty` from `myanmar.dtx`.
- `myanmar.sty` is the generated package file used by LaTeX documents.
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
myanmar.sty
```

For local testing, keep `myanmar.sty` beside the document you are compiling, or
compile from this repository root so TeX can find it.

For a user-level installation, copy the generated `myanmar.sty` into a local
TeX tree. For example:

```text
texmf/tex/latex/myanmar/myanmar.sty
```

Then refresh the filename database if your TeX distribution requires it.

## Basic Usage

```tex
% !TeX program = xelatex
\documentclass{article}

\usepackage[font=noto, language=burmese]{myanmar}

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
\usepackage[font=noto]{myanmar}
\usepackage[font=pyidaungsu]{myanmar}
\usepackage[font=myanmartext]{myanmar}
\usepackage[font=myanmar-text]{myanmar}
\usepackage[font=padauk]{myanmar}
\usepackage[font=tharlon]{myanmar}
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

Selects the target Myanmar-script language variant.

```tex
\usepackage[language=burmese]{myanmar}
\usepackage[language=shan]{myanmar}
\usepackage[language=mon]{myanmar}
\usepackage[language=sgawkaren]{myanmar}
```

Available values:

| Value | Language |
| --- | --- |
| `burmese` | Burmese |
| `shan` | Shan |
| `mon` | Mon |
| `sgawkaren` | S'gaw Karen |

Default:

```tex
language=burmese
```

At present, Burmese has the basic localization hook. Other language options are
reserved for future language-specific behavior.

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

When `language=burmese` is selected, the package currently defines basic
Burmese names for common LaTeX document strings at the beginning of the
document.

The implementation currently covers strings such as:

- `\contentsname`
- `\chaptername`
- `\figurename`
- `\tablename`
- `\bibname`

Additional language-specific strings for Shan, Mon, and S'gaw Karen are planned
for future development.

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
`myanmar.sty`, generate the package documentation with XeLaTeX:

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
\usepackage[font=noto, language=burmese]{myanmar}

\begin{document}
\textmyanmar{မြန်မာစာ}

\myanmarnumber{1234567890}
\end{document}
```

Compile it with:

```sh
xelatex test.tex
```
