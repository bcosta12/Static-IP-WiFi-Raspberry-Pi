# Static-IP-WiFi-Raspberry-Pi

 This is tutorial explain how to set static IP on Raspberry Pi 3B. My objective is to save this knowledge and future users can find this solution here too. 

# Let's do it 

Go to 
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


    

# Acknolagenmet:
   Thanks, Professor Diego Haddad from CEFET/RJ to make this project possible and the followings websites that I learn how to do this project.

bib:
----
    1 - Milliways' profile:
        https://raspberrypi.stackexchange.com/users/8697/milliways
    
    2 - When Milliways answer the question:
        https://raspberrypi.stackexchange.com/questions/37920/how-do-i-set-up-networking-wifi-static-ip-address/37921#37921?newreg=edb03c9d935f414e8484fbea44ae2b25
 
#PS:
    Feel free to comment, ask, criticism or suggest something to improve this.
