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

## Text section

Examining S00.FLD, which has two sections, it looks like there's text within both chunks. Based on the format of Eternal Blue I expected them to contain discrete types of data, but I guess not.

Text content within the first chunk begins at 0x1754 and continues until roughly the end of the chunk.

Text content within the second text chunk begins at roughly 0x31FE and continues until the end of the text chunk. That leaves text content of roughly 2527 bytes or so, and preceding content of roughly 2558 bytes. Some of this data is probably map content - but what?

## Padding

Each data segment is padded out with 0xFFs in order to reach an even sector boundary (2048 bytes). This applies to the header as well.

Since the final segment is also padded, this means that every file ends on an even sector boundary and each file is evenly divisible by 2048.
