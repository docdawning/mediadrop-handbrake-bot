mediadrop-handbrake-bot
====================

mediadrop-handbrake-bot is a simple php daemon. It watches mediadrop media tables and loops over uploaded media.
When an unencoded one is found it invokes handbrake to encode it in an h264, "Apple TV 3" compatible one. 
Then it creates the needed media_files in mediadrop db and set the original media as encoded.

There's also some relevant commentary in the php file.

Install:
* sudo add-apt-repository ppa:stebbins/handbrake-releases; sudo apt-get update; sudo apt-get -y install handbrake-cli 
* save bot file in /opt (If you want to change this remember to change hardcoded paths )
* save .conf file in /etc/init/ (This also has an hardcoded path so remember to review it, also upstart ignores symlinked .conf files, so actually copy in there)
* start handbrake bot service with "start handbrake-bot"


Features:
* fill media_file metadata as size and bitrate
* send email via php mail to media author when encoding is done
* upstart script for ubuntu/debian distros

Many todos:
* multiple encoding profiles
* script parametrization ( remove all hardcoded paths )
* automated thumbnail generation 
* ini-based config file support
