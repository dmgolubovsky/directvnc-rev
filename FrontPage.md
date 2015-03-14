# Introduction #

The goal of this project is to provide a graphics terminal client suitable for Xen3 Dom0. It is expected that guest VMs will run Xvnc for their graphics output in case they need X. The [directvnc](http://savannah.nongnu.org/projects/directvnc) program is a thin layer on top of [DirectFB](http://www.directfb.org), has small code size and memory footprint, does not need to be suid-root to run.

However this program has not been in active development for a couple years now. It was written when 64 bit CPUs were not so widespread, it supports only 16 bpp screen resolution, and does not support Unicode. This project is an attempt to revive directvnc adding missing features.


# Major Things to Fix #

  * Make sure it compiles in 64bit environment (AMD64): done, testing snapshots available  in the [Downloads Section](http://code.google.com/p/directvnc-rev/downloads/list)
  * Add support for at least 24bpp screen resolution: done, with manual configuration, see the NewFeatures page
  * Implement universal keyboard switch (similarly to the xmodmap mechanism): done, see the NewFeatures page
    * Ctrl-Q is not a good choice for a quit key, Ctrl-Alt-Del is a better choice since the keyboard is not in its regular console mode anyway: done


# Known Issues #

  * Screen does not redraw properly when switching back to the Linux console where directvnc is running - may be a DirectFB issue though.
  * Not all mouse chords work (also need to look at DirectFB side)

