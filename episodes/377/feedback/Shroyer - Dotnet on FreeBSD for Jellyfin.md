Allan, Benedict, JT,

Great show!  I never miss an episode.  Keep up the great work!

My question is about how to be able to run Jellyfin on FreeBSD.  Jellyfin - for those that don't know - is a descendant of Emby, and it's basically a fully free and open source (and slightly more rough-around-the-edges) competitor to Plex.  Being able to run it on FreeBSD would be so great!  Me asking you about this is basically a hail mary, because it feels almost impossible to do, but if anyone can do it, you can!

If you want to know what I've gone through, here you go:

I found a recent reddit thread (https://www.reddit.com/r/jellyfin/comments/hztlrq/jellyfin_and_freebsd/) where someone points out that you should be able to install and run Jellyfin on FreeBSD because there is a Dotnet 3.0 available for FreeBSD.  Then a developer chimed in that Jellyfin needs Dotnet 3.1. In fact, they have a developer who tried to run Jellyfin, and they listed the steps here: https://github.com/mcarlton00/jellyfin-bsd-testing.  I tried to install 3.0 the same way as on the github page to see what would happen.  

I got "pretty far" following those steps.  I got the following errors at first:

Failed to load ?, error: Shared object "libintl.so.8" not found, required by "libcoreclr.so"
Failed to bind to CoreCLR at '/usr/local/dotnet/shared/Microsoft.NETCore.App/3.0.0-preview-27218-01/libcoreclr.so'

So then I installed the gettext package which brought with it libintl.so.8 (which seemed to be the thing to do after some searching).  That got me a new error:

Failed to initialize CoreCLR, HRESULT: 0x8007001F

I overcame this with adding allow.mlock; to the jail.conf.

And it worked!  Except it didn't.  I got the same error as at the bottom of the github page.  After dotnet starts and shows some progress, it ultimately says:

Microsoft.DotNet.Cli.Utils.CommandUnknownException: No executable found matching command "dotnet-jellyfin".

At first, all I could find was that there was supposedly no Dotnet 3.1 for FreeBSD, but then I found this:

https://github.com/jasonpugsley/core-sdk/wiki/.NET-Core-3.1.103-for-FreeBSD

It provides some additional instructions, namely to modify a NuGet config so that it uses some system packages that he has you download and extract.  Since there is no NuGet config for Jellyfin (that I saw), I couldn't heed that advice.  But I took the rest of the steps, and the result was the same as with Dotnet 3.0: No executable found matching command "dotnet-jellyfin"..

The guy who created the 3.1 build did a lot of work, and he points out that FreeBSD would really benefit from more people from the community using and contributing to the dotnet repos.  Here's a link for building Dotnet 3.1 yourself along with his commentary: https://github.com/jasonpugsley/core-sdk/wiki/Build-.NET-SDK-3.1.103-for-FreeBSD

Anyway, I don't know what else to try.  Apparently, Microsoft can't bootstrap compile Dotnet for FreeBSD anymore, so it's really tough for the folks working on DotNet for FreeBSD because they must reinvent the wheel, but it sounds like they're making progress.  Nevertheless, a "good enough" 3.1 appears to be available, so I'd like to think it'd work.

Presumably, the Jellyfin developers could work around this, given the resources.  Are we at the mercy of the Jellyfin developers to restore FreeBSD functionality (who don't have FreeBSD machines for building and testing, much less spare time to figure it out)?  Or might you fine gentlemen have some magic up your sleeves?? :D:D

Even if you don't have magic up your sleeves, I'd be curious to hear your thoughts if you have any.

Thanks so much!