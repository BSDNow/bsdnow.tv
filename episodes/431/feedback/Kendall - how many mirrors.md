
Hello Everyone,

I've been running a 6 drive pool (raidz2 vdev) in my FreeBSD server for years now without a problem. I started with 1tb, then upgraded to 2 and now 4tb. However, I
decided to start using mirrors for a smaller hit to the wallet when upgrading.

I was wondering what a maximum or recommend size is for the amount of mirrored vdevs in a pool? Right now I have a separate pool with 3 mirrored pairs (2x2tb pairs and 1x8tb pair). I would like to eventually have (3x8tb pairs) but after that do you recommend adding more? How many can I or should I do? I have 15 slots in the chassis total with three empty but I'm thinking of converting the six drives in the raidz2 to mirrors and putting them into the mirror pool. So total would have 6 mirror pairs of 4 and 8 TB (3x8 and 3x4). I could even fit one more pair in there for 7 total. Does this sound like a bad idea? Should I have a separate pool? This pool is just for file serving. I have a separate ssd pool for jails and bhyve.

If you don't mind me asking, how do you configure your mirrored pools?

I appreciate any help and advice you have.

Sincerely,

Kendall 
