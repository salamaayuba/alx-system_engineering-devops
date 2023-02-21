What's the Linux Hosts File?
The hosts file is a plain text file that all operating systems use to translate hostnames (also known as web addresses or URLs) into IP addresses. When you type in a hostname, such as wikipedia.org, your system will look into the hosts file to get the IP address needed to connect to the appropriate server.

If you open the hosts file, you'll quickly notice that it doesn't have the directory of the entire internet in there. Instead, there might be just a couple of lines and that's it. What gives?

Turns out, your system will check the hosts file first before looking up a site on the DNS servers defined in your network settings (usually your ISP's DNS servers).

This means that you can use the hosts file to add to what the DNS servers can't provide (such as aliases for locations on your local network, which is otherwise only possible if you have a DNS server set up within your local network) or override the IP addresses that your DNS servers would normally provide.

For example, if you ask for wikipedia.org, the DNS servers will return Wikipedia's IP address to your computer. But if you wanted to block Wikipedia on that computer, you can add an entry in the hosts file that tells your computer that wikipedia.org points to some other IP address that's different from Wikipedia's actual IP address.


Before DNS came online, this file held all the hostnames and IP addresses for the entire internet. System administrators would periodically download updated copies of this file from a central repository. Even by the early 1980s, it was almost impossible for admins to keep up as more and more hosts came online even when the network was still mostly limited to universities and research labs, so DNS was created.

This made the hosts file largely obsolete when dealing with the public internet or even more than a few machines, but it's perfect for managing your local machine and a small local network like your Wi-Fi.

Nowadays, this file will typically have the hostname you chose for the Linux machine when you installed it and the localhost defined, which is the minimum required to use the network.

The Linux Hosts File's Location
On Linux, you can find the hosts file under /etc/hosts. Since it's a plain text file, you can open the hosts file using your preferred text editor.

Since the hosts file is a system file, you'll need administrative rights to save changes. To edit the file using a Linux terminal-based text editor such as nano, you'll need superuser access.


For example:

sudo nano /etc/hosts
To use a graphical text editor such as gedit:

gksu gedit /etc/hosts
Once you've finished editing the file, exit the editor. In nano, hit Ctrl + X, and then y to confirm overwriting the changes. It's a good idea to save a backup copy of the file before you edit it so you can restore it if you make a mistake because it could mess with your network access.

To make a backup of the hosts file, just make a copy of it. You might add a suffix like .old so you remember that this is an old copy of the file:

sudo cp /etc/hosts /etc/hosts.old
How to Add Sites to the Hosts File
hosts_file_example
In the hosts file, each entry has its own line. The syntax is simple. Type the IP address you want the hostname to translate to, press the Tab key on your keyboard, and then type the hostname.

For example, to block Wikipedia, you'd type (remembering to use the Tab key rather than Space):

127.0.0.1        wikipedia.org
127.0.0.1 is the loopback IP address that will always point back to your own system. Since the web isn't stored on your machine, your browser will say the site can't be found. It is now effectively blocked.

If you feel intimidated by the terminal, check out Linux Mint's Domain Blocker application (also known as mintnanny). It will add entries into the hosts file that point the hostnames you specify to 127.0.0.1. But to do anything else, you will still need to make changes with a text editor.

Download: Domain Blocker (Free)

linux mint domain blocker
Create Shortcuts in the Hosts File
The other way that the hosts file is useful is in creating easy-to-remember names of machines on a small office or home network.

If you have a computer on your home network (say with an IP address of 192.168.1.10) that has a simple website or file server that does something useful for you, you can type the following in your hosts file:

192.168.1.10        homeserver
Then, if you open your browser and just type:

http://homeserver
Your computer will now automatically redirect to 192.168.1.10. It's much easier than having to lookup an IP address. You can permanently assign an IP address to any machine on your network using your Wi-Fi router's configuration menu.

Alternatively, you can use the hosts file to create shortcuts to certain sites on the web. Use a command such as nslookup to find a website's IP address, then add it to your hosts file alongside the desired shortcut, just as in the example above. Since most major websites have multiple IP addresses, this might not work on sites like Google or Netflix.

Potential Issues With the Hosts File
So we've established how to make changes to the host file, but you may still run into issues when using Google Chrome. This web browser tends to ignore the hosts file unless you do one of two possible things:

Type http:// at the beginning of each address. For example, if you have Wikipedia blocked in the hosts file, then Chrome will circumvent the block if you just type wikipedia.org into the address bar. However, if you type http://wikipedia.orginto the address bar, it will follow the hosts file.
Disable the "Use a web service to help resolve navigation errors" option in Chrome Settings and then you won't have to type http:// at the beginning every time. This is one of several Google Chrome privacy tips worth doing anyway.
How Will You Change the Hosts File?
The hosts file offers an easy way to block access to certain websites on your computer as well as create names for any home servers that are easy to remember.

If you have kids, it's a crude but effective way to block sites you may not want them to see or limit screen time, at least as long as they don't have superuser access. There are other tools available that allow you to limit internet access and screen time on Linux.
