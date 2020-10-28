# UTF Watermarker

## What have you done?

UTF Watermarker is an API to add watermarkes to text documents that are invisible to the human eye, but easily read by a computer program that knows the code being used. 

### This is in developement.

This readme is the first thing I've started on this project. Unless otherwise noted take all this as "proposed features" or "thinking out loud".

When the first official release hits, any proposed features will be moved to GitHub issues, and any 'notes and thinking aloud' will be cleaned from this document.

## Why did you do this?

It seemed like a fun project.

This is inspired by a similar watermarking scheme used by [Geinus media](www.Genius.com), to prove that their content was being scraped and plagerized by Google, and/or one of their contractors. More information on that can be found [here](https://www.docketalarm.com/cases/New_York_State_Kings_County_Supreme_Court/526241---2019/Genius_Media_Group_Inc._v._Google_LLC_et_al/1/).

## How does this work?

The watermark is hidden in the text with the use of 'lookalike' characters, that have different codes in the file, but have the same, or very similar appearance on screen.

In short, some of the 'common' characters are replaced with uncommmon characters with the same appearance. By making these replacements in a known pattern, the document is watermarked 

### An example

Consider the following two texts:

TODO Images of same text, with and without watermark.

The top image is unmodifed. In the bottom image the (spaces) have been replaced with (space lookalike).  

TODO image illistrating the above paragraph.

If the spaces are interpreted as dots, and the (lookalikes) are interpreted as dashes, they can be interpreted as morse code, spelling out (something).

### Multiple Watermarks

As long as the watermarking schemes do not use the same characters, you can apply as many watermarks as you can fit into the text.

For example, the text above contains a second watermark, hidden in the (character).

TODO: image of the above, with second watermark highlighted and a chart deciphering it.

## Watermark types

This API supports multiple method types of watermark pattern.

### Morse

The above examples interprets the characters as dots and dashes in morse code, while not required, it is a very compact meant of encoding text into your watermark.

### Digital

In this, the characters and their replacements are interpreted as 1's and 0's and may encode any (short) digital message you like.

This could be a random pattern of ones and zeros, or you can specify and integer value.

### Multiple Character Replacement

This variation allows for multiple characters to be part of the same watermark. 

ie: In standard mode a space, or a comma may be part of the same watermark, but not both. Multiple Character Mode can use both.

### Repeating Pattern

A varation of either of the Morse or Ditigal types. Rather than inserting the watermark once, the watermark is repeated as many times as it will fit into the text.
- Repeating Morse
- Repeating Digital

### High Density

Nothing limits us from replacing more than one character per watermarking schemee and some characters have more than one possible replacement. We can leverage both of these to potentialy pack more information into the watermark.

In this mode, the full library of replacable characters is used, and if more than one replacement character is available; the additional characters may be used to represent short patterns of data, rather than single bits.

There are two high desity options

- High Density Morse
- High Desity Digital

Note: I expect that the amount of data that can fit in a given document with this mode to be extreamly variable, as not all possible bit combinations will be available at a given position. So while a document may have a *theoretical* capacity of 250 bits, whether or not that document will be able to hold a given watermark of, say 240 bits will be a matter of trial and error.

If this is implimented, then automated testing tools will already be built to make this process easier.
