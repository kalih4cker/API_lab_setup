# API_lab_setup
This Repo contain the lab set up for API Pentesting
Burp Suite Community Edition
Burp Suite should come stock with the latest version of Kali, but if it does not then use the following command:

$ sudo apt-get install burpsuite -y

 Download Jython (https://www.jython.org/download.html) and add the .jar file to the Extension Options:



Under the Extension BApp Store search for Autorize and install the extension.

 

Proxy Traffic
An important aspect of API testing is being able to capture web application traffic as requests are made. In the course videos, I'll be using Foxy Proxy Standard and you are welcome to follow along using that. An alternative is using the built-in Burp Suite browser.

The Burp Suite Browser
The Burp Suite Browser is a convenient method of proxying traffic directly into Burp Suite. Later in the course, we will be reverse-engineering our own API documentation. If you'd like to follow along, that will be completed using Foxy Proxy.


Foxy Proxy Standard
While Firefox is open use the shortcut CTRL+Shift+A or navigate to https://addons.mozilla.org/en-US/firefox/addon.

Search for FoxyProxy Standard.
Add FoxyProxy to Firefox.
Install FoxyProxy Standard and add it to your browser.
Click the fox icon at the top-right corner of your browser (next to the URL) and select Options.
Select Proxies >Add New Proxy >Manual Proxy Configuration.
Add 127.0.0.1 as the host IP address.
Update the port to 8080 (Burp Suite’s default proxy settings).
Under the General tab, rename the proxy to BurpSuite.
Add a second new proxy:
Add 127.0.0.1 as the host IP address.
Update the port to 5555
Under the General tab, rename the proxy to Postman
 

Burp Suite Certificate
Start Burp Suite.
Open your browser of choice.
Using FoxyProxy, select the BurpSuite proxy. Navigate to http://burpsuite and click the CA Certificate. This should initiate the download of the Burp Suite CA certificate.
Save the certificate somewhere you can find it.
Open your browser and import the certificate. In Firefox, open Preferences and use the search bar to look up certificates. Import the certificate.

In Chrome, open Settings, use the search bar to look up certificates,
select More>Manage Certificates>Authorities, and import the certificate. If you do not see the BurpSuite cacert.der certificate. (You may need to expand the file type options to “DER” or “All files").



Now that you have the PortSwigger CA certificate added to your browser, you should be able to intercept traffic without experiencing issues.

 

MITMweb Certificate Setup
Now we will also import the cert for MITMweb through a very similar process.

Stop burpsuite (it's listening on 8080 and mitmweb needs that to work)
Start mitmweb from the terminal:
$mitmweb
Use FoxyProxy in Firefox to send traffic to the BurpSuite proxy (8080).
Using Firefox Visit mitm.it.

Download the mitmproxy-ca-cert.pem for Firefox. 
Return to the Firefox certificates (see Burp Suite Certificate instructions).

Import the MITMweb (mitmproxy-ca-cert.pem) certificate.

Install Postman
$ sudo wget https://dl.pstmn.io/download/latest/linux64 -O postman-linux-x64.tar.gz && sudo tar -xvzf postman-linux-x64.tar.gz -C /opt && sudo ln -s /opt/Postman/Postman /usr/bin/postman


Install Git
$ sudo apt-get install git

 

 Install Docker

$ sudo apt install docker.io -y

$ sudo apt-get install docker.io docker-compose

 

Install mitmproxy2swagger
$ git clone https://github.com/alufers/mitmproxy2swagger.git
$ cd mitmproxy2swagger
$ sudo docker build -t mitmproxy2swagger .
 

Install Go
$ sudo apt install golang-go

 

The JSON Web Token Toolkit v2
$ cd /opt

$ sudo git clone https://github.com/ticarpi/jwt_tool

$ cd jwt_tool

$ python3 -m pip install requirements.txt --break-system-packages


(Optional) Make an alias for jwt_tool.py

$ sudo chmod +x jwt_tool.py

$ sudo ln -s /opt/jwt_tool/jwt_tool.py /usr/bin/jwt_tool

 

Install Sublime Text
Install the GPG key:

$ wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/sublimehq-archive.gpg > /dev/null

Select the Stable channel:

$echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list

Update apt sources and install Sublime Text:

$sudo apt-get update

$sudo apt-get install sublime-text

 

Install Kiterunner
$ sudo git clone  https://github.com/assetnote/kiterunner.git

$ cd kiterunner

$ sudo make build

$ sudo ln -s /opt/kiterunner/dist/kr /usr/bin/kr

 

Install Arjun
$ sudo git clone https://github.com/s0md3v/Arjun.git

Recommended way to install arjun:

$ cd Arjun

$ pip3 install arjun

 

Install OWASP ZAP
$ sudo apt install zaproxy

(https://www.kali.org/tools/zaproxy/)

Once ZAP is installed, make sure to navigate to the Manage Add-Ons (CTRL+U). Make sure to apply updates for the Fuzzer and OpenAPI Support.

 

Useful Wordlists
SecLists (https://github.com/danielmiessler/SecLists)

$ sudo wget -c https://github.com/danielmiessler/SecLists/archive/master.zip -O SecList.zip \
&& sudo unzip SecList.zip \
&& sudo rm -f SecList.zip

Hacking-APIs (https://github.com/hAPI-hacker/Hacking-APIs)

$ sudo wget -c https://github.com/hAPI-hacker/Hacking-APIs/archive/refs/heads/main.zip -O HackingAPIs.zip \
&& sudo unzip HackingAPIs.zip \
&& sudo rm -f HackingAPIs.zip

Once you have these tools installed and updated you should be ready to proceed to the next module.
