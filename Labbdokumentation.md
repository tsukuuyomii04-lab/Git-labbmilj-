Labbmiljö, Git, CLI och AI
Introduktion till yrkesrollen och grunderna i IT-infrastruktur (MYH 2025/4008)

Datum: 18-09-2026

Beskrivning: Ett LAN nätverk mellan två servrar med hjälp av VMs.
En servern har Ubuntu som OS och andra har WIN 11 som OS.


<h1>Nätverkstabell</h1>

| Host Name  |  OS  |  IP  | SubNetmask   | Gateway  |
|---|---|---|---|---|
| Laxa  |  Ubuntu |  192.168.50.10 | 255.255.255.0  |  Ingen |
| Windows  |  Windows 11|  192.168.50.20 |  255.255.255.0 |  Ingen |

<p>Båda servrarna konfigurerades med statiska IP-adresser på samma privata LAN-nätverk. Eftersom nätverket endast används för kommunikation mellan de två virtuella maskinerna behövs ingen standardgateway.</p>

<div>
<h1>Kommandoradsgenomförande </h1>

<h3>Ubuntu</h3>

<p> Följande kommandon användes för att skapa katalogen, gruppen och filen samt konfigurera ägarskap och behörigheter.</p>

<p> Skappning av Directory

1. Skapa Mappen

 mkdir -p /var/Systementor/konsultdata 

2. Skapa Filen

sudo touch var/Systementor/konsultdata/anteckningar.txt

3. Skapa Gruppen

sudo groupadd konsulter

4. Tilldela gruppen till katalogen

sudo chown :konsulter var/Systementor/konsultdata

5. Tilldela gruppen till filen

sudo chown :konsulter var/Systementor/konsultdata/anteckningar.txt

6. ändra filens behörigheter
   
 sudo chmod 640 var/Systementor/konsultdata/anteckningar.txt

 7. ändra katalogens behörigheter

 sudo chmod 750 var/Systementor/konsultdata

8. Resultat

ls -ld /var/Systementor/konsultdata

ls -l /var/Systementor/konsultdata/antecknignar.txt

</p>

<h3>IP configs</h3>
<p>


</p>

<h3>Windows</h3>
<p>
1. Kontrollerar Windows nätverkskonfiguration

ipconfig

2. Testa anslutningen

ping 192.168.50.10

3. Om det inte går för att firewall

New-NetFirewallRule -DisplayName "Allow ICMPv4-In" -Protocol ICMPv4 -IcmpType 8 -Direction Inbound -Action Allow

4. testa pingen igen 



</p>


<div><h1>Screenshots</h1>

</div>
</div>