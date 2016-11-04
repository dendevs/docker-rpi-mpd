# Pi Mpd

*simple mpd on raspbian*

# Contents

* build: all files for creating images

* run: all files for running container

# Cmd
docker run -d --device /dev/snd -v $PWD/music:/var/lib/mpd/music -p 6600:6600 -p 6680:6680 dendev/rpi-mpd

# Notes
chgrp audio -R $PWD/music # audio host && audio docker share same gid
