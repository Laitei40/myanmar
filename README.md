<div align="right">
  <strong>Languages:</strong> 
  <a href="#the-myanmar-script-package-english">🇬🇧 English</a> | 
  <a href="#myanmar-script-package-အကြောင်း-burmese">🇲🇲 မြန်မာဘာသာ</a>
</div>

# The `myanmar-script` Package (English)
---
`myanmar-script` is a lightweight LaTeX package that provides helpers for Unicode Myanmar-script typesetting with XeLaTeX and LuaLaTeX.

The package focuses on providing a simple and reliable foundation for Burmese-language documents. It offers font selection, Myanmar text commands and environments, Myanmar numeral conversion, and basic localization of common document labels.

Its scope is intentionally limited. It does not attempt to provide advanced linguistic or typographic support for Shan, Mon, Karen, Kachin, Rakhine, or other Myanmar-script languages.

## Features

* Unicode-first Myanmar (Burmese) text input.
* XeLaTeX and LuaLaTeX support through `fontspec`.
* Automatic engine check that prevents compilation with pdfLaTeX.
* Built-in font presets for common Myanmar fonts.
* Inline command for short Myanmar text.
* Environment for paragraph and block Myanmar text.
* Arabic digit to Myanmar digit conversion.
* Basic Burmese localization for selected document labels.
* Standard DocStrip (`.dtx` / `.ins`) package structure.

## Supported Fonts

The package currently provides presets for the following fonts:

* Noto Sans Myanmar
* Pyidaungsu
* Myanmar Text
* Padauk
* Tharlon

Example:

```latex
\usepackage[font=padauk]{myanmar-script}
```

## Requirements

You need a modern TeX distribution such as TeX Live or MiKTeX with:

* LaTeX2e
* expl3
* l3keys2e
* iftex
* xparse
* fontspec

Compilation must be performed with:

* XeLaTeX, or
* LuaLaTeX

pdfLaTeX is not supported.

At least one supported OpenType Myanmar font must be installed on the operating system.

## Installation

Generate the package file:

```sh
latex myanmar-script.ins
```

This creates:

```text
myanmar-script.sty
```

Move the generated file to a directory searched by TeX, or keep it beside your document during local development.

## Building the Documentation

Compile the documentation using:

```sh
xelatex myanmar-script.dtx
```

or

```sh
lualatex myanmar-script.dtx
```

The generated manual will be:

```text
myanmar-script.pdf
```

## Usage

Load the package:

```latex
\usepackage[font=noto]{myanmar-script}
```

### Inline Myanmar Text

```latex
\textmyanmar{မြန်မာစာ}
```

### Myanmar Text Environment

```latex
\begin{myanmar}
မြန်မာစာ စာပိုဒ်တစ်ပိုဒ်
\end{myanmar}
```

### Myanmar Numerals

```latex
\myanmarnumber{2026}
```

Output:

```text
၂၀၂၆
```

## Package Options

### Font Selection

```latex
\usepackage[font=noto]{myanmar-script}
```

Available values:

* noto
* pyidaungsu
* myanmartext
* padauk
* tharlon

### Language Selection

```latex
\usepackage[language=burmese]{myanmar-script}
```

Currently supported:

* burmese

## Limitations

This package currently does not provide:

* Automatic Myanmar page numbering
* Myanmar date formatting
* Alphabetical sorting and collation
* Babel integration
* Polyglossia integration
* Advanced line breaking support
* Specialized support for non-Burmese Myanmar-script languages

## Contributing

Bug reports, feature requests, and pull requests are welcome.

Before submitting major changes, please open an issue to discuss the proposed enhancement.

## License

This package is distributed under the LaTeX Project Public License (LPPL), version 1.3c or later.

See:

https://www.latex-project.org/lppl/

## Author

Laitei

Myanmar TeX Project

## Contact

GitHub Issues are the preferred method for reporting bugs and requesting features.

#

# myanmar-script Package အကြောင်း (Burmese)

myanmar-script ဆိုတာ XeLaTeX နဲ့ LuaLaTeX သုံးပြီး Unicode မြန်မာစာ စာစီစာရိုက်ဖို့အတွက် အကူအညီပေးတဲ့ ပေါ့ပေါ့ပါးပါး LaTeX package လေးတစ်ခုပါ။

ဒီ package က မြန်မာဘာသာနဲ့ရေးတဲ့ document တွေအတွက် ရိုးရှင်းပြီး ယုံကြည်စိတ်ချရတဲ့ အခြေခံတစ်ခုဖြစ်ဖို့ အဓိကထားထားပါတယ်။ Font ရွေးတာ၊ မြန်မာစာအတွက် command တွေနဲ့ environment တွေ၊ မြန်မာဂဏန်းပြောင်းပေးတာ၊ နောက်ပြီး document တွေမှာ အသုံးများတဲ့ အညွှန်း (label) တချို့ကို မြန်မာလို အခြေခံပြောင်းပေးတာတွေ ပါဝင်ပါတယ်။

သူ့ရဲ့ လုပ်ဆောင်နိုင်စွမ်းကို တမင်သက်သက် ကန့်သတ်ထားတာပါ။ ရှမ်း၊ မွန်၊ ကရင်၊ ကချင်၊ ရခိုင် နဲ့ တခြား မြန်မာစာလုံးသုံး ဘာသာစကားတွေအတွက် အဆင့်မြင့် ဘာသာစကားပိုင်းဆိုင်ရာ ဒါမှမဟုတ် စာစီစာရိုက်ပိုင်းဆိုင်ရာ အထောက်အပံ့တွေ ပေးဖို့ မကြိုးစားထားပါဘူး။

## ပါဝင်တဲ့ လုပ်ဆောင်ချက်များ (Features)

* Unicode အခြေခံ မြန်မာစာ ရိုက်ထည့်နိုင်ခြင်း။
* fontspec ကနေတဆင့် XeLaTeX နဲ့ LuaLaTeX ကို support ပေးခြင်း။
* pdfLaTeX နဲ့ run မိရင် တားဆီးပေးတဲ့ အလိုအလျောက် engine စစ်ဆေးမှုစနစ် ပါဝင်ခြင်း။
* အသုံးများတဲ့ မြန်မာ font တွေအတွက် အသင့်သုံး (preset) တွေ ပါဝင်ခြင်း။
* တိုတောင်းတဲ့ မြန်မာစာတွေအတွက် inline command ပါဝင်ခြင်း။
* စာပိုဒ်တွေနဲ့ စာစုတွေအတွက် environment ပါဝင်ခြင်း။
* အင်္ဂလိပ် (အာရေဗျ) ဂဏန်း ကနေ မြန်မာဂဏန်း ပြောင်းပေးခြင်း။
* ရွေးချယ်ထားတဲ့ document label တွေအတွက် အခြေခံ မြန်မာဘာသာပြန် ပါဝင်ခြင်း။
* စံသတ်မှတ်ချက်နဲ့အညီ DocStrip (.dtx / .ins) package တည်ဆောက်ပုံဖြစ်ခြင်း။

## အသုံးပြုနိုင်တဲ့ Font များ (Supported Fonts)

လောလောဆယ် ဒီ package မှာ အောက်ပါ font တွေအတွက် preset တွေ ပါဝင်ပါတယ် -

* Noto Sans Myanmar
* Pyidaungsu
* Myanmar Text
* Padauk
* Tharlon

ဥပမာ -

```latex
\usepackage[font=padauk]{myanmar-script}
```

## လိုအပ်ချက်များ (Requirements)

သင့်ဆီမှာ TeX Live ဒါမှမဟုတ် MiKTeX လိုမျိုး ခေတ်မီ TeX distribution တစ်ခု ရှိဖို့လိုပါတယ်။ အဲ့ဒီထဲမှာ အောက်ပါတို့ ပါရပါမယ် -

* LaTeX2e
* expl3
* l3keys2e
* iftex
* xparse
* fontspec

အောက်ပါ engine တစ်ခုခုနဲ့ run (compile) ပေးရပါမယ် -

* XeLaTeX, ဒါမှမဟုတ်
* LuaLaTeX

pdfLaTeX ကို support မပေးပါဘူး။

ကိုယ့်စက်ထဲမှာ (OS မှာ) အထောက်အပံ့ပေးထားတဲ့ OpenType မြန်မာ font အနည်းဆုံး တစ်ခုတော့ သွင်းထားရပါမယ်။

## Install လုပ်နည်း (Installation)

Package file ကို ထုတ်ယူရန် -

```bash
latex myanmar-script.ins
```

ဒီလို run လိုက်ရင် အောက်ပါဖိုင် ထွက်လာပါမယ် -

```text
myanmar-script.sty
```

ထွက်လာတဲ့ဖိုင်ကို TeX က ရှာတွေ့နိုင်တဲ့ directory ထဲ ရွှေ့လိုက်ပါ၊ ဒါမှမဟုတ် ကိုယ် project လုပ်နေတုန်း ကိုယ့် document ဖိုင်ဘေးမှာပဲ ထားထားလို့ ရပါတယ်။

## Documentation (လက်စွဲစာအုပ်) ထုတ်ယူခြင်း

Documentation ကို အောက်ပါအတိုင်း run ပြီး ထုတ်နိုင်ပါတယ် -

```bash
xelatex myanmar-script.dtx
```

(ဒါမှမဟုတ်)

```bash
lualatex myanmar-script.dtx
```

ထွက်လာမယ့် လက်စွဲစာအုပ်ကတော့ -

```text
myanmar-script.pdf
```

## အသုံးပြုပုံ (Usage)

Package ကို ခေါ်သုံးရန် -

```latex
\usepackage[font=noto]{myanmar-script}
```

### စာကြောင်းထဲ မြန်မာစာ ညှပ်ထည့်ရန် (Inline Myanmar Text)

```latex
\textmyanmar{မြန်မာစာ}
```

### စာပိုဒ်လိုက် မြန်မာစာရေးရန် (Myanmar Text Environment)

```latex
\begin{myanmar}
မြန်မာစာ စာပိုဒ်တစ်ပိုဒ်
\end{myanmar}
```

### မြန်မာဂဏန်းများ (Myanmar Numerals)

```latex
\myanmarnumber{2026}
```

ရလဒ် -

```text
၂၀၂၆
```

## Package ရွေးချယ်စရာများ (Package Options)

### Font ရွေးချယ်ခြင်း

```latex
\usepackage[font=noto]{myanmar-script}
```

ရွေးချယ်နိုင်တဲ့ တန်ဖိုးများ -

* noto
* pyidaungsu
* myanmartext
* padauk
* tharlon

### ဘာသာစကား ရွေးချယ်ခြင်း

```latex
\usepackage[language=burmese]{myanmar-script}
```

လောလောဆယ် အထောက်အပံ့ပေးထားသည်များ -

* burmese

## ကန့်သတ်ချက်များ (Limitations)

ဒီ package မှာ လောလောဆယ် အောက်ပါအရာတွေ မပါဝင်သေးပါဘူး -

* စာမျက်နှာနံပါတ်ကို မြန်မာလို အလိုအလျောက်တပ်ပေးခြင်း
* မြန်မာ ရက်စွဲပုံစံ
* အက္ခရာစဉ်လိုက် စီစဉ်ခြင်း
* Babel package နဲ့ ချိတ်ဆက်အသုံးပြုနိုင်မှု
* Polyglossia package နဲ့ ချိတ်ဆက်အသုံးပြုနိုင်မှု
* အဆင့်မြင့် စာကြောင်းဖြတ်တောက်မှု (line breaking)
* ဗမာစာမဟုတ်တဲ့ တခြား မြန်မာစာလုံးသုံး ဘာသာစကားတွေအတွက် သီးသန့် အထောက်အပံ့

## ပါဝင်ကူညီရန် (Contributing)

အမှားအယွင်း (Bug) တင်ပြတာတွေ၊ လုပ်ဆောင်ချက် အသစ်တောင်းဆိုတာတွေနဲ့ Pull request တင်တာတွေကို ကြိုဆိုပါတယ်။

အပြောင်းအလဲ အကြီးကြီးတွေ မလုပ်ခင်မှာ အဆိုပြုချင်တဲ့ အကြောင်းအရာကို ဆွေးနွေးဖို့ Issue အရင် ဖွင့်ပေးပါ။

## လိုင်စင် (License)

ဒီ package ကို LaTeX Project Public License (LPPL) version 1.3c ဒါမှမဟုတ် အဲ့ဒီနောက်ပိုင်းထွက် version တွေနဲ့ ဖြန့်ဝေထားပါတယ်။

ဒီမှာကြည့်ပါ -

https://www.latex-project.org/lppl/

## ရေးသားသူ (Author)

Laitei

Myanmar TeX Project

## ဆက်သွယ်ရန် (Contact)

Bug တွေ တင်ပြဖို့နဲ့ လုပ်ဆောင်ချက်အသစ်တွေ တောင်းဆိုဖို့ဆိုရင် GitHub Issues ကနေတဆင့် ဆက်သွယ်တာကို အားပေးပါတယ်။
