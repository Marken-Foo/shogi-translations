# BOD format #

*This document is a translation of the original Japanese text at https://mozuyama.hatenadiary.org/entry/20030909/p5, published under the title "kif形式詳細 (1)", or "Details of the KIF format (1)".*

- 2020-11-11 translated to English by Marken Foo
- 2003-09-09 original post by mozuyama-san

I did some investigation of the KIF file format used by the free software distributed on Kakinoki Yoshikazu's homepage, Kifu for Windows Ver. 5.13. Although an official version should exist, it has not been made publicly available, so this may be useful for those work on conversion programs supporting the KIF format.

Please do note that there is still a likelihood of errors in this document.

We begin with specifying the board position notation. (If we're only dealing with the board position, it might be more accurate to call it the BOD format.)

## Example of a board position in KIF format ##

An board position in the KIF format could look like the following example in text.

```
後手：羽生善治
後手の持駒：飛　角　金　銀　桂　香　歩四　
  ９ ８ ７ ６ ５ ４ ３ ２ １
+---------------------------+
|v香v桂 ・ ・ ・ ・ ・ ・ ・|一
| ・ ・ ・ 馬 ・ ・ 龍 ・ ・|二
| ・ ・v玉 ・v歩 ・ ・ ・ ・|三
|v歩 ・ ・ ・v金 ・ ・ ・ ・|四
| ・ ・v銀 ・ ・ ・v歩 ・ ・|五
| ・ ・ ・ ・ 玉 ・ ・ ・ ・|六
| 歩 歩 ・ 歩 歩v歩 歩 ・ 歩|七
| ・ ・ ・ ・ ・ ・ ・ ・ ・|八   
| 香 桂v金 ・v金 ・ ・ 桂 香|九
+---------------------------+
先手：谷川浩司
先手の持駒：銀二　歩四　
手数＝171  ▲６二角成  まで
*第44期王位戦第4局

後手番
```

The meaning of each part is as below. Note that in the case of handicap games, "sente" is replaced by "shitate" and "gote" is replaced by "uwate".

### Board ###

The information from ` ９ ８ ７ ６ ５ ４ ３ ２ １` until the second `+---------------------------+` represents the shogi board position. ` ・` (half-width space + full-width dot `・`) represents an empty square, ` 駒` (half-width space + one of 「玉飛龍角馬金銀全桂圭香杏歩と」) represents one of sente's pieces, and `v駒` (half-width lowercase letter v + piece character) represents one of gote's pieces.

### Player names ###

The lines beginning with `先手：` and `後手：` (full-width colons) until a newline represent the names of the sente and gote players respectively. Note that the player names seem to have an upper limit of 79 bytes. (TN: not sure this restriction is still in force in 2020.)

### Pieces in hand ###

The lines beginning with `先手の持駒：` and `後手の持駒：` (full-width colons) until a newline represent the pieces held in hand by sente and gote respectively.

`駒[数]　` (one of 「飛角金銀桂香歩」 + a number in kanji (「一」 for 1 is omitted) + full-width space) represents the number of a particular piece type held in hand. Note that a full-width space is output at the end of the line.

In the case that a player has no pieces in hand, `なし` is used.

### Move number ###

This follows the format of `手数＝[half-width number]  [prior move]  まで`. When the half-width number is zero `0`, the prior move is omitted. Between the half-width number and the prior move, and also between the prior move and the `まで`, there are two half-width spaces.

### Comments ###

The lines beginning with `*` are comments about the board position. In the event that the comment contains a newline, multiple lines shall be marked as comments.

### Side to move ###

If gote is the side to move, `後手番` is output. If sente is the side to move, nothing is output here.
