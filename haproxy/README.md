# Create self signed certificate:

From: [https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04#StepTwo%E2%80%94CreateaSelf-SignedSSLCertificate](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04#StepTwo%E2%80%94CreateaSelf-SignedSSLCertificate)

```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout haproxy.key -out haproxy.crt
```

Then, combine the two together in a PEM file:

```
cat haproxy.crt haproxy.key > haproxy.pem
```


Also see: [http://crohr.me/journal/2014/generate-self-signed-ssl-certificate-without-prompt-noninteractive-mode.html](http://crohr.me/journal/2014/generate-self-signed-ssl-certificate-without-prompt-noninteractive-mode.html)


