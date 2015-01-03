Steps for setting up local web server on Mac OS X
---

This guide references the following guides:
- [Apple Support Communities: Setting up a local web server on OS X](https://discussions.apple.com/docs/DOC-3083)
- [maketecheasier: How to Setup a Web Server in Mac OS X Mountain Lion](http://www.maketecheasier.com/setup-web-server-in-mountain-lion/)

There are plenty of guides on the web for setting up local web servers on Mac OS X Mountain Lion or later, with much better explanations.  The main purpose of this guide is to give the minimum set of instructions to get Apache running.

1.  Open terminal.
2.  `mkdir ~/Sites`
3.  `sudo vim /etc/apache2/users/<your short user name>.conf`
4.  For non-Yosemite, copy and paste into file:
```
<Directory "/Users/<your short user name>/Sites/">
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from localhost
</Directory>
```
5. For Yosemite, copy and paste into file:
```
<Directory "/Users/<your short user name>/Sites/">
    AddLanguage en .en
    LanguagePriority en fr de
    ForceLanguagePriority Fallback
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from localhost
     Require all granted
</Directory>
```
6. Exit and save (`esc`, then `:wq` or `:wq!`).
7. To run or stop Apache:
`sudo apachectl start`
`sudo apachectl stop`
8. `http://<your local host>/~<your short user name>/index.html` now corresponds to `~/Sites/index.html`.

