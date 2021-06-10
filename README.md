# Burp Suite Demo
This is a demo on getting Burp Suite set up on your local machine

## Download Burp Suite
- To install Burp Suite Community Edition go to: https://portswigger.net/burp/communitydownload. <br />
- Run the installation wizard to finish installing Burp Suite
- On MacOS you may get an error saying that the installer "can't be opened because Apple cannot check it for malicious software". If this happens, do the following: <br />
  1. Close the error message popup
  2. Go to "Systems Preferences" > "Security & Privacy"
  3. At the bottom of the dialog, you will see a message saying that the Burp Suite installer was blocked. Next to it, click "Open anyway"
  4. The initial error message will pop up agian, but this time you have the option to click "Open" to run the installer despite the warning

## Starting Burp
- After running the installation wizard open "Burp Suite Community Edition"
- When Burp opens you can select to open a temporary project, create a new projec that will save on the disk, or open up an existing project. For now we are going to open up a temporary project
- On the next screen it will ask if you want to load the Burp default settings, the settingns from the project being opened, or load your own configuration file. We are just going to select Burp defaults
### Checking default Proxy Settings
- When the Burp project opens click on the "Proxy" > "Options" and confirm that the Proxy Listener that is active is: 127.0.0.1:8080
![proxyoptions](https://user-images.githubusercontent.com/40414269/121556975-59201a00-c9e2-11eb-9252-5e7d39808282.gif) <br />
- While still under the "Proxy" tab select "Intercept" and click "Intercept is on" to turn the intercept off
![turninterceptoff](https://user-images.githubusercontent.com/40414269/121557413-bae08400-c9e2-11eb-8a63-c64b22d9ce21.png)

## Configuring Proxy Settings For Browser
### FireFox w/ FoxyProxy (Probably the easiest set up)
- Download FoxyProxy here: https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/
- Open FoxyProxy extension and click on options <br />
  ![foxyoptions](https://user-images.githubusercontent.com/40414269/121427073-46ee9f00-c942-11eb-9cb1-bfda406fbdba.png) <br />
- Once in options click "Add" on the left side <br />
  ![foxyadd](https://user-images.githubusercontent.com/40414269/121427072-46ee9f00-c942-11eb-9640-7db982bfe2a2.png) <br />
- Change the following settings:
  * Set a name/title for the proxy
  * Keep the Proxy Type as: HTTP
  * Change Proxy IP address to: 127.0.0.1
  * Change Port to: 8080
  * Leave Username and Password fields empty
- Save the proxy settings
- Turn on the Proxy <br />
![foxyTurnOn](https://user-images.githubusercontent.com/40414269/121427074-47873580-c942-11eb-8248-3cb0f61f4436.png) <br />

### Chrome and Safari
- I am not going to detail how to set up Chrome since you have to use Internet Explorer to download Burp Suites Certificate to browse HTTPS sites
- I'm also not going to detail how to set up Safari as I cannot fully test it to make sure everything works properly
- If you wan't to use Chrome or Safari check out this resource: https://portswigger.net/burp/documentation/desktop/getting-started/proxy-setup/browser

## Install the CA Certificate for Corresponding Browser
Now that a proxy is set up in your browser, you will need to install Burp's CA certificate to capture HTTPS traffic through Burp.
### Installation Process if using FireFox
- Now that a proxy is on via FoxyProxy and you have your Burp project up and running with Intercept off, visit this link in FireFox: http://burpsuite
