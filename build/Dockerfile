FROM resin/rpi-raspbian:latest

MAINTAINER Denis De Vos <ddenis.de.vos@gmail.com>

# prepare system
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install --reinstall \
      libraspberrypi0 \ 
      libraspberrypi-dev \ 
      libraspberrypi-doc \ 
      libraspberrypi-bin

# install audio && mpd
RUN apt-get install \
      alsa-base \ 
      alsa-utils \ 
      mpg321 \ 
      lame \
      mpd \
      -y

# set good perms
RUN mkdir /run/mpd \
    && chown mpd:audio -R /run/mpd \
    && chmod 775 -R /run/mpd \
    && chown mpd:audio -R /var/lib/mpd \
    && chmod 775 -R /var/lib/mpd

# config mpd 
COPY config/mpd.conf /etc/mpd.conf

USER mpd

CMD mpd --no-daemon --stdout -v 

EXPOSE 6600 8000
