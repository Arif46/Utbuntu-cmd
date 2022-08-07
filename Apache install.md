## install apache 

```
sudo apt update
```
## then install Apache
```
sudo apt install apache2
```
------You’ll also be prompted to confirm Apache’s installation by pressing Y, then ENTER-----

## Once the installation is finished, you’ll need to adjust your firewall settings to allow HTTP traffic. UFW has different application profiles that you can leverage for accomplishing that. To list all currently available UFW application profiles, you can run:

``` 
sudo ufw app list
```

----------------------You’ll see output like this:---------------

Output
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH

  Here’s what each of these profiles mean:

Apache: This profile opens only port 80 (normal, unencrypted web traffic).
Apache Full: This profile opens both port 80 (normal, unencrypted web traffic) and port 443 (TLS/SSL encrypted traffic).
Apache Secure: This profile opens only port 443 (TLS/SSL encrypted traffic).
For now, it’s best to allow only connections on port 80, since this is a fresh Apache installation and you still don’t have a TLS/SSL certificate configured to allow for HTTPS traffic on your server.

To only allow traffic on port 80, use the Apache profile:

## To only allow traffic on port 80, use the Apache profile:
```
sudo ufw allow in "Apache"
```

## You can verify the change with:
```
sudo ufw status
```

Output
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                                
Apache                     ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)                    
Apache (v6)                ALLOW       Anywhere (v6)   

## You can do a spot check right away to verify that everything went as planned by visiting your server’s public IP address in your web browser (see the note under the next heading to find out what your public IP address is if you do not have this information already):

```
http://your_server_ip
```
