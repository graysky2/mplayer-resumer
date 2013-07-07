#Mplayer-resumer
An mplayer wrapper script that will resume playback of previously-stopped video where you left off. Written by Bob Igo.

##Dependencies
* Perl
* Perl-shell (http://search.cpan.org/dist/Shell/)

##Documentation
Consult the included man page.

##Installation from Source
To build from source, see the included INSTALL text document.

##Links
* ![logo](http://www.monitorix.org/imgs/archlinux.png "arch logo")Arch: in the [AUR](https://aur.archlinux.org/packages/mplayer-resumer).

##Usage
Usage is trivial... simply call the wrapper-script in place of mplayer.

Example:
	$ mplayer-resumer [options] [path/]filename

If this script is restarted within $tdiff (default 5 seconds) then it will delete the file used to keep track of the videos resume position.

##Rationale
Watching 90 % of a video and stopping causes you to return to the beginning again the next time you watch it. Remembering where you were in the video and resuming at that position is a much nicer behavior for the user. By default, mplayer spits out timecode information that tells you where you are in the video, to the tenth of a second. Mplayer also supports a seek feature on the command-line. We can make use of these features to write an mplayer wrapper that will remember the last position in a video file and resume to it on playback.

##Design Limitation
If the video file to be played is on a read-only file system, or otherwise lives in a location that cannot be written to, resume will fail. This is because the current implementation uses a file parallel to the video file to store the timecode.

