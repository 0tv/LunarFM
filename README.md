
# LunarFM

⚠ STILL HEAVILY WIP - EXPECT BUGS, EVERYWHERE!!! ⚠

LunarFM is an innovative FM radio broadcaster that leverages flaws in standard computer setups (specifically HDMI radio interference) to transmit audio that can be heard on FM-based radios, by rendering specific patterns of screen data.

## Key features
- Web based: no installation is required and only some configuration if the automatically chosen parameters are not suitable for your use case. (or if some part of automatic detection has gone wrong, this is a WIP project)
- Optimized for performance: this should be able to run on most computers provided they are able to run a HTML5 browser well. (you may want to use a chromium based browser for this project rather than firefox for performance reasons, and safari is very experimental)
- High sample rate: on a 1920x1080@60Hz screen, you can expect audio playback to work up to around 129,600 samples per second (2 * height * refreshRate), this can also be configured to be higher or lower but will change performance.
- Variable frequency: while a lot of similar projects involving HDMI interference only will operate at the pixel clock rate of the connection (e.g. 148.5MHz for a standard 1080p60 setup), this supports a range of up to 20MHz - 1GHz on some setups.
- Automatic configuration: this project uses the timing parameters specified in [CEA-861-B](https://ia803004.us.archive.org/12/items/CEA-861-B/CEA-861-B.pdf) to try automatically determining your pixel clock rate, rather then you manually having to check.

## Main drawbacks
- Limited format support: the project currently only supports mono 8-bit unsigned PCM wav files as they are simple to use with code, this may be updated in the future to support more formats.
- Broadcast range: since HDMI signals aren't exactly intended to be used to broadcast radio signals, they have a very limited range. (I have very limited coverage outside my house, though it still works to some degree)
- Frequency coverage: although in my testing I have managed to create a radio signal from as low as 16.5MHz up to 1.6GHz (my RTL-SDR dongle cuts out at the upper limit), some frequencies will have very poor signal strength (100MHz seems to be a weak spot for my setup) whereas other frequencies (e.g. 400MHz) will have great signal strength.
- Harmonics: while targeting one radio frequency, you can expect copies/distorted versions of the signal all over the radio spectrum, mostly at integer multiples of the main frequency. (the program will tell you where to expect them, but this may not always be accurate)
- Tuning inaccuracy: while the program attempts to detect your pixel clock rate, it will not always be correct, and on top of this even if correct it may still vary slightly - the UI will provide some manual adjustment inputs to allow you to attempt to fix it.
