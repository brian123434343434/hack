# hack
script_pentestig
#!/bin/bash
$url
$varsqlmap
$sqlmapurl
echo 'Introduzca el dominio o ip:'
read url
echo "Startup"
whois $url
firefox "site:$url type:pdf"
theharvester -d $url -b all
nmap -T4 -A -v -Pn $url
xprobe2 $url
sslscan -no-failed $url
nikto -host $url
echo 'Se va a ejecutar SlqMap, introduzca la url a consultar tiene que tener una sintaxis como esta http://ejemplo.com/login.php?
user=miguel&password=12345:'
read sqlmapurl
echo 'Luego la variable a analizar por ejemplo si tenemos la URL http://ejemplo.com/login.php?
user=miguel&password=12345 y se va a analizar password, introducir password "Si no quiere ejecutar SqlMap oprima Crtl+C"'
read varsqlmap
sqlmap -u "$sqlmapurl" -p $varsqlmap --tamper=apostrophemask,apostrophenullencode,appendnullbyte,base64encode,between,bluecoat,chardoubleencode,charencode,charunicodeencode,concat2concatws,equaltolike,greatest,halfversionedmorekeywords,ifnull2ifisnull,modsecurityversioned,modsecurityzeroversioned,multiplespaces,nonrecursivereplacement,percentage,randomcase,randomcomments,securesphere,space2comment,space2dash,space2hash,space2morehash,space2mssqlblank,space2mssqlhash,space2mysqlblank,space2mysqldash,space2plus,space2randomblank,sp_password,unionalltounion,unmagicquotes,versionedkeywords,versionedmorekeywords
