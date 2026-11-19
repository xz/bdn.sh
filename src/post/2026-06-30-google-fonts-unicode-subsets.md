---
title: "Google Fonts' Unicode Subset Ranges"
---

I'm working on a project where I'm making optimizations to web fonts to make their file sizes as small as possible, giving the benefits of faster font loading and reduced bandwidth.

One method of optimization called "subsetting" involves splitting one large font file into multiple smaller files, each containing only a portion of the original font's characters.

Subsetting is commonly used for splitting a font into language-specific font files: there's no need to download a font's whole library of Japanese characters when you're reading an article written only with Latin characters! If a user translates that page into Japanese, though, their browser can intelligently request only the Japanese character subset.

As I was researching how other web font providers implement subsetting, I decided to dig deeper into the Unicode ranges Google Fonts uses for their basic Latin subset. I'm publishing this in case it makes anyone else's work with font subsetting a little bit easier!

Let's get the embedding code for the "Inter" family, for example:

```html
<link href="https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap" rel="stylesheet">
```

The URL links to a stylesheet that defines `@font-face` rules for the following subsets, each in normal and italic styles:

- Cyrillic
- Cyrillic extended
- Greek
- Greek extended
- Latin
- Latin extended
- Vietnamese

Focusing on just the "Latin" subset:

```css
/* latin */
@font-face {
  font-family: 'Inter';
  font-style: normal;
  font-weight: 100 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/inter/v20/UcCo3FwrK3iLTcviYwYZ8UA3.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+0304, U+0308, U+0329, U+2000-206F, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
```

This gives a list of Unicode codepoints and codepoint ranges that this font should cover. I checked multiple different fonts from Google Fonts and they all seemed to give the same ranges. For reference, I've broken down these codepoints below.

<details>
<summary>Codepoint details, click here to open!</summary>

## Codepoint Ranges

_Note: for ranges of only 2 characters, I've put these in the "Individual Codepoints" section._

- `U+0000-00FF`: This is technically two blocks:
  - `U+0000-007F`: Basic Latin block: a-z, A-Z, 0-9, and basic punctuation. 34 of the 128 characters are special "control" characters that aren't displayed as text.
  - `U+0080-00FF`: Latin-1 Supplement block: Currency symbols, some math operators like `±` and `×`, fractions like `½` and `¾`, and various accented letters like `ä` and `ð`. Includes 33 invisible control characters.
- `U+2000-206F`: General Punctuation block: A number of differently sized whitespace characters, "fancy" quotation marks, some more mathematical symbols, and some less common punctuation marks like the interrobang `‽`.

## Individual Codepoints

| Codepoint | Name                              | Character |
| --------- | --------------------------------- | --------- |
| `U+0131`  | Latin Small Letter Dotless I      | `ı`       |
| `U+0152`  | Latin Capital Ligature Oe         | `Œ`       |
| `U+0153`  | Latin Small Ligature Oe           | `œ`       |
| `U+02BB`  | Modifier Letter Turned Comma      | `ʻ`       |
| `U+02BC`  | Modifier Letter Apostrophe        | `ʼ`       |
| `U+02C6`  | Modifier Letter Circumflex Accent | `ˆ`       |
| `U+02DA`  | Ring Above                        | `˚`       |
| `U+02DC`  | Small Tilde                       | `˜`       |
| `U+0304`  | Combining Macron                  | `◌̄`       |
| `U+0308`  | Combining Diaeresis               | `◌̈`       |
| `U+0329`  | Combining Vertical Line Below     | `◌̩`       |
| `U+20AC`  | Euro Sign                         | `€`       |
| `U+2122`  | Trade Mark Sign                   | `™`       |
| `U+2191`  | Upwards Arrow                     | `↑`       |
| `U+2193`  | Downwards Arrow                   | `↓`       |
| `U+2212`  | Minus Sign                        | `−`       |
| `U+2215`  | Division Slash                    | `∕`       |
| `U+FEFF`  | Zero Width No-Break Space         | n/a       |
| `U+FFFD`  | Replacement Character             | `�`       |

</details>

If my math is correct, this gives a total of 387 codepoints. Interestingly, the `.woff2` file linked in Google Fonts' CSS contains many additional characters located in other blocks, such as "Latin Capital Letter A with Dot Below" (`Ạ`) from the Latin Extended Additional block. On closer inspection, it looks like these characters are "composite glyphs", overlaying two existing characters.
