# Text

I haven't yet located the text. The script doesn't follow the same file layout as Silver Star Story, so I don't have something immediately clear to go on.

The game's font is located in [../files/KANJI.FNT](KANJI.FNT). Silver Star Story has a similar font layout; in that game, dialogue uses a two-byte fixed-length encoding which is a simple index of the character within the font. That may not be the case in this game.

## Sample

This is the first dialogue box in the game.

> 今年は ジャムを作って<br>
> それから パイに ケーキに<br>
> アイスクリームってところね❤<br>

Line 1:

| Offset | Character | Index in KANJI.FNT |
| ------ | --------- | ------------------ |
| 00 | 今 | 0295 |
| 01 | 年 |  |
| 02 | は | 007E |
| 03 |   | 0000 |
| 04 | ジ | 00AC |
| 05 | ャ | 00D7 |
| 06 | ム | 00D4 |
| 07 | を | 0093 |
| 08 | 作 |  |
| 09 | っ | 0066 |
| 10 | て | 0069 |

Line 2:

| Offset | Character | Index in KANJI.FNT |
| ------ | --------- | ------------------ |
| 00 | そ | 0060 |
| 01 | れ | 008F |
| 02 | か | 004E |
| 03 | ら | 008C |
| 04 |   | 0000 |
| 05 | パ | 00C5 |
| 06 | イ | 0098 |
| 07 | に | 0062 |
| 08 |   | 0000 |
| 09 | ケ | 00A5 |
| 10 | ー | 000A |
| 11 | キ | 00A1 |
| 12 | に | 0062 |

Line 3:

| Offset | Character | Index in KANJI.FNT |
| ------ | --------- | ------------------ |
| 00 | ア | 0096 |
| 01 | イ | 0098 |
| 02 | ス | 00AD |
| 03 | ク | 00A3 |
| 04 | リ | 00DE |
| 05 | ー | 000A |
| 06 | ム | 00D4 |
| 07 | っ | 0066 |
| 08 | て | 0069 |
| 09 | こ | 0056 |
| 10 | ろ | 0090 |
| 11 | ね | 0070 |
| 13 | ❤︎ | 030F |

