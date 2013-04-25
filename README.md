OMXPlayer
=========

OMXPlayer is a commandline OMX player for the Raspberry Pi. It was developed as
a testbed for the XBMC Raspberry PI implementation and is quite handy to use
standalone. 

Downloading OMXPlayer
---------------------

    git clone git://github.com/gstein/omxplayer.git

Compiling OMXPlayer
-------------------

This fork of huceke/omxplayer is intended for building natively on
the Raspberry Pi device under the Raspbian distribution.

The following packages should be installed first:

    libavcodec-dev
    libavdevice-dev
    libavfilter-dev
    libboost-dev
    libpcre3-dev

No configuration is needed. Simply:

    make

This will produce `omxplayer.bin` within the build directory.

Installing OMXPlayer
--------------------

The `omxplayer` script can be used to run omxplayer.bin.

Note: Raspbian installs the omxplayer package by default. The script
looks for that package. Tweak the script, or uninstall the package.

NOTE: I have used a custom script to test omxplayer.bin, rather than
the included `omxplayer` script. I need to set up a better test
environment to tweak `omxplayer`. Just edit the script for your setup.

Using OMXPlayer
---------------

    Usage: omxplayer [OPTIONS] [FILE]
    Options :
             -h / --help                    print this help
             -n / --aidx  index             audio stream index    : e.g. 1
             -o / --adev  device            audio out device      : e.g. hdmi/local
             -i / --info                    dump stream format and exit
             -s / --stats                   pts and buffer stats
             -p / --passthrough             audio passthrough
             -d / --deinterlace             deinterlacing
             -w / --hw                      hw audio decoding
             -3 / --3d mode                 switch tv into 3d mode (e.g. SBS/TB)
             -y / --hdmiclocksync           adjust display refresh rate to match video (default)
             -z / --nohdmiclocksync         do not adjust display refresh rate to match video
             -t / --sid index               show subtitle with index
             -r / --refresh                 adjust framerate/resolution to video
             -g / --genlog                  generate log file
             -l / --pos n                   start position (in seconds)
                  --boost-on-downmix        boost volume when downmixing
                  --vol n                   Set initial volume in millibels (default 0)
                  --subtitles path          external subtitles in UTF-8 srt format
                  --font path               subtitle font
                                            (default: /usr/share/fonts/truetype/freefont/FreeSans.ttf)
                  --font-size size          font size as thousandths of screen height
                                            (default: 55)
                  --align left/center       subtitle alignment (default: left)
                  --lines n                 number of lines to accommodate in the subtitle buffer
                                            (default: 3)
                  --win "x1 y1 x2 y2"       Set position of video window
                  --audio_fifo  n           Size of audio output fifo in seconds
                  --video_fifo  n           Size of video output fifo in MB
                  --audio_queue n           Size of audio input queue in MB
                  --video_queue n           Size of video input queue in MB

For example:

    ./omxplayer -p -o hdmi test.mkv

Key Bindings
------------

While playing you can use the following keys to control omxplayer:

    z			Show Info
    1			Increase Speed
    2			Decrease Speed
    j			Previous Audio stream
    k			Next Audio stream
    i			Previous Chapter
    o			Next Chapter
    n			Previous Subtitle stream
    m			Next Subtitle stream
    s			Toggle subtitles
    d			Subtitle delay -250 ms
    f			Subtitle delay +250 ms
    q			Exit OMXPlayer
    Space or p	Pause/Resume
    -			Decrease Volume
    +			Increase Volume
    Left Arrow	Seek -30
    Right Arrow	Seek +30
    Down Arrow	Seek -600
    Up Arrow	Seek +600
