# Can a shogi tactics trainer be made? #

*(Original post by karakoro-san: https://note.com/karakorororo/n/n3d352a787214)*

If you have been exposed to both shogi and chess before, you may have wondered about something.

"Isn't there a shogi version of chess tactics?"

Let's try to look at it from a regular person's perspective, someone familiar with shogi but without specialist knowledge.

## What is a tactics trainer\*? ##

Something that **automatically extracts "next move" problems from real games.**

There is an amazing number of problems simply by **automatically** creating (extracting) them. The [picture](https://assets.st-note.com/production/uploads/images/39771817/picture_pc_2c861b8cb9ba2617cbfcd68b8042f965.png) shows lichess tactic number 104184.

This functionality is very interesting, and I'd like to see the same for shogi.

[(How lichess generates training puzzles)](https://lichess.org/blog/U4sjakQAAEAAhH9d/how-training-puzzles-are-generated)

Here I'll do a brief survey of shogi software and applications that offer something similar to a tactics trainer.

## Real-game tsumeshogi ##

In chess there are mate tactics; the shogi equivalent, **real-game tsumeshogi**, is a relatively common problem type in the shogi world.

[(Official tweet by Piyoshogi about real-game tsumeshogi functionality in their web version)](https://twitter.com/STUDIOKPONTA/status/1329959513558970369)

You can find these in books, sites, apps and other places.

However, all of these feel like they have been **added by hand (the problems were curated by humans)**.

There used to be a blog which would post automatically-extracted tsume positions from the floodgate server, but I seem to recall the problems were too hard and thus were not very appropriate for training. This does leave some doubt as to whether such extraction can be successful.

## Shogi Wars Kishin Quiz ##

[(Shogi Wars Kishin Quiz user guide)](https://shogiwars.heroz.jp/guides/quiz?locale=ja)

Kishin Quiz is a feature where you are given positions from your own games where you have to pick between the best move according to engine analysis, and the move you actually played.

By focusing on the comparison to the move actually played, this feature offers something slightly different from a tactic, as these are not necessarily positions with a single "correct" move, whereas with tactics there is a clear single best move.

I think that perhaps the choice of this format is to reduce the amount of machine computation needed.

## Shogi Spark! ##

[(Shogi Spark! app on Google Play Store)](https://play.google.com/store/apps/details?id=com.monaca.shogispark&hl=ja)

Shogi Spark! automatically creates four-option multiple choice next-move questions.

It was too difficult, as the difference in evaluation between the best and the next-best move could be as little as 100-200 points.

## Gekisashi 15's automatic next-move generation ##

Gekisashi 15 has a feature that can automatically create next-move problems.

[(Gekisashi 15 on Amazon JP)](https://www.amazon.co.jp/dp/B08BJHN128?tag=note0e2a-22&linkCode=ogi&th=1&psc=1)

I suspect the generation method probably resembles following: somewhat "random" moves are played from joseki positions stored within Gekisashi, until **the evaluation difference between the best and next-best moves is above a certain threshold, and the next-best move results in an evaluation below zero**.

This is basically the same as extracting positions from a large number of realistic games, so it does seem possible to create tactics in this manner.

However, one concern is that **a fairly large amount of computation power may be required**.

## Summary ##

Seeing that Gekisashi 15's next-move problems are not all of good quality, I wonder if that's the reason why the behemoth Shogi Wars instead decided on the format of comparing the best move against the user-played move.

A shogi tactics trainer is planned to be implemented at lishogi, but seeing how lichess tactics problems sometimes turn out to be a little strange, I'm concerned if it will work out well at lishogi.

You can now catch whispers of "surpassing AI"\*\* floating around in the shogi world, but in fact it is not uncommon for misevaluations of positions with long tsume sequences to occur, where large amounts of computation power are needed.

However, there are also many other ways to implement a tactics trainer, for example like on chess.com where users can rate the problems, or like goproblems where users themselves can create the answers to the problems, and I hope to see further developments in this area.

------

\* TN note: the Japanese term used, 「タクティクス」, can mean tactics puzzles (the puzzles themselves), a tactics trainer (since it's the name used for the lichess tactics trainer), or used to refer to the automatic generation of tactics problems (cf. the lichess implementation). All three meanings are variously used throughout this article.

\*\* TN note: "surpassing AI" or 「AI超え」 is a term that has entered the Japanese lexicon at large after Fujii Souta's thusly-acclaimed 58th move S31, in the 2nd game of the BO5 Kisei match against Watanabe Akira, on 2020-06-28.

*~translated from Japanese by Illion*

If you liked this post, why not go to the [original article on note.com](https://note.com/karakorororo/n/n3d352a787214) and give it a like?