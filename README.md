dockerfile-dwarffortress
========================

Dwarf Fortress in a container. Tested on Mint 15 and 16.

Usage
-----

Make sure you are in the same directory as the Dockerfile

    cd dockerfile-dwarffortress

Build the image and tag it DwarfFortress. The -rm options cleans the cache after the final image ha been created.

    docker build -t DwarfFortress -rm .

If you want to run in text mode

    docker run -t -i DwarfFortress -p TEXT

In order to run in 2D mode you need to map stuff from the host to the container

    docker run -t -i -v /tmp/.X11-unix:/tmp/.X11-unix -v /dev/snd:/dev/snd -lxc-conf='lxc.cgroup.devices.allow = c 116:* rwm' -e DISPLAY=unix$DISPLAY DwarfFortress


Todo
----

* Add some common tilesets or
* Use the lazy newb pack (http://www.bay12forums.com/smf/index.php?topic=130792)
* Implement some pratical way to keep saved games.

Credits
-------

* Obviously Toady One at http://www.bay12games.com for Dwarf Fortress.
* Daniel Mizyrycki for the slideshow (http://www.slideshare.net/dotCloud/dockerizing-your-appli) that helped get started.
* Henrik Mühe for the fuse install hack (https://gist.github.com/henrik-muehe/6155333)
* All the guys that maintain the Dwarf Fortress wiki (http://dwarffortresswiki.org/index.php/DF2012:Installation)
