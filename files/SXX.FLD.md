# SXX.FLD

## Description

The numbered SXX.FLD files contain the game's maps, along with script data. The text encoding and similar information is documented in the [text notes](notes/text.md).

From reading [Supper's notes](https://github.com/suppertails66/wdtools/blob/master/notes/lunareb_notes.txt) and skimming the files in a hex editor, Magical School's data format bears a superficial similarity to the format used by Lunar: Eternal Blue on the Sega CD.

## Header

The header is always fixed-length, 2048 bytes.

Within the header, each set of 8 bytes contains a 4-byte pointer to the start of a section of data, followed by 4 bytes specifying how long the data chunk is. The number of pointers and what they mean differs from file to file, probably due to complexity of a given scene.

For example, S00.FLD, the smallest file, contains the following four pointers:

00000800 - Pointer into text (and map?) data
000018A4 - Length of preceding chunk
00002800 - Pointer into other map/text data
000013DD - Length of preceding chunk (e.g., 0x2800 + 0x13DD == 0x3BDD, which is where the padding at the end of the file begins)

## Headers

The header format is, roughly:

| Index | Description | Type |
|-------|-------------|--------|
| 0x00 - 0x03 | Unknown | Unsigned 32-bit big-endian integer |
| 0x04 - 0x07 | Offset of dialogue header | Unsigned 32-bit big-endian integer |
| 0x08 - ??? | Unknown - runs until the beginning of the next section |  |
| Offset pointed to by 04-07 | Number of dialogue entries | Unsigned 32-bit big-endian integer |
| Follows the previous offset | Offset to the table of dialogue offsets | Unsigned 32-bit big-endian integer |

The table of dialogue offsets is simply a set of pointers to specific offsets within the file. Each of them points to the beginning of a string, and each string continues until the 0x0800 termination control code.

For example, S00's header looks like this:

* 0x00 - 0x03: 001D0000 - unknown value
* 0x04 - 0x07: 00000038 - offset of dialogue header
* 0x08 - 0x37: various unknown data
* 0x38 - 0x3B: 00000028 (40 in base 10) - number of dialogue strings
* 0x3C - 0x3F: 0000026C - offset to the table of dialogue offsets

* 0x26C - 0x30c: Set of 40 32-bit unsigned integers containing string offsets

The first offset, located at 0x26c, is 00000F54, the address of the first string in the file.

## Padding

Each data segment is padded out with 0xFFs in order to reach an even sector boundary (2048 bytes). This applies to the header as well.

Since the final segment is also padded, this means that every file ends on an even sector boundary and each file is evenly divisible by 2048.
