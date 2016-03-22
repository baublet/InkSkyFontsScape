# InkSkyFontsScape
Use SkyFonts with InkScape and other font managers

# Background

InkScape version 0.91 [doesn't correctly load fonts linked in the Windows](https://bugs.launchpad.net/inkscape/+bug/1451267) (10, for me, but reports of 7+ are circulating around the internet) fonts folder. This makes it so font managers like [SkyFonts](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwj4t5utu9TLAhWIlh4KHWiODk0QFggcMAA&url=https%3A%2F%2Fskyfonts.com%2F&usg=AFQjCNFzwRI1GVxhhe3PA18At63mbr2QZQ&sig2=egZ4dUSAiPR08vUo7JrFCw&bvm=bv.117218890,d.dmo), [NexusFont](http://www.xiles.net/), [The Font Thing](http://members.ozemail.com.au/~scef/tft.html), [FontBase](http://fontba.se/), etc. can't be used with Inkscape.

# How to Fix

The fix--for me, at least--is to use symlinks. Windows has allowed symlinks since [Windows Vista](https://msdn.microsoft.com/en-us/library/windows/desktop/aa365680.aspx). Unfortunately, it's not so simple as creating a symlink in the command line, as Windows only allows administrators to run the command.

To get around this, right click on the Windows icon in the bottom left of your screen and select **Command Prompt (Admin)**. That should allow you to create symlinks.

InkScape looks in your %USERPROFILE%/.fonts directory for installed typefaces. So we're going to be creating a symlink from %USERPROFILE%/.fonts to the SkyFonts font directory.

For me, this command worked:

```
mklink /D "%USERPROFILE%\.fonts" "%USERPROFILE%\AppData\Roaming\Monotype\skyfonts-google"
```

This should work regardless of your username, but if you use a different font manager than SkyFonts, you will need to change the second link to whatever directory your font manager stores its fonts.

Hope that helps!
