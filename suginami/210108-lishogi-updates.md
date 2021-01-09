# lishogi latest updates (8th January) #

*(Original post by ch_suginami-san: https://note.com/ch_suginami/n/n5097fa386257)*

Dear readers, happy new year.

lishogi has implemented multiple desired features during this year end and new year period. Although I would have already written a post about them, today's updates were so near completion that I decided to wait for them before writing, so this post comes a little later. So, let's have a look at these new features.

## Added features ##

### Byoyomi added!!! ###

We simply cannot talk about the major progress lishogi has made at the end of the year without mentioning the implementation of byoyomi. As covered in [lishogi's official blog post](https://lishogi.org/blog/X-0MXxEAACIAJcZs/12%E6%9C%88%E3%81%AE%E3%82%A2%E3%83%83%E3%83%95%E3%83%86%E3%83%BC%E3%83%88) (I have translated this one too), for the time controls, the number of seconds is written after **a + sign for increment time controls**, and **a | sign for byoyomi time controls**. Rated matches can use one of the existing sudden death, increment, or new byoyomi time controls. This way of writing the time controls allows for the rare and novel possibility for increment and byoyomi to be used simultaneously. However, as internal Discord discussions are still happening, this mixed time control **may change in the future**. I will make an update if this happens.

Even so, this definitely increases the interest in lishogi as a site. Although at launch 10-second \[byoyomi\] shogi was unavailable, this has since been remedied. A byoyomi setting of not just 30 seconds is available, but you can choose from a wide range of 1 second to 180 seconds. It's even possible to have a zero base time, **1-second byoyomi ultrabullet** (I haven't played it yet, so I can't even imagine what kind of world it is!)

It is also possible to specify **"additional"** byoyomi periods. This appears to be very familiar in the go world, but there may be shogi players for whom this rings no bells. If you watch the NHK Cup, you can think of it as similar to the "additional thinking time" system used there. The number of periods can be set to one for ordinary byoyomi, or it can go up to five for multiple periods. However, rated games cannot be made with two or more periods. (TN: They can now.)

### Click to drop pieces in hand ###

Until now pieces in hand could only be dropped on the board via dragging, and this was unpopular among tablet device users in particular. After this change, the experience has improved for not just PC browser users, but also tablet and smartphone users.

### Streaming functionalities ###

If there are readers considering streaming shogi using lishogi, why not register as a streamer on lishogi? Once you have submitted a streamer application and been accepted by a moderator, your lishogi streams will appear at the top of the main lishogi site page. The two platforms of **YouTube Live** and **Twitch** are supported.

Of course, the stream content must be related to lishogi. For the specific rules, please check the [lishogi streamers page](https://lishogi.org/streamer).

### Additional boards and pieces ###

You can now customise the board for a more traditional shogi aesthetic, or for a more thought-out original look. By changing the site background to transparent, you can set your own favourite background. Customise lishogi your way.

### Server analysis engine "YaneuraOu" added! ###

Computer analysis is now possible. However, YaneuraOu can only be used on the server-side, and only for regular even games (it seems variant shogi currently causes it to crash). But it takes a fair bit of time (it runs on a distributed network, so analysis can only run when there is an available machine), and the evaluation value will of course differ from other engines. If your own machine has good specs, or if you are particular about the engine used, you can export a kifu as described next and run your own analysis instead.

### Kifu export provided!!! ###

This is yet another much-awaited feature. Until now kifu had to be manually entered, or else other kifu conversion sites had to be used. Now standard-conforming kifu export is supported. At the point of writing this post, because I hadn't yet gotten wind of this, I hadn't tried using ShogiGUI etc. to analyse, but it probably works without problems. This certainly makes it easier to do original analysis and post-game reviews.


## Points to note and improvements from here on ##

Now that I've broadly explained the added features, let's note a few points we should take notice of.

### No byoyomi countdown ###

Unfortunately, there is currently no countdown feature for byoyomi (voice countdown is notably missing), so when you're in byoyomi you have to pay attention to the time you have left.

### Regarding the try rule ###

Although there is a try rule, from what I've heard due to discrepancies between the English Wikipedia page used as a reference and the actual try rule, it is currently not functioning correctly.

As it stands, it seems that the game is won when one king legally reaches the opponent's king's starting square while "both sides have entering kings". Under the original try rule, you win if your king reaches the target square, regardless of the opponent's king position. This difference has been reported and is being fixed, but until then please take note of this while playing online games. Eventually this will be fixed, and after that impasse declaration is looking to be implemented next. The developers are attacking this issue, so as users we can just wait patiently.

<br/>

As an online shogi playing site its features are coming together quite nicely. And the number of concurrent users, which was a concern at one point, seems to be on the rise. Although there may be instances where it feels like things are lacking, it has already come this far with a lot of support since it came into service just a few months ago. Here's to more new encounters and great games to come.


------

*~translated from Japanese by Illion*

If you liked this post, why not go to the [original article on note.com](https://note.com/ch_suginami/n/n5097fa386257) and give it a like?