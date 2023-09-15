1.How many open TCP ports are listening on nibbles?
First what we need to do is check what's happend on the server and how many ports are open.
We don't see nothing intresting, only some SSH and HTTP. Let's go dipper to find something more intresting.

![obraz](https://github.com/Anogota/Nibbles/assets/143951834/f41ed141-e648-4f40-b5d2-ebc17c793eff)

2.What is the relative path on the webserver to a blog?
First what i did is go to website, but there is nothing intresting, only Hello world!
But when i check the source code i found <!-- /nibbleblog/ directory. Nothing interesting here! -->
This looks very intresting and this also the answer for as question :)

3.What content management system (CMS) is being used by the blog??
I check the source code but there is nothing intresting, i recommend to install extensions wallalyzer, this extension help mi figure out what kind of software running on the server, but in this situation, wapalyzer don't detect the CMS lol :P
Next my think is maybe to find some switch for nmap to detect the CMS. I found this --script=http-enum but still i don't have any idea what kind of CMS is this.
After few min, checking the webpage i found in right corner: Powered by nibbleblog, lol

4.What is the relative path to an XML file that contains the admin username?
I used feroxbuster, with this tool you can, forced browsing is an attack where the aim is to enumerate and access resources that are not referenced by the web application, but are still accessible by an attacker. feroxbuster uses brute force combined with a wordlist to search for unlinked content in target directories
I found this:

![obraz](https://github.com/Anogota/Nibbles/assets/143951834/5d3e718a-289f-498e-9552-6ddeae9c8f2f)
