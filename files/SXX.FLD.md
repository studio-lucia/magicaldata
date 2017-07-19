# SXX.FLD

## Description

The numbered SXX.FLD files contain the game's maps, along with script data. The text encoding and similar information is documented in the [text notes](notes/text.md).

From reading [Supper's notes](https://github.com/suppertails66/wdtools/blob/master/notes/lunareb_notes.txt) and skimming the files in a hex editor, Magical School's data format bears a superficial similarity to the format used by Lunar: Eternal Blue on the Sega CD.

## Header

The header is always fixed-length, 2048 bytes.

Within the header, each set of 8 bytes contains a 4-byte pointer to the start of a section of data, followed by 4 bytes specifying how long the data chunk is. The number of pointers and what they mean differs from file to file, probably due to complexity of a given scene.

For example, S00.FLD, the smallest file, contains the following four pointers:

00000800 - Pointer into ??? (map?) data
000018A4 - Length of preceding chunk
00002800 - Pointer into text data
000013DD - Length of preceding chunk (e.g., 0x2800 + 0x13DD == 0x3BDD, which is where the padding at the end of the file begins)

## Text section

Text content begins at roughly 0x31FE into S00.FLD and continues until the end of the text chunk. That leaves text content of roughly 2527 bytes or so, and preceding content of roughly 2558 bytes. What's in the preceding content? Why is it so big?

## Padding

Each data segment is padded out with 0xFFs in order to reach an even sector boundary (2048 bytes). This applies to the header as well.

Since the final segment is also padded, this means that every file ends on an even sector boundary and each file is evenly divisible by 2048.
