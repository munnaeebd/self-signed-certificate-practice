# self-signed-certificate-practice
self-signed-certificate-practice

~~~
Step 1: Generate a Private Key
openssl genrsa -des3 -out server.key 1024

Step 2: Generate a CSR (Certificate Signing Request)
openssl req -new -key server.key -out server.csr

Step 3: Remove Passphrase from Key
cp server.key server.key.org
openssl rsa -in server.key.org -out server.key

signing the certificate:
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

 mv server.key ssl.key
 mv server.crt ssl.crt
 
 openssl x509 -in ssl.crt -text -noout
 
 docker build -t ssl-test1:1 .
 docker run -d -p 80:80 -p 443:443 ssl-test1:1
 ~~~
 
http://www.moserware.com/2009/06/first-few-milliseconds-of-https.html 
 
 
 
 
 
 
 
