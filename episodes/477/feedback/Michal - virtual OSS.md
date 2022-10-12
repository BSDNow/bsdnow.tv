Hello
I want to share with my history of working with FBSD as main daily OS.
I'm using this system as main OS for 3 years and only one thing was problematic.
The making a video conference with co-workers. The biggest issue was a sound card.
Browsers with native oss weren't working properly.
Sometimes only noises from mic was generated.
Sometimes no sound card was detected.
And eventually I found that virtual oss is a solution for this.
Only problem was that mic was very quiet. I have an old sound card CMI8738
and I found that under linux there was some magic in driver which was turning boost on mic.
I couldn't find any solution for this so I decided to wrote a question to author of virtual oss: HSelasky.
And I was suprised in very positive way.
I received answer almost instantly. The solution was using gain option and compressor.

As I dsicovered with virtual oss the quality of mic was a lot better than under linux (confirmed by co-workers).
Also with launching 2 virtual daemons I can make simple switching between native sound card and audio usb dongle.

Since then I can use FBSD in 100% to work (without switching to linux).

Thanks for the great podcasts!

Michał Zielonka
