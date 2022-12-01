# How-to-Setup-in-aws-Godaddy-SSL-on-AWS-EC2-2-
How to Setup Godaddy SSL on AWS EC2 (2)
How to Setup Godaddy SSL on AWS EC2

Step-1
Generate local key 
Generate key in any new folder /home/ec2-user/blvd

Run the command inside blvd folder

$ sudoopensslgenrsa -out localhost.key 2048




Local key in side folder









Step-2 Request for csr
Run the command 
$ sudoopensslreq -new -key localhost.key -out csr.pem

After this command fill the detail accordingly required












Step-3
Open csr in edditor and login to godaddy =>ssl certificate => under drop down manage domain.
Copy and past csr key to Re-Key you certificate then Add change and submit and done.



Step -4
After submitting refresh  the page where you get download zip option select as your server type.




Now locate the ssl.conf. In my case it was in /etc/apache2/sites-available

Step -5
$ sudo nano ssl.conf

Open and change the path for 
SSLCertificateFile /home/ec2-user/blvd/localhost.crt 
SSLCertificateKeyFile /home/ec2-user/blvd/localhost.key
SSLCertificateChainFile /home/ec2-user/blvd/gd_bundle-g2-g1.crt


Before change unzip rename the file and move the both .crt file to blvd folder with the name 








Step -6
Save and exit 

Step -7
$ sudosystemctl restart apache2

Done Check the Website.

Video Link https://www.youtube.com/watch?v=ovP9h3JUyQE





