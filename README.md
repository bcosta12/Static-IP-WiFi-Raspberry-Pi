# Static-IP-WiFi-Raspberry-Pi

 This is tutorial explain how to set static IP on Raspberry Pi 3B. My objective is to save this knowledge and future users can find this solution here too. 

# Static Address

Go to /etc/network/interfaces, shoud be like this on Raspbian:

      #interfaces(5) file used by ifup(8) and ifdown(8)

      #Please note that this file is written to be used with dhcpcd
      #For static IP, consult /etc/dhcpcd.conf and 'man dhcpcd.conf'

      #Include files from /etc/network/interfaces.d:
      source-directory /etc/network/interfaces.d

      auto lo  
      iface lo inet loopback

      iface eth0 inet manual

      allow-hotplug wlan0
      iface wlan0 inet manual
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

      allow-hotplug wlan1
      iface wlan1 inet manual
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

Change wlan0 config to static address:

    allow-hotplug wlan0
    iface wlan0 inet static
        address 10.1.1.31
        netmask 255.255.255.0
        gateway 10.1.1.1
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

address: is the address from the command above (or another unused address on the same network),
netmask: 255.255.255.0 corresponds to network size/24.
gateway: is the address of your router (or gateway).

The broadcast is automatically derived from address and netmask and need not be specified.
For more detail see https://wiki.debian.org/NetworkConfiguration
    
Now you have to set up WiFi configurations to join in your network

# WiFI config 

The file /etc/wpa_supplicant/wpa_supplicant.conf has ssid and password information, you should put yours there.

    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1

    network={
     ssid="ESSID"
     psk="Your_wifi_password"
    }
    
If you need to connect to a private network (i.e. no broadcast SSID) include the line scan_ssid=1 inside network={⋯}.

NOTE If you want to connect to different networks (e.g. at work or home) you can include multiple network={⋯} entries.
There are many other options which can be used see man wpa_supplicant.conf.

# Acknolagenmet:

  Thanks Miliway for this, I hope your solution can help a lot of people here..

bib:
----
    1 - Milliways' profile:
        https://raspberrypi.stackexchange.com/users/8697/milliways
    
    2 - When Milliways answer the question:
        https://raspberrypi.stackexchange.com/questions/37920/how-do-i-set-up-networking-wifi-static-ip-address/37921#37921?newreg=edb03c9d935f414e8484fbea44ae2b25
 
#PS:
    Feel free to comment, ask, criticism or suggest something to improve this.
