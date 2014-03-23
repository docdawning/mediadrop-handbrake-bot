mediadrop-handbrake-bot
====================

mediadrop-handbrake-bot is a simple php daemon. It watches mediadrop media tables and loops over uploaded media.
When an unencoded one is found it invokes handbrake to encode it in an h264, "Apple TV 3" compatible one. 
Then it creates the needed media_files in mediadrop db and set the original media as encoded.

It also creates thumbnails using ffmpeg. I've created a little script directory in here. You can tune the thumbnail script
a little if you want. Right now it mindlessly just makes a thumbnail from 15s in to the video, so I guess you'd better have a video
at least that long or there will be no thumbnail.

There's also some relevant commentary in the php file.

Install:
* git clone https://github.com/docdawning/mediadrop-handbrake-bot.git /opt/mediadrop-handbrake-bot
* sudo add-apt-repository ppa:stebbins/handbrake-releases; sudo apt-get update; sudo apt-get -y install handbrake-cli
* Optional: My thumbnail generation uses ffmpeg, to install it: sudo apt-get install ffmpeg
* Update path info in .php and .conf file if you installed to some other path
* Copy .conf file to /etc/init/ (Note upstart disregards symlinked .conf files, so actually copy in there, lame, I know)
* start handbrake bot service with "start handbrake-bot"
* Watch plugin output if you want: tail -f /var/log/upstart/handbrake-bot.log
* Paypal donate a beer to Doc: http://www.dawning.ca/about/

Features:
* fill media_file metadata as size and bitrate
* send email via php mail to media author when encoding is done
* upstart script for ubuntu/debian distros

Many todos:
* multiple encoding profiles
* script parameterization ( remove all hardcoded paths )
* Improved thumbnail generation (right now the small, medium and large sizes are all the same)
* ini-based config file support
