# CSA standard kifu file format #

*This document is a translation of the original Japanese text at http://www2.computer-shogi.org/protocol/record_v22.html on 2020-12-19 by Marken Foo.*

- 1991-03-08 original draft by Kakinoki Yoshikazu
- 1991-03-09 discussed by the Computer Shogi Association (CSA)
- 1991-05-11 1st Edition accepted by the CSA
- 1997-08-25 3rd Edition accepted by CSA board
    - `%KACHI`, `%HIKIWAKE` added
- 2002-11-15 4th Edition accepted by CSA board
    - Version(V2), kifu metadata added
- 2005-09-10 5th Edition accepted at regular CSA board meeting
    - `%TIME_UP` added
    - `%ILLEGAL_MOVE` added
    - Updated to V2.1
- 2008-01-12 accepted by CSA board
    - `%+ILLEGAL_ACTION` added
    - `%-ILLEGAL_ACTION` added
    - Updated to V2.2
- 2020-12-19 translated to English by Marken Foo


## 1. Introduction ##

A kifu file format standard is specified to enable position data transfer of kifu and tsumeshogi between different shogi software. Accordingly, human readability or minimising file size are not the main goals of this format.

Individual software are not required to use this file format natively. If each software's native format can be converted to this format, data transfer between all becomes possible.

This specification is based on the following regulations.

1. 「コンピュータ将棋ファイル記述形式」(第1版)、CSA 資料集 Vol.1
2. 「通信将棋規約の案」、CSA 資料集 Vol.2
3. 「第1回コンピュータ将棋選手権, 通信仕様」、CSA 資料集 Vol.4



## 2. Kifu file format ##

### 2.1 Summary ###

In order to simplify handling kifu files, they shall be text files. Character and newline encodings follow the OS or environment. Comments and kifu metadata (player names etc.) may be in Japanese.

Kifu files are composed of the following data:

1. Version
2. Kifu metadata
3. Initial position (including pieces in hand and side to move)
4. Moves played and time expended
5. Comments

Except for comments, the data must follow this order.

(2), (4) and (5) may be omitted.

To display multiple kifu or data, multiple sets of data may be concatenated with separators (lines containing exactly "/") in between to display multiple kifu or positions.


### 2.2 Version ###

The version number is recorded following a "V". The current version is `V2.2`.

In the event that the version is missing, it will default to the 1997-08-25 standard.


### 2.3 Kifu metadata ###

#### (1) Player names ####

- `N+` followed by the name of the "+" (sente/shitate) player.
- `N-` followed by the name of the "-" (gote/uwate) player.

Each takes one line and may be omitted.

Example:

```
N+NAKAHARA
N-YONENAGA
```

#### (2) Various types of metadata ####

Each field is in the form of `$` followed by a `KEYWORD` followed by a `:`, then a string for the data.

All metadata fields may be omitted.

- Event name: `$EVENT:(event name)`
- Location: `$SITE:(location name)`
- Start time and date (time can be omitted): `$START_TIME:YYYY/MM/DD HH:MM:SS`
    - One space between the date and time (if included).
    - e.g. `$START_TIME:2002/01/01 19:00:00` or `$START_TIME:2002/01/01`
- End time and date (time can be omitted): `$END_TIME:YYYY/MM/DD HH:MM:SS`
- Time control (base time and byoyomi): `$TIME_LIMIT:HH:MM+SS`
    - Base time in `HH:MM`, byoyomi in `SS`. In the event of sudden death, record byoyomi as `00`. Examples:
    - `$TIME_LIMIT:00:25+00` is 25 minute sudden death.
    - `$TIME_LIMIT:00:30+30` is 30 minute base time with 30-second byoyomi.
    - `$TIME_LIMIT:00:00+30` is no base time, 30-second byoyomi.
- Opening: `$OPENING:(opening name)`
- Additional information: more fields can be added following the same format of `$(keyword):(data)`


### 2.4 Pieces and position ###

Piece names: `FU` (pawn), `KY` (lance), `KE` (knight), `GI` (silver), `KI` (gold), `KA` (bishop), `HI` (rook), `OU` (king)

Promoted pieces: `TO` (promoted pawn), `NY` (promoted lance), `NK` (promoted knight), `NG` (promoted silver), `UM` (horse), `RY` (dragon)

Position: squares are numbered with 2 digits, from `11` to `99` as in regular notation (first digit is the column from right to left, second digit is the row from top to bottom.)

The "square" for pieces in hand is `00`.

Prepend `+` for sente/shitate's pieces, and `-` for gote/uwate's pieces.


### 2.5 Initial position ###

A string beginning with `P` (this was decided initially).

#### (1) Even games and handicap games ####

For even games, indicate `PI`. For handicap games, indicate `PI` followed by the squares and types of the missing pieces.

e.g. 2-piece handicap: `PI82HI22KA`

#### (2) Specify a whole position ####

The status of a row of squares is specified. The number of the row is indicated, followed by the pieces' side and type.

If the piece side indicator is anything other than `+` or `-`, no piece will be present in that square.

One square is described by three characters, and one row contains nine squares.

e.g. `P1-KY-KE-GI-KI-OU-KI-GI-KE-KY`, `P2 * -HI *  *  *  *  * -KA * `

#### (3) Specify individual pieces ####

When specifying pieces one by one, specify first the side, then the square and type of piece.

`AL` used for pieces in hand represents "all other pieces".

The "square" for pieces in hand is `00`.

Kings cannot be held in hand.

Example:
```
P-22KA
P+99KY89KE
P+00KI00FU
P-00AL
```

#### (4) Side to move ####

`+` indicates the "+" side (sente/shitate), `-` indicates the "-" side (gote/uwate) to move. This occupies one line, and must be specified.

#### (5) Additional information ####

The default position assumes all pieces are in the piece box (i.e. off the board and also not in either player's hand), and using the methods in (2) and (3), pieces are moved from the piece box into the position. Accordingly, any pieces not specified by items (1)-(3) are assumed to be in the piece box. Additionally, when nothing is specified to be on the board, the board will remain empty.

Descriptions (1) and (2) cannot be used simultaneously.

`P+00AL` and `P-00AL`, when used, must be the final position description present.

Side to move must be indicated after the rest of the position data.


### 2.6 Moves played and time expended ###

Each move takes one line, and the time spent for that move is on the following line.

#### (1) Regular moves ####

Indicated as side to move (`+` or `-`), followed by initial and final squares, followed by the piece name.

e.g. `+3324NG` is ▲2四銀成

#### (2) Special "moves" / game termination ####

These begin with `%`.

- `%TORYO` resignation
- `%CHUDAN` abortion
- `%SENNICHITE` sennichite
- `%TIME_UP` the side to move loses on time
- `%ILLEGAL_MOVE` the side to move makes an illegal move and loses; the illegality is recorded in a comment.
- `%+ILLEGAL_ACTION` sente (shitate) makes an illegal action, and gote (uwate) wins.
- `%-ILLEGAL_ACTION` gote (uwate) makes an illegal action, and sente (shitate) wins.
- `%JISHOGI` jishogi
- `%KACHI` (entering king) declaration of a win
- `%HIKIWAKE` (entering king) declaration of a draw
- `%MATTA` takeback
- `%TSUMI` mate
- `%FUZUMI` not mate
- `%ERROR` error

#### (3) Time expended ####

Given as `T` followed by the number of seconds spent on the move. Fractions of seconds are truncated.

Time expended may be omitted.

e.g. `T10`


### 2.7 Comments ###

Lines beginning with `'` (an apostrophe) are skipped by the parser.

Comments cannot be inserted in the middle of a line.


### 2.8 Multi-statements ###

Using `,` (a comma), multiple lines may be condensed into one line.


### 2.9 File extension ###

This shall be `csa`. If case matters like in Unix, this shall be in small letters.


## 3. Kifu file example ##

```
'----------棋譜ファイルの例"example.csa"-----------------
'バージョン
V2.2
'対局者名
N+NAKAHARA
N-YONENAGA
'棋譜情報
'棋戦名
$EVENT:13th World Computer Shogi Championship
'対局場所
$SITE:KAZUSA ARC
'開始日時
$START_TIME:2003/05/03 10:30:00
'終了日時
$END_TIME:2003/05/03 11:11:05
'持ち時間:25分、切れ負け
$TIME_LIMIT:00:25+00
'戦型:矢倉
$OPENING:YAGURA
'平手の局面
P1-KY-KE-GI-KI-OU-KI-GI-KE-KY
P2 * -HI *  *  *  *  * -KA * 
P3-FU-FU-FU-FU-FU-FU-FU-FU-FU
P4 *  *  *  *  *  *  *  *  * 
P5 *  *  *  *  *  *  *  *  * 
P6 *  *  *  *  *  *  *  *  * 
P7+FU+FU+FU+FU+FU+FU+FU+FU+FU
P8 * +KA *  *  *  *  * +HI * 
P9+KY+KE+GI+KI+OU+KI+GI+KE+KY
'先手番
+
'指し手と消費時間
+2726FU
T12
-3334FU
T6
%CHUDAN
'---------------------------------------------------------
```