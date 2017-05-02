# Project 10 - Honeypot

Time spent: **1** hours spent in total

> Objective: Setup a honeypot and provide a working demonstration of its features.

### Required: Overview & Setup

- [X] A basic writeup (250-500 words) on the `README.md` desribing the overall approach, resources/tools used, findings

	  I haven't had much luck with Vagrant or Docker in previous assignments and decided to look for solutions that only required VirtualBox. I've been using VirtualBox for years and it just felt like the best option for me.
	  Initially, I thought this would mean finding a Linux distribution similar to Kali Linux but built to be used as a honeypot rather than a pentesting suite. After some googling I found HoneyDrive.
	  
      HoneyDrive is a preconfigured VirtualBox appliance. It comes fully loaded with Apache2 and MySQL, Wordpot Wordpress Honeypot, and a collection of other honeypot, security, and analysis tools. 
	  It uses the Xubuntu Desktop as a base distro and setup is fully automated due to it being a VirtualBox appliance. After downloading it only takes a few steps to import into VirtualBox. All in all, it took about 5 minutes to get to
	  the Xubuntu Desktop. However, the process only involved 30 sections of actual interaction. The rest of it was spent waiting for the appliance to set itself up. The only configuration I had to do after that point was
	  setting up port forwarding so that HoneyDrive could communicate through to my host machine and the outside world.
	  
	  HoneyDrive had many options for setting up a honeypot. After reviewing my options I decided to setup an SSH honeypot using the included Kippo SSH honeypot. In addition to Kippo, a utility called Kippo-Graph is included
	  in HoneyDrive which visualizes the information that Kippo is able to capture. Much like the setup of HoneyDrive itself, Kippo and Kippo-Graph were preconfigured and only took a single command to get running.
	  
	  Kippo is a
	  
- [x] A specific, reproducible honeypot setup, ideally automated. There are several possibilities for this:
	- HoneyDrive is available for download here: http://bruteforcelab.com/honeydrive
	- Setup is as simple as opening the OVA file.

### Required: Demonstration

- [x] A basic writeup of the attack (what offensive tools were used, what specifically was detected by the honeypot)

	Since I setup an SSH honeypot I needed to perform an SSH attack. I decided a bruteforce attack would be the best way to demonstrate the functionality of Kippo and Kippo-Graph. I decided to use Ncrack. Ncrack is a command utility
	that lets you issue a bruteforce attack against a suite of network protocols, including SSH. In addition, I needed a password list. I grabbed the very popular "john.txt".
	
	With these ready to go, the attack just required giving Ncrack the password list and the IP of my HoneyDrive setup.

- [x] An example of the data captured by the honeypot (example: IDS logs including IP, request paths, alerts triggered)
	
	Kippo collects a lot of information about SSH login attempts. Among other things, this includes attempted username and password combinations, the IP addresses of the attackers, the SSH client being used, and whether or not any attempts were successful or not.
	
	Kippo-Graph takes this information and presents it in an easy to digest and informative way. It includes things like most commonly attempted passwords, usernames, the most used combinations of the two. It also lets you download
	a comma seperated value file of the distinct passwords used which unsurprisingly matched the "john.txt" file I used in the attack.
	
	My favorite feature of Kippo-Graph was a map with hotspots based on where the attacks are coming from and links to easily look up the attackers IPs on websites like McAfee. 
	
	Included is an example of how useful Kippo can be in identifying when an attacker attempts an SSH bruteforce. The 10.0.2.2 address is my host computer running the attack.
	
	![Screenshot](http://i.imgur.com/myzppSl.png)

- [x] A screen-cap of the attack being conducted

  ![Screenshot](http://i.imgur.com/4gkz2d4.png)

