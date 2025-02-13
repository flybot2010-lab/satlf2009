# Satlf2009
An open source version of the azulsatlf.weatherscan.me client.

Azul Sat LF Server Created by PJFRIX.

I DO NOT RUN THE SERVER AT PHONEHOME.AWNETWORK.NET. I DID NOT MAKE THE CLIENT AT azulsatlf.weatherscan.me. THE CLIENT PROVIDED HERE IS A CUSTOM CLIENT MADE IN http://penguinmod.com AND DOES NOT CONTAIN ANY COPYRIGHT CODE OR IMAGES. THE SLIDESHOW IS LOADED AT RUNTIME AND IS NOT STORED IN THE CODE.

Precompiled and source files are avalible.

Music will be coming soon.

NOTE: If it's not loading, close the tab and wait a minute. The server is refreshing the radar, as such the simulator will refuse to load as a failsafe instead of just showing nothing for the radar.

## Technical Writeup:
The Sat LF simulator (and subsequently Azul Sat LF simulator), are almost completly server-side programs, the client just being a audio player with a slideshow.

In theory there is nothing stopping you from making your own server, other then matching the one made by weatherranch would be damn near impossible without some sort of source code leak. So I recreated the client instead because why not.

The first thing the client does is get the current "timestamps" from the server from https://phonehome.awnetwork.net/satlf/current_timestamps_slides.txt for the slides and https://phonehome.awnetwork.net/satlf/current_timestamps_2009.txt for the radar. No clue why the timestamps for the radar aren't shared from the satLF simulator or in the /satlf2009/ folder.

Then the client goes through the first 4 slides for the "Hourly Forcast" segment. The slides are retrieved at https://phonehome.awnetwork.net/satlf2009/hourly_#.png?SLIDE_TIMESTAMP, where SLIDE_TIMESTAMP is the timestamps_slides.txt we got earlier and # is a number between 0 and 4. The slides are changed every 7 seconds.

Then, the client gets the radar from https://phonehome.awnetwork.net/satlf2009/output_##_TIMESTAMP.png where ## is either ne, se, sc, mw, nw, or sw. And for TIMESTAMP, The server provides 16 timestamps for the radar, which are cycled through rapidly to create the moving radar. Why they didn't use a APNG or a GIF is beyond me. Also of note the server sometimes doesn't provide all 16 timestamps and will only provide 0 to 4 timestamps. This appears to happen when the server is updating the images, and it fixes itself in around a minute and a half.

After that, the 3 Day Forcast is retrieved from https://phonehome.awnetwork.net/satlf2009/3day_#.png?SLIDE_TIMESTAMP, SLIDE_TIMESTAMP was explained before and # being a slide number between 0 and 9.

Finally, the travel forcast is retreved from https://phonehome.awnetwork.net/satlf2009/trv_##.png?SLIDE_TIMESTAMP, with ## folowing the same format as the radar.
