# The `myanmar` Package

The `myanmar` package provides native, Unicode-compliant typesetting support for the Myanmar script ecosystem in LaTeX. It natively maps typographic OpenType features for Burmese, Shan, Mon, and Karen via `fontspec` and standardizes text input and numeral manipulation using `expl3`.

## Features
* **Engine Strictness:** Compiles exclusively under XeLaTeX and LuaLaTeX (requires OpenType shaping).
* **Font Configuration:** Out-of-the-box support for `Noto Sans Myanmar`, `Padauk`, and `Tharlon`.
* **Numeral Conversion:** Seamless translation of Arabic digits to Myanmar digits via `\myanmarnumber{}`.
* **Localization:** Automatic translation of standard LaTeX document strings (Table of Contents, Chapters, Figures).

## Installation
Run standard compilation on the `.ins` file to extract the `.sty`:
```bash
latex myanmar.ins