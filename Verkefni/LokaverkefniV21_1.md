# KEST2VW Lokaverkefni vor 2021 (20%)
Verkefnið skal halda utan um í lokaðri geymslu á [GitHub](https://github.com). Áður en lengra er haldið skulu þið því búa til nýja lokaða geymslu og bjóða svo kennaranum ykkar inn á hana sem samstarfsaðila (e. collaborator). Skilið svo hlekknum á geymsluna í skilahólfið á Innu.

Þið þurfið að halda dagbók á github um hvað þið gerið og hvenær.

## Verkefnið
Þú hefur verið fengin(n) til að setja upp eina tölvu sem frumgerð fyrir ungt fyrirtæki þar sem starfa 9 starfsmenn. 

Þið vinnið áfram með tölvuna sem þið settuð upp á önninni.

### 1. Uppsetning á Windows og grunn stillingar (20%)
- Setjið upp nýja Windows 10 uppsetningu á tölvuna.
- Passið að velja **Domain join instead** þegar það er í boði [sjá mynd](../Myndir/MicrosoftSignIn.png).
- Búið ykkur til sem notanda í uppsetningarferlinu.
- Breyttu nafninu (e. computer name) á tölvunni í KEST2VW-[nöfning ykkar] (án íslenskra stafa og bila (e. space)).
- Setjið upp Python3 (64 bita) og VS Code (með Python stuðningi).
- Setjið upp annan hugbúnað eftir þörfum.

### 2. Notendur (20%)

Búið til notendahópana (e. user group) Innkaup, Sala og Yfirstjórn.

Skrifið svo skriftu í PowerShell sem býr til notendurna í þessari [skrá](https://raw.githubusercontent.com/gestskoli/KEST2VW/master/Annad/notendur.csv). Skriftan á að búa til notendurna út frá þeim upplýsingum sem eru í skánni ásamt því að setja þá í hópana sem þið gerðuð í liðnum hér fyrir ofan. Athugið að líklega þarftu líka að setja þá í aðra hópa líka.

Gott er að skoða [`Import-Csv`](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/import-csv?view=powershell-7) skipunina í PowerShell fyrir lausnina á þessum lið. Sjá dæmi um notkun [hér](https://github.com/gestskoli/KEST2VW/blob/master/PowerShell/UmPowerShell.md#lesa-úr-csv-skrá).

**Tryggðu að allir notendurnir geti skráð sig inn.**

Búðu til hópinn *Allir* en í honum eiga hóparnir Innkaup, Sala og Yfirstjórn að vera. Þetta þarf ekki að leysa með PowerShell en það má.

### 3. Skrár, möppur og réttindi (20%)
Hver hópur þarf að eiga sér sína eigin möppu sem eingöngu þeir sem eru í þeim hóp hafa aðgang að. Síðan þarf að vera til mappan Sameign sem allir notendurnir hafa aðgang að. Búðu til möppuna *Gögn* á rót C drifsins. Búið svo möppurnar fyrir hópana til í möppunni Gögn og stillið svo réttindin á möppunum. Búið til textaskrá í hverri möppu sem heitir eftir nafninu á möppunni.

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
