# ASCII.FNT

## Description

Contains the game's menu fonts. The file has a mixture of 8x16 and 8x8 fonts, all stored at 1bpp.

## 8x16

Begins at the beginning of the file, and lasts for 256 bytes. Contains 14 characters and two empty characters for padding:

| Index | ASCII character |
| ----- | --------------- |
|  0 | 0 |
|  1 | 1 |
|  2 | 2 |
|  3 | 3 |
|  4 | 4 |
|  5 | 5 |
|  6 | 6 |
|  7 | 7 |
|  8 | 8 |
|  9 | 9 |
| 10 | : |
| 11 | / |
| 12 | L |
| 13 | v |
| 14 |   |
| 15 |   |

## 8x8

Begins at 0x0100, and continues for the remainder of the file. Contains an uppercase and lowercase English font, assorted punctuation, and a set of hiragana.

### Encoding

The codepoints for the 8x8 font begin at 32; the "missing" 32 characters are the space taken up by the 8x16 font.

Like the filename implies, the 8x8 font is based directly on ASCII. More specifically, it's a variant of [JIS X 0201](https://en.wikipedia.org/wiki/JIS_X_0201), an 8-bit encoding which was the basis of [Shift JIS](https://en.wikipedia.org/wiki/Shift_JIS). Up through 0x7D, it follows JIS X 0201 exactly, complete with \ rendered as ¥. 0x7E, normally an overline (‾) in JIS X 0201, is a tilde (~) as it is in ASCII. \ is contained at 0x7F, normally the DEL control character.

JIS X 0201 contains a katakana character set, but not hiragana. In this character set, the full set of katakana and Japanese punctuation from 0xA1 through 0xDF have the same codepoints as they do in JIS X 0201.

Unlike JIS X 0201, this character set does include a full set of hiragana. It replaces the control characters which normally exist between 0x86 and 0x9F and the unassigned characters between 0xE0 and 0xFD. Because no single block of control characters was large enough to fit a contiguous block of hiragana, the set of hiragana is split into two parts, with the first block containing を through そ and the second block containing た through ん. Aside from this, the order of hiragana is identical to the order of katakana.

### Table

A copy of the full set of characters is available within the [ASCII_FNT_8x8.csv](../font_tables/ASCII_FNT_8x8.csv) file. This map has the decimal codepoint and the UTF-8 version of the character. A couple of notes on this file:

* JIS X 0201 katakana are normally represented as half-width characters, to distinguish from the regular-width characters in the two-byte space of Shift JIS. I've chosen to map these to full-width characters.
* Empty spaces in the character set are represented as boxes similar to ☐ in the font. I've mapped them to the Unicode replacement character, �.
