# lishogi updates and regarding the byoyomi format #

*(Original post by ch_suginami-san: https://note.com/ch_suginami/n/n22781eba6766)*

## Correction ##

In the previous post, I wrote that more kifu notation types were added. There, I wrote that the 「右左直引」 disambiguations were not implemented.

But yesterday when I happened to look at a kifu, the notation system had been upgraded and I noticed that disambiguation was supported. I don't know if it was a difference in time or if action was taken after reading the post, but as a result the content of the prior post is now inaccurate. This correction is noted here.

## Happy words ##

I've become quite involved with lishogi, and as I've said before, along the way I've been asked more than a few times for my opinions as a Japanese player. During this time, there are a few passionate people who have taken the trouble to find and read these articles, and even translating those articles saying "this is worth sharing" ([English translations are here](https://gist.github.com/Marken-Foo/4232579bdfb0a87ce646cb2f79719b98)). I have only gratitude for that.

I'm not amazing at shogi, and don't have a lot of followers, so recently I've been acutely appreciative that people are willing to listen to my opinions and discuss them. I'm grateful to everyone involved, and now more than ever feel a greater reponsibility for what I write.

I look forward to continue working with you in the future.

## The byoyomi debate ##

I've written before that byoyomi is nearing implementation, but now another new debate has risen in Discord.

"Should byoyomi have its own independent rating pool?" Or to put it another way, "Is byoyomi incompatible with sudden death and Fischer increment?" is my personal understanding of the debate. (If I've misunderstood please let me know in some way.)

Regarding this point, I've participated in Discord discussions and laid out my thoughts. However, Japanese readers of these posts may not have understood my intentions, and overseas readers may find it hard to understand why Japan has the unique time control of byoyomi in the first place. Conversely, many Japanese may not have even been aware of the Fischer increment from chess culture until it was introduced in the last few years.

I knew of the history of byoyomi from [this post](https://news.yahoo.co.jp/byline/matsumotohirofumi/20200606-00182152/). If you're interested definitely do have a read. However since it is in Japanese, I'll write a little about it here for the English audience.

(Everything enclosed in "" below is quoted from the article.)

As described in the linked post, shogi matches were originally played with "unlimited time" (actually until recently sumo bouts also had no conception of time constraints, and time limits were implemented for the sake of media and television broadcasts.) But in the process of modernisation, around Showa 10 (the 1930s) the idea of a time limit was introduced. At that time, "the chess system was used as a major reference".

In that case, why did the unique system of byoyomi take root in Japan? Historically speaking, the answer is that "with stopwatches which could only round down to the nearest minute, it was difficult to obtain functional chess clocks". Japan at the time imported many goods from the West, and co-opted them into the Japanese way of life. But back then most imports were done by ship, and in the shipping process many chess clocks would have been damaged or become inaccurate. The situation could be summed up as "The Japan Shogi Association bought many imported chess clocks, but they all soon broke and were unusable."

At the end of the day, Japan was forced to adopt a unique time control (principally due to mechanical limitations). Naturally, this was unpopular among overseas players at the time (once at a chess tournament held in Japan, an Englishman was furious after losing in Japanese-style byoyomi, something which modern people can likely still relate to.) In the modern era, chess clock technology has vastly improved, not just in durability, but to the point where they can even be domestically produced now. But because the byoyomi format has become firmly entrenched, systemic change is difficult: there are now chess clocks that support increment and those that support byoyomi. Even so, while professional matches still use byoyomi, time controls are slowly evolving. The rest of the story enters into details, so we'll leave it at this.

(End of referencing the Yahoo article)

So, being based on lichess, from initially having only "sudden death" and "Fischer increment", how should we then treat "byoyomi"? And what should we do with rated games? This brings us back to the topic at the beginning of this section.

There are varied reactions from overseas players, ranging from "Byoyomi is intrinsically linked to Japanese culture, and shogi without byoyomi is inconceivable" to "Byoyomi doesn't suit me so I won't play with it". As I see these exchanges, I think that lishogi should be a site where "even though all these people have differences in their cultural and shogi thinking patterns, they can all still enjoy shogi in the same place", and as far as I know, lishogi is the only place where so many diverse voices can make themselves heard. I'm quite partial in saying so, but I write this carrying my hopes for the site.

So at last, here is my opinion (also expressed on Discord). I think that "regardless of time settings \[increment/byoyomi\], all ratings should be established based on the time it takes for one game." This notion comes from lichess, the origin of lishogi. One concern (as I understand it) is that, won't that mean different time controls affect the same rating value? For example along the lines of "For a game falling within a certain time range, will the rating pool be dominated by increment players rather than byoyomi players?" But I don't think we need to worry about this issue.

As to why, it's because the extra time that increment gives is generally less than that for byoyomi. So games with increment will be shorter than games with byoyomi. Thus, I don't think there's so much overlap within the cadence classifications lichess has made. They may overlap in the case of sudden death, but this is already the case for lichess, and so I don't think this needs special consideration. The increment used for blitz games tends to be fairly short anyway, maybe about equivalent to a 10-second byoyomi game.

That said, although I've made my opinion known here, it's up to the developers and admins to decide. However they decide to do it, as users we should respect it. But since I thought it wouldn't be right to not state my opinion, I wrote it as a long note.com post.

I'd like to hear your candid opinions, and share them as far as possible.

------

*~translated from Japanese by Illion*

If you liked this post, why not go to the [original article on note.com](https://note.com/ch_suginami/n/n22781eba6766) and give it a like?