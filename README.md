## Remove Server: Apache header
check header curl -v http://localhost:80/ | head

## edit /etc/apache2/conf-enabled/security.conf
```
ServerTokens OS to ServerTokens Prod
ServerSignature On to ServerSignature Off
```

## remove the word apache
```
sudo apt install libapache2-mod-security2
sudo a2enmod security2
apachectl -M | grep security
```

## edit /etc/apache2/apache2.conf
```
<IfModule security2_module>
    SecRuleEngine on
    ServerTokens Min
    SecServerSignature " "
</IfModule>
```
