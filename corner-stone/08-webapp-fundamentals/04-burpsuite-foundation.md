## Introduction to Burp Suite
Burp suite is basically a java based framework built to be a full solution for web application penetration testing, its become the industry standard for hands on security assessments of web and mobile apps including ones relying on apis. What it actually does at its core is capture and let you manipulate all the http and https traffic going between a browser and a web server. By intercepting requests you get the flexibility to route them into different parts of the burp framework, and being able to intercept view and modify requests before they hit the target, or even manipulate responses before they reach your browser, is what makes it so valuable for manual testing

Burp comes in different editions. Community edition is free for non commercial use and is what well be focusing on. Professional is the unrestricted version with stuff like an automated vulnerability scanner, a fuzzer thats not rate limited, project saving and report generation, a built in api for integrating other tools, unrestricted extensions, and access to burp collaborator. Enterprise is different from both since its meant for continuous scanning, it sits on a server and constantly scans target web apps automatically instead of being used for manual local attacks like the other two editions

## Key Tools in Burp Suite
Even though community is more limited than pro it still comes packed with useful tools

- Proxy — the most well known part, lets you intercept and modify requests and responses while interacting with a web app
- Repeater — lets you capture modify and resend the same request multiple times, great for crafting payloads through trial and error like sql injection or testing an endpoint
- Intruder — sprays endpoints with requests, commonly used for brute forcing or fuzzing, though its rate limited in community
- Decoder — decodes captured info or encodes payloads before sending, other tools exist for this but having it built in is efficient
- Comparer — compares two pieces of data at word or byte level, quick to send data straight into it with a shortcut
- Sequencer — used to check the randomness of tokens like session cookies, if the algorithm generating them isnt secure it can expose serious attack paths

Burp is written in java which means extensions can be built for it in java python through jython or ruby through jruby. The Extender module lets you load extensions easily and the BApp Store is the marketplace for third party ones, some need a pro license but plenty are still available for community, like Logger++ which extends the built in logging

## Installing Burp Suite
Burp is useful for web or mobile assessments pentesting bug bounty or even just debugging during dev work. On the attackbox its already installed so no setup needed. Kali comes with it preinstalled too, and if its missing it can be grabbed from the kali apt repos. For other systems portswigger provides installers for windows mac and linux from their downloads page where you pick your os and select community edition

On windows you just run the executable, on linux you run the script from terminal with or without sudo, if sudo isnt used it installs into your home directory at ~/BurpSuiteCommunity/BurpSuiteCommunity and wont be added to path. The installer is generally safe to just accept defaults on but still worth reviewing as it goes

## First Launch and the Dashboard
After launching and accepting the terms youll pick a project type, community has limited options so you just click next. Next you choose your configuration, defaults are usually fine, then click start burp to open the main interface. First time users might see a training options screen which is worth going through when you have time

If you dont see that screen youll land on the burp dashboard which has four quadrants going counter clockwise from top left

- tasks — background tasks burp runs while you work, community defaults to live passive crawl which logs pages visited, pro has more like on demand scans
- event log — shows actions burp has performed like starting the proxy plus details on connections made through it
- issue activity — pro only, shows vulnerabilities found by the automated scanner ranked by severity and filterable by certainty
- advisory — gives detailed info on identified vulnerabilities including references and remediation suggestions, exportable into reports, community usually shows nothing here since theres no scanner

Question mark icons appear throughout burp and clicking them opens help info specific to that section, worth using whenever something is unclear

## Navigation
Navigation in burp mainly happens through the top menu bar where you switch between modules like proxy repeater etc, and if a module has sub tabs they show up in a second row right below the main bar. Tabs can also be detached into their own separate windows through the Window option in the app menu, and reattached the same way

There are keyboard shortcuts for jumping to key tabs

- Ctrl + Shift + D — Dashboard
- Ctrl + Shift + T — Target tab
- Ctrl + Shift + P — Proxy tab
- Ctrl + Shift + I — Intruder tab
- Ctrl + Shift + R — Repeater tab

## Configuring Settings
There are two types of settings, global aka user settings which affect the whole burp installation every time you open it, and project settings which only apply to the current session, community doesnt support saving projects so project specific settings get lost once you close burp

Settings are accessed through the Settings button in the top nav bar which opens a separate window with a menu on the left letting you search for specific settings by keyword, filter by user or project type, or browse by category. A lot of tools in burp also have shortcuts straight to their relevant settings category, like the proxy module having its own proxy settings button

## The Burp Proxy
The proxy is the core tool in burp, it captures requests and responses between the user and the target server, letting you manipulate them send them to other tools or just let them continue through

When requests come through the proxy theyre intercepted and held back from reaching the server, they show up in the proxy tab where you can forward drop edit or send them elsewhere. Clicking the Intercept is on button toggles this off so requests pass through uninterrupted. Even with interception off burp still logs all requests by default which is useful for reviewing later, and it also logs websocket communication. Logged traffic can be reviewed under HTTP history and WebSockets history

Proxy settings give a lot of control over its behaviour. Response interception is off by default and only happens per request unless you enable the rule based option to intercept responses more broadly. Match and Replace lets you use regex to modify requests and responses on the fly, like changing a user agent or messing with cookies

## Setting Up the Proxy with FoxyProxy
To actually use the proxy your browser needs to be configured to route traffic through it, using firefox with the foxyproxy extension for this

1. install the foxyproxy basic extension (already installed on the attackbox)
2. click the foxyproxy icon top right of firefox to open its options popup
3. click Options inside that popup which opens a new tab for foxyproxy configs, then click Add to make a new proxy config
4. fill in title as Burp, proxy ip as 127.0.0.1, and port as 8080
5. save the config
6. click the foxyproxy icon again and select the Burp config to activate it, burp needs to be running for requests to go through while this is active
7. switch to burp and make sure intercept is turned on in the proxy tab
8. open firefox and try visiting a site, the browser will hang and the request will show up in the proxy tab

Worth remembering that with the proxy active and intercept on your browser will hang on every request, so dont forget to turn intercept off when youre not actively using it. Right clicking a captured request also gives options like forward drop or sending it to other burp tools

## The Target Tab
The target tab does more than just control scope, it has three sub tabs

Site map builds a tree structure of the web app being tested, every page visited while the proxy is active gets logged here automatically just by browsing normally. Pro can also crawl automatically but even in community its useful for enumeration, especially for catching api endpoints the app hits behind the scenes

Issue definitions gives a full list of vulnerabilities the scanner looks for complete with descriptions and references, even without the actual scanner in community this list is useful for referencing in reports or describing something found manually

Scope settings lets you control what domains or ips are in or out of scope so you can focus only on the app youre actually testing instead of capturing everything

## The Burp Browser
Instead of manually configuring your normal browser burp also ships with a built in chromium browser thats already preconfigured to use the proxy with zero setup. You open it by clicking Open Browser in the proxy tab and any requests made in that window go through the proxy automatically

If youre running burp as root on linux like on the attackbox you might hit a sandbox error preventing the browser from starting. Two fixes for this, the proper way is running burp under a separate low privilege user, the quick way is going to Settings then Tools then Burps browser and checking Allow Burps browser to run without a sandbox, this is off by default for security reasons since a compromised browser without a sandbox could expose the whole machine, so its fine on something like the attackbox but should be used carefully elsewhere

## Scoping
Capturing everything gets overwhelming fast especially when you only care about one target. Scoping fixes this by defining what actually gets proxied and logged. Easiest way is going to the Target tab right clicking your target in the list on the left and choosing Add To Scope, burp will then ask if you want to stop logging anything out of scope which you usually want to say yes to

Scope settings sub tab under target lets you fine tune this by including or excluding specific domains or ips. Even with logging disabled for out of scope stuff the proxy still intercepts everything unless you also go to the proxy settings sub tab and enable And URL Is in target scope under Intercept Client Requests, this makes the proxy fully ignore anything outside the defined scope for a much cleaner view

## Installing the PortSwigger CA Certificate
When intercepting traffic on tls enabled sites like https://google.com/ you can run into an error saying the portswigger ca isnt trusted, this happens because the browser doesnt trust the cert burp is presenting. The attackbox already has this handled but heres the manual process

1. with the proxy active go to http://burp/cert to download a file called cacert.der
2. in firefox go to about:preferences and search for certificates then click View Certificates
3. in the certificate manager click Import and select the cacert.der file
4. check Trust this CA to identify websites and click OK

Once done you should be able to browse tls sites through the proxy without hitting the cert error anymore

## Real World Walkthrough Reflected XSS
Using a support form at MACHINE_IP/ticket/ as an example to test for reflected xss, which only affects the person making the request as opposed to other types of xss

Trying to type `<script>alert("Succ3ssful XSS")</script>` directly into the contact email field gets blocked by a client side filter that rejects special characters not allowed in emails. Client side filters like this are easy to bypass though

With the proxy active and intercept on, first submit the form with legit data like an email of pentester@example.thm and a query like Test Attack, the request gets caught by the proxy. From there edit the email field in the intercepted request to the actual payload, select it and url encode it with Ctrl + U to make it safe to send, then hit Forward. Doing this pops an alert box on the site confirming the xss worked