## Piratebox for laptop (eeePc) script collection
##   created by Matthias Strubel (matthias.strubel@aod-rpg.de)  2011-02-22
##   licenced by gpl ;; please feel for improvements or feedback :)
##  Changes:
##    2011-02-27  Chatbox-Integration based on piratebox-release 0.3-1
##    2011-03-02  Still based on 0.3-1 ; now able to deactivate interface-setup
##    2011-03-14  changed droopy with:
##                  - flexible template for chatbox integration (1. step for deactivation option)
##                  - flexible hostname; now import the hostname per -H option
##                changes in ini-script for droopy option -H
##                changed hostname to piratebox.lan  (look@piratebox.conf $HOST option for more info)
##   2011-06-03   added init.d script for routers ; changed references on script-headers
##                added tmp dir with lease file
##   2011-12-19   Some Bugfixes ; Added IW option 
##   2012-01-22   Fixed DomainBug
##   2012-02-11   Fixed some hostname bugs and a wrong path in .READ.ME.txt
##   2012-02-24   Fixed Bridging-Option
##   2012-03-19   Fixed droopy indexhtml
##   2012-04-01   New Feature: Basic python-Forum -> 
##                              http://www.triv.org.uk/~nelis/forest
##                              https://github.com/thatotherguy/piratebox
##                Configure dnsmasq interface in piratebox.conf
##                More customization in /opt/piratebox.conf
##                Possibility to change upload directory

What to do? / Install
---------------------
  > Install debian
  > Install following Packages:
     # Python
     # hostapd
     # dnsmasq
     #   ((courage)) ;)

  > configure your share-folder (where should the uploaded file put to?)
  >   link   or mount your destination folder to /opt/piratebox/share
     # rm /opt/piratebox/share & ln -s /mountpoint /opt/piratebox/share
     or
     # mount /dev/usbstick /opt/piratebox/share
  > copy over the piratebox folder into /opt/ (as root)
     # sudo cp -rv piratebox /opt 
  > create a symlink /opt/piratebox/init.d/piratebox /etc/init.d/
     # sudo ln -s /opt/piratebox/init.d/piratebox /etc/init.d/piratebox  
  > add piratebox to you runlevel (optional)
    # sudo  update-rc.d piratebox defaults
  >   link   or mount your destination folder to /opt/piratebox/share
      # rm /opt/piratebox/share & ln -s /mountpoint /opt/piratebox/share
      or
      # mount /dev/usbstick /opt/piratebox/share
  > copy over the *.htm files from the /opt/piratebox/src/ folder to your share-folder
  >  you can use the installation step:
     /opt/piratebox/bin/install_piratebox.sh /opt/piratebox/conf/piratebox.conf prepShare 
  >  Ensure you copied all .* files  
      # ls -la /opt/piratebox/share 
  > define your personall options in
    # /opt/piratebox/conf/piratebox.conf        # Start which services, IPs etc
    # /opt/piratebox/conf/hostapd.conf          # Some stuff about beeing an APN 

I created
/opt/piratebox/bin   - Binarys and Scripts
/opt/piratebox/conf  - Piratebox related configs (seperated from the normal system-configs!)
/opt/piratebox/src   - Some stuff from david darts ( picture etc)
/opt/piratebox/init.d - the init-script (later more?)

If you use a router, use the piratebox_router init.d script. It has a working start-stop script.


Chatbox/Shoutbox-Integration
-------------------
The Shoutbox is by J-Tech (http://joeyjwc.x3fusion.com). He uses a fix path for the datafile. Because of pointing this path to the /chat folder (yes... in the root directory ),
I changed this path in the chat/cgi-bin/pso*.py scripts to /opt/piratebox/chat/cgi-bin/.
If you plan to put your files somewhere else, you need to change the path in the mentioned scripts.


Forum
-----
Thank you Andrew Nelis for providing the software.  http://www.triv.org.uk/~nelis/forest
You can enabling the python Forum doing the following steps:
  /opt/piratebox/init.d/piratebox stop
  cd /opt/piratebox
  bin/install_piratebox.sh conf/piratebox.conf pyForum
  vi conf/piratebox.conf
     and uncomment the FORUM_LINK_HTML line containing the link
  /opt/piratebox/init.d/piratebox start

Seperate Runlevel
-----------------
I'm using the piratebox on another runlevel, because I don't want to use it on daily work. So do not use the above update-rc.d command if you don't intend to start it always.
If you want to use it on another runlevel you can use
 #  update-rc.d piratebox enable 4
and disable other services, you don't need
 i.e.  # update-rc.d acpid disable 4
These examples are for debian based distributions.


Thank you for trying or using my scripts :)

