# KEST2VW Lokaverkefni haust 2020 (20%)
Verkefnið skal halda utan um í lokaðri geymslu á [GitHub](https://github.com). Áður en lengra er haldið skaltu því búa til nýja lokaða geymslu og bjóða svo kennaranum þínum inn á hana sem samstarfsaðila (e. collaborator). Skilaðu svo hlekknum á geymsluna í skilahólfið á Innu.

Þú þarft að halda dagbók á github um hvað þú gerir og hvenær.

## Verkefnið
Þú hefur verið fengin(n) til að setja upp eina tölvu sem frumgerð fyrir ungt fyrirtæki þar sem starfa 9 starfsmenn. 

### 1. Uppsetning á Windows og grunn stillingar (20%)
- Ef þú átt ekki nú þegar 90 daga prufuútgáfu af Windows 10 skaltu [sækja](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise) hana (ISO - Enterprise). 
- Búðu til nýja sýndartölvu í VirtualBox, þú velur allar stillingar sjálf(ur) fyrir utan að netstillingin á að vera stillt á *Bridged Adapter*.
- Settu upp nýja Windows 10 sýndartölvu í VirtualBox.
- Passaðu að velja **Domain join instead** þegar það er í boði [sjá mynd](../Myndir/MicrosoftSignIn.png).
- Búðu til sjálfa(n) þig sem notanda í uppsetningarferlinu.
- Breyttu nafninu (e. computer name) á tölvunni í KEST2VW-[nafnið þitt] (án íslenskra stafa og bila (e. space)).
- Búðu til notendahópana (e. user group) Innkaup, Sala og Yfirstjórn.

### 2. Notendur (20%)
Skrifaðu skriftu í PowerShell sem býr til notendurna í þessari [skrá](https://raw.githubusercontent.com/gestskoli/KEST2VW/master/Annad/notendur.csv). Skriftan á að búa til notendurna út frá þeim upplýsingum sem eru í skánni ásamt því að setja þá í hópana sem þú bjóst til í liðnum hér fyrir ofan. Athugaðu að líklega þarftu líka að setja þá í aðra hópa.

Gott er að skoða [`Import-Csv`](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/import-csv?view=powershell-7) skipunina í PowerShell fyrir lausnina á þessum lið. Sjá dæmi um notkun [hér](https://github.com/gestskoli/KEST2VW/blob/master/PowerShell/UmPowerShell.md#lesa-úr-csv-skrá).

**Tryggðu að allir notendurnir geti skráð sig inn.**

Búðu til hópinn *Allir* en í honum eiga allir notendurnir að vera. Þetta þarf ekki að leysa með PowerShell en það má.

### 3. Skrár, möppur og réttindi (20%)
Hver hópur þarf að eiga sér sína eigin möppu sem eingöngu þeir sem eru í þeim hóp hafa aðgang að. Síðan þarf að vera til mappan Sameign sem allir notendurnir hafa aðgang að. Búðu til möppuna *Gögn* á rót C drifsins. Búðu svo möppurnar fyrir hópana til í möppunni Gögn og stilltu svo réttindin á möppunum. Búðu til textaskrá í hverri möppu sem heitir eftir nafninu á möppunni.

### 4. Öryggismál (10%)
  - Breyttu lykilorðareglunni þannnig að:
    - Lágmarkslengd lykilorða verður 8 stafir.
    - Einföld lykilorð eru ekki heimil.
  - Eldveggur: 
    - Lokað fyrir allt nema ping.

### 5. Netkerfi (30%)
Leystu [þetta](../Annad/Lokaverkefni_V20.pka) PacketTracer verkefni. Áður en þú byrjar á því gæti verið gott að skoða [þetta](../Annad/10.2.1.7%20Packet%20Tracer%20-%20Web%20and%20Email.pka) æfingaverkefni.


## Skil á verkefninu
Skilin á verkefninu fara þannig fram að fyrir lið 1 til og með 4 þá sýnir þú kennaranum þínum verkefnið í gegnum fjarfund í MS Teams.

Fyrir lið 5 þá skilar þú PacketTracer skránni á Innu.
