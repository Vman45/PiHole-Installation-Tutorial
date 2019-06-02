# Windows Tutorial for Installing Pi-Hole (and more!)
<p align="center">
<a href="https://pi-hole.net"><img src="https://pi-hole.github.io/graphics/Vortex/Vortex_with_text.png" width="150" height="255" alt="Pi-hole"></a><br/>
<b>Network-wide ad blocking via your own Linux hardware</b><br/>
</p>

The Pi-hole[®](https://pi-hole.net/trademark-rules-and-brand-guidelines/) is a [DNS sinkhole](https://en.wikipedia.org/wiki/DNS_Sinkhole) that protects your devices from unwanted content, without installing any client-side software.

- **Easy-to-install**: our versatile installer walks you through the process, and [takes less than ten minutes](https://www.youtube.com/watch?v=vKWjx1AQYgs)
- **Resolute**: content is blocked in _non-browser locations_, such as ad-laden mobile apps and smart TVs
- **Responsive**: seamlessly speeds up the feel of everyday browsing by caching DNS queries
- **Lightweight**: runs smoothly with [minimal hardware and software requirements](https://discourse.pi-hole.net/t/hardware-software-requirements/273)
- **Robust**: a command line interface that is quality assured for interoperability
- **Insightful**: a beautiful responsive Web Interface dashboard to view and control your Pi-hole
- **Versatile**: can optionally function as a [DHCP server](https://discourse.pi-hole.net/t/how-do-i-use-pi-holes-built-in-dhcp-server-and-why-would-i-want-to/3026), ensuring *all* your devices are protected automatically
- **Scalable**: [capable of handling hundreds of millions of queries](https://pi-hole.net/2017/05/24/how-much-traffic-can-pi-hole-handle/) when installed on server-grade hardware
- **Modern**: blocks ads over both IPv4 and IPv6
- **Free**: open source software which helps ensure _you_ are the sole person in control of your privacy

## Buying a Raspberry Pi
You can buy a Raspberry Pi 3 through the official store linked [here](https://raspberry.piaustralia.com.au/raspberry-pi-3-model-b).

## Setting Up
*Should also work for any version of the Ubuntu Server builds*

Visit the [ubuntu downloads page](https://www.ubuntu.com/download/iot/raspberry-pi-2-3) and follow the instructions.
- Make sure your downloaded file is a `.img` or `.img.xz` (latter needs to be extracted using 7zip or alternative)
- Download [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/files/latest/download) or another flashing software of your choice
- Flash the `ubuntu-18.04.x-preinstalled-server-arm64+raspi3.img` to your microSD card

## Installing Ubuntu Server 18.04.x LTS on the Raspberry Pi
Insert the card into your Raspberry Pi 3 and let it install. You will be prompted for a password which by default is:  
- Username: `ubuntu`
- Password: `ubuntu`

You will be asked to change the default password after.

After the installation has completed, restart your Raspberry Pi 3 with the following command:  
`sudo reboot`

Once Ubuntu Server has restarted, login with your new details. Now, we need to ensure that everything is updated to the latest version (2-5mins). To do so, we can use the following command:  
`sudo apt-get update && sudo apt-get upgrade -y && sudo reboot`

Once this is completed, we can move onto installing Pi-Hole

## One-Step Automated Install
The most convenient method of installing Pi-Hole is to use the command:

`sudo curl -sSL https://install.pi-hole.net | bash`

When prompted, allow for the Web Interface to be installed.

As for the DNS server, you may pick any one of your choice (Though I would reccomend using a DNS with ECS).

*If this doesn't work out, or you would like an alternative approach, you can visit the [official repo](https://github.com/pi-hole/pi-hole) for more details.*

## Finalising the Settings
You can now access the Web Interface by going to your Rpi's IP address (use the command `ip a` if you don't know it) and change the settings. 

Once you're in, go to Settings and tick the "Enable `DHCP`" setting. **IMPORTANT:** you will need to go to your modem's settings and *untick* DHCP so that *only* your Rpi is being used to allocated IP's. 

Restart your devices that you wish to connect so that the IP lease is renewed.

After this, you'll be done!

## Post-Installation
- I highly reccomend you add (dbl.oisd.nl) to your block lists as it is updated frequently and covers pretty much all there is.
- If you would ever like to SSH to your device, I recommend [MobaXterm](https://mobaxterm.mobatek.net/) as your go-to terminal for Windows users. Just connect to your Rpi's IP address with the details you created in the initial setup.
