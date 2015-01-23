[![](/wiki/icons/home.gif)](/wiki/Home.md) 

----------
## Introduction
As you may have noticed, from time to time there is a news article on the left side of the login screen for the WoW Client. Sometimes it can be annoying having a Blizzard notice that the servers are going down, when in reality, your server(s) is not going to be going down for maintenance in the foreseeable future.

Here are instructions on how to alleviate this problem for you and your players, should you have anyone else on your server:

## Disabling Breaking News
First, we need to go into our “hosts” file, which, depending on your operating system, will be in a different location. For Windows, the hosts file is in C:\Windows\System32\drivers\etc\hosts. In order to edit this file, though, you are going to have to go into your start menu, type notepad, right-click on notepad and run as administrator. Then just hit file, open, and navigate to the hosts file. For *NIX, the location of the “hosts” file is /etc/hosts.

Second, once you are editing the “hosts” file, you will need to go to the end of the file and enter the ip address of your server, in my case it would be 192.168.0.4. Then tab over to the space under “localhost” and enter the actual servername of the warcraft breaking news server, again, in my case it was “launcher.worldofwarcraft.com”. Depending on your region the address will be different. There will be a list of breaking news server later.

Finally, once you are done modifying your “hosts” file, you can restart the client and you will never see Blizzard’s breaking news again.

## “Pushing” Breaking News for your Server
In order to start “pushing” your own news, follow the instructions from Disabling Breaking News and then, once you have finished modifying your “hosts” file, come back to this section.
I’m assuming that you are using the WAMP server which covers both MySQL and Apache and are on Windows. If you are in *NIX, then you should not have to worry about MySQL and Apache as they should both already be installed, normally.

With our server configuration out of the way, we are ready to begin preparing to push our own news to our clients.

In the root web directory for your domain name or ip address, create a file called “Alert”. No quotation marks, no file extension, just Alert. And yes, capitalize the A. Alert is an over-simplified html file. As an example Alert file we have: 

`SERVERALERT:`

`<html><body><p>Your Message.</p></body></html>`

If you feel the need to disable your news system again at a future date, simply rename Alert to something like Alert2. When you want to re-enable your news system for a new tidbit of news, all you have to do is move Alert2 back to Alert and edit it.

## Blizzard’s Breaking News Servers
`US/SEA - http://launcher.worldofwarcraft.com/alert`

`LA - http://launcher.worldofwarcraft.com/es/alert`

`EN - http://status.wow-europe.com/en/alert`

`ES - http://status.wow-europe.com/es/alert`

`FR - http://status.wow-europe.com/fr/alert`

`DE - http://status.wow-europe.com/de/alert`

`RU - http://status.wow-europe.com/ru/alert`

`KR - ??? http://launcher.worldofwarcraft.co.kr/alert`

`CN - ??? http://launcher.battlenet.com.cn/alert`

`TW - ??? http://launcher.wowtaiwan.com.tw/alert`
