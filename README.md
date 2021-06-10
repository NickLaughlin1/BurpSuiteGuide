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
- Once there, click the CA Certificate in the top right corner to download (take note where this is saved)
![CAcert](https://user-images.githubusercontent.com/40414269/121567198-4ca0bf00-c9ec-11eb-9aa9-9d51a7aca9e4.png)
- Open up FireFox preferences by clicking the burger menu > "Preferences" (or "Settings")
- Open the "Privacy and Security" settings found on the left side and scroll down until you see the "Certificates" section
- Once there click on "View Certificates" > "Import" and select the Burp CA certificate that you downloaded earlier
![import](https://user-images.githubusercontent.com/40414269/121567705-e5373f00-c9ec-11eb-9d50-be3bca978592.png)
mport"
- When prompted, make sure to check "This certificate can identify websites" is selected and click "OK"
- Now close and restart FireFox and you should now start to see your traffic being recorded through Burp under the "Proxy" tab > "HTTP History"

### Installation Process for Other Browsers
- You can find the steps to install the CA Certificate for other browsers here: https://portswigger.net/burp/documentation/desktop/getting-started/proxy-setup/certificate

## Burp Features
Now that we have Burp installed and your browser set up we can start looking at some of the features that Burp offers. While Burp offers many useful tools/features, in this demo we are going briefly explain these five:
  * Target
  * Proxy
  * Intruder
  * Repeater
  * Decoder <br />

For a more in depth explanation of these five (and many more) tools: https://portswigger.net/burp/documentation/desktop/tools
### Target
The Target tab allows you access three different tabs: Site map, Scope, and Issue Definitions. <br /> Here is a brief description of each tab: 
- Site map
  * From Burps website "The left-hand-side tree view contains a hierarchical representation of content, with URLs broken down into domains, directories, files, and parameterized requests. You can expand interesting branches to see further detail. If you select one or more parts of the tree, the relevant details about all the selected items and items in child branches are shown in the right-hand-side view."
  * ![sitemapleft](https://user-images.githubusercontent.com/40414269/121573175-ef5c3c00-c9f2-11eb-840f-ff946be3fc6c.png)
  * The tree view icons also provide a visual indication of the most significant security issue that has been identified within each branch
  * For more on Site Map: https://portswigger.net/burp/documentation/desktop/tools/target/site-map
- Scope
  * The Scope allows you to filter what Burp will/will not capture from your traffic
  * For example, here I am specifying that I only want to see traffic coming from https://www.techsmith.com and nothing else. I could do the opposite and block all traffic from just https://www.techsmith.com if I move the entry to the "Exclude from Scope" section <br />
   ![scopeexample](https://user-images.githubusercontent.com/40414269/121574336-27b04a00-c9f4-11eb-9f41-0cd892d82108.png)
  * For more information regarding Scope visit: https://portswigger.net/burp/documentation/desktop/tools/target/scope
- Issue Definitions
  * This tab lists the definitions of all issues that can be detected by Burp Scanner
 
 ### Proxy
 The Proxy tab is where you will monitor the traffic that Burp is intercepting. <br />
 Here is a brief description of each tab you will find under Proxy: <br />
 - Intercept
  * From Burps website: "The Intercept tab is used to display and modify HTTP and WebSocket messages that pass between your browser and web servers."
  * You can configure exactly what HTTP requests and responses are stalled for interception
  * For more details on Intercept: https://portswigger.net/burp/documentation/desktop/tools/proxy/intercept
 - HTTP History
  * This tab shows the HTTP history captured by Burp and displays information about it. This information includes the Host, HTTP Method, URL file path & query string, a Params flag, flag indicating if request was modified by user, status code, byte length of request, MIME type, extension, etc.
    ![httphistory](https://user-images.githubusercontent.com/40414269/121576280-37c92900-c9f6-11eb-97b9-97fd8a3b5e66.png)
  * Left clicking on an entry will show the request and the response
  * Right clicking allows you to do a variety of things to the request including:
      * Adding to Scope
      * Sending to Intruder, Repeater, Sequencer, Comparer
      * Add comment to request
      * Delete the request from the history
      * etc
        ![historyoptions](https://user-images.githubusercontent.com/40414269/121576861-d786b700-c9f6-11eb-88f4-620b26a1bf60.png)
- WebSockets Hisory
  * This tab works similarly to HTTP History
- Options
  * This tab allows you change the Proxy and Intercept settings
  * For more information on the options tab visit: https://portswigger.net/burp/documentation/desktop/tools/proxy/options

### Intruder
Burp defines the Intruder tool as a means "for automating customized attacks agains web applications. It is extremely powerful and configurable, and can be sued to perform a huge range of tasks, from simple brute-force guessing of web directories through to active exploitation of complex blind SQL injection vulnerabilities." There are many type of attacks that you can perform and ways to customize those attacks. This is a quick example of how you could potentially use the Intruder tool:
- The first tab you will see is "Attack Target" and here you can specify the host and port of the target. If a request was sent over from the HTTP History section then this will already be filled in
- Next is the positions tab and this is where you specify which paramters you want the Intruder to modify. The selected positions are indicated by a green highlight and being surrounded by this character: §
![positions](https://user-images.githubusercontent.com/40414269/121578973-42d18880-c9f9-11eb-94e0-9aa096f7d6f5.png)
  <br />Here you can also change your attack type. For more information on attack types check out the link at the end of this section.
- After selecting the positions it is time to define the payload that will fill those positions. Here there are numerous payload types and for this example we will select the numbers payload <br />
 ![payloadnumber](https://user-images.githubusercontent.com/40414269/121579565-d3a86400-c9f9-11eb-82e8-7764d8d50148.png)
  <br /> In this payload type we can set the range of numbers to be inserted into the position(s), if those numbers will be inserted sequentially or random, whether or not to skip any numbers, send decimal or hex, max and min integer digits and/or fraction digits <br />
  ![payloadoptions](https://user-images.githubusercontent.com/40414269/121580914-46660f00-c9fb-11eb-90c5-7e7de3be24bd.png) <br />
  For this example we are going to send a payload that includes numbers 1-4 and doesn't skip any of the numbers (step = 1). If step = 2 then the payload would be: 1,3 because it does every other number (and if step = 3 then payload would be 1,4)
- (Optional) You can add payload processing that will added to the payload before it is used. This could be encoding/decoding the payload entries, hash them, adding prefix/suffix, reverse entry, etc.
- (Optional) You can add Payload URL-encoding to certain characters defined in this section
- For more information on the Intruder visit: https://portswigger.net/burp/documentation/desktop/tools/intruder

### Repeater
Burp defines the Repeater as "a simple tool for manually manipulating and reissuing individual HTTP and WebSocket messages, and analyzing the application's responses." You can use the Repeater to change parameter values, change HTTP request type, test logic flaws by issuing requests in a specific sequence, etc. <br />
Once you are done making changes to the request you can send it and see the response <br />
![repeater](https://user-images.githubusercontent.com/40414269/121582035-88438500-c9fc-11eb-8939-09011393f53d.png) <br />
- For more information on the Repeater visit: https://portswigger.net/burp/documentation/desktop/tools/repeater

### Decoder
The Decoder does exactly what you would think it does: decodes passed in values. It also has the ability to encode and/or hash the value passed in a variety of different ways. <br />
For example, here is a a value that is getting base64 encoded and then decoded to give the original value <br />
![decoder](https://user-images.githubusercontent.com/40414269/121582745-5da5fc00-c9fd-11eb-948c-59f30b922392.png) <br />
For more information on the decoder visit: https://portswigger.net/burp/documentation/desktop/tools/decoder
