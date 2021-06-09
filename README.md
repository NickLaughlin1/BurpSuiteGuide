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



