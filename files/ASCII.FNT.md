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

Like the filename implies, the 8x8 font is based directly on ASCII. The 16 8x16 characters take up the space normally used by ASCII's unprintable control codes, leaving the 8x8 font to begin with the first printable character. Up through 0x7E, it follows Japanese editions of ASCII exactly, complete with \ rendered as ¥. (Backslash is contained at 0x7F, normally the DEL control character.) From 0x80 on, it appears to follow a custom layout.
