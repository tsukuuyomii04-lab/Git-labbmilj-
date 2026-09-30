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

<h3>IP configs med NetworkManager</h3>
<p>

1. Check ip

    Ip add

2. visa routing table

    Ip route 

3. Update Ubuntu server

    sudo apt update

4. Install Network-manager if u want it

    sudo apt install network-manager

5. starta det network-manager

    sudo systemctl start NewtworkManager

6. enable network-manager

    sudo systemctl enable NetworkManager

7. Checka att den är aktiv

    systemctl is-active NetworkManager

8. Checka network interfaces 

    nmcli device status 

9. Checka vilka available connections det finns 

    nmcli connection show

10. create labnet 
    
    sudo nmcli connection add type ethernet ifname enp0s8 con-name [Din valda Namn till nätverket] ipv4.method manual ipv4.addresses [Din Valda IP]
    
    
11. starta ditt nätverk

    sudo nmcli connection up labnet 

12. checka igen  

    ip add

13. checka route igen 

    ip route 

14. checka connection med Windows server

    ping -c [din valda ip address]


</p>

<h3>Skapning av mappar o användare</h3>

<p> Följande kommandon användes för att skapa katalogen, gruppen och filen samt konfigurera ägarskap och behörigheter.</p>

<p>

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

<h3>Windows</h3>

<h3>Windows Network Configs</h3>
<p>
1. Kontrollerar Windows adapters

    Get-NetAdapter

2. visa ip config

    Get-NetIPConfiguration 
3. Visa nuvarande Ip address 
   
    Get-NetIPAddress

4.  Ge ny ip address
   
   New-NetIPAddress -InterfaceAlias "Ethernet" -IPAddress 192.168.50.20 -PrefixLength 24

5. Checka Statisk ip address

    Get-NetIPAddress -InterfaceAlias "Ethernet"

6. Testa anslutningen till linux server

    ping [din valda ip]

7. Om det inte går för att firewall

    New-NetFirewallRule -DisplayName "Allow ICMPv4-In" -Protocol ICMPv4 -IcmpType 8 -Direction Inbound -Action Allow

8. testa pingen igen 

    ping [din valda ip]

</p>

<h3>Windows Katalog & Användare</h3>
<p>
1. skapa mapp 

    mkdir C:\Systementor\KonsultData

2.checka behörigheter 

    Get-Acl C:\Systementor\KonsultData




</p>


<h2>Git & Versionshantering</h2>

<p>
git log --oneline

ecda917 (HEAD -> main, origin/main) All nätverks Step-by-step

8084c79 Windows configs

e04fd21 Hela Linux cli lines klara

ea5256f Nätverkstabbel och en del av commandolines

dbd7505 .gitignore skapad

7b25597 Skapa labbdokumentation

https://github.com/tsukuuyomii04-lab/Git-labbmilj- 
</p>


<h2>Ai-Logg</h2>
<p>

Jag då använde mig av Chatgpt för att få svar, Jag ställde frågor som "Hur använder man Chmod och vad gör det för något" 

Jag bad AI då alltid förklara vad jag har gjort så att jag då förstår.

Jag fick inte direkt några hallucinationer för att alla frågor var väldigt simpla att förklara, skulle jag säga att jag använde mig av mycket AI, ja det gjorde jag.

Skulle nog säga att om man frågar AI hur man ska sätta privilieges som vem som äger filen och foldern då är det redan då en säkerhets risk för AI vet. Men bottom det nej inte direkt.  


</p>
<div><h1>Screenshots</h1>

</div>
</div>