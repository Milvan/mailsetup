# Installation

```
sudo apt-get install postfix
```

# Configure settings 

```
sudo vim /etc/postfix/main.cf
```

```
sudo vim /etc/postfix/virtual
```

## Fix a relay
currently using free smtp relay mailjet
configure /etc/postfix/main.cf accordingly


# Start service

```
sudo postmap /etc/postfix/virtual
```

```
sudo service postfix reload
```


# Check mail status

sudo service postfix status

# Check emails 

less /var/mail/marcus

# Send emails

Edit file testemail

```
sendemail recipient_address@gmail.com < testemail
```


#Troubleshooting
check that smtp is running

```
sudo netstat -pel | grep smtp
tcp 0 0 *:smtp *:* LISTEN root 8487 2212/master
```
Then we use the 2212 from that in the following to get the package:

```
$ dpkg -S "$(sudo ps ux | grep 2212 | awk '{print $NF}')"
```
