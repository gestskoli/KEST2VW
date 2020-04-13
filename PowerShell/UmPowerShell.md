# PowerShell
PowerShell er skriftumál fram Microsoft sem byggir á .NET
* [Breytur](#breytur)
* [Samanburðar- og rökvirkjar](#samanburðar--og-rökvirkjar)
* [Skilyrðissetningar](#skilyrðissetningar)
* [Lykkjur](#lykkjur)
* [Fylki](#fylki)
* [Hashtöflur - Dictionary](#hashtöflur---dictionary)
* [Föll](#föll)
* [Lesa frá console](#lesa-frá-console)
* [Vinna með tölur sem texta](#vinna-með-tölur-sem-texta)
* [Skrifa í CSV skrá](#skrifa-í-csv-skrá)
* [Athugasemdir í kóða](#athugasemdir-í-kóða)

## Breytur
Breytur í PowerShell eru skilgreindar með ```$``` og svo nafni breytunnar.

Dæmi, búum til breytu sem heitir notandi.
```powershell
$notandi
```
Athugið að ekki er tekið fram af hvaða tagi breytan er og er hún núna ```NULL```.

PowerShell getur sjálft fundið út af hvaða tagi breytan á að vera.
Við getum notað GetType til að sjá af hvaða tagi breytur eru.
```powershell
$notandi.GetType()  # Þetta skilar villu af því að breytan er NULL

$notandi = 10
$notandi.GetType()  # Segir okkur að breytan er núna Int32

$notandi = 3.2
$notandi.GetType()  # Breytan er núna Double

$notandi = "PowerShell"
$notandi.GetType()  # Breytan er núna String
```
Það er hægt að stjórna því af hvaða tagi breytur eru með því að setja tagið í hornklofa fyrir framan breytunafnið.

Grunnntög Powershell eru t.d. Byte, Char, Decimal, Double og Int. Sjá fullan lista [hér](https://blogs.technet.microsoft.com/heyscriptingguy/2015/01/26/understanding-numbers-in-powershell/)  
```powershell
[Int]$tala = 3.2   # Innihald breytunnar verður 3 
[Int]$tala = 3.7   # Innihald breytunnar verður 4 
[Int]$tala = [Math]::Floor(3.7) # Innihald breytunnar verður 3 
$tala.GetType()
```
## Samanburðar- og rökvirkjar
### Samanburðarvirkjar
| Python | Powershell |
| --- | --- |
| == | -eq |
| != | -ne |
| < | -lt |
| <= | -le |
| > | -gt |
| >= | -ge |

### Rökvirkjar
| Python | Powershell |
| --- | --- |
| and | -and |
| or | -or |
| not | -not |
## Skilyrðissetningar
### if-elseif-else
```powershell
if($i -eq 10) {
    "i = 10"
} elseif($i -eq 20 -or $i -gt 30) {
    "i = 20 eða i > 30"
} else {
    "i er eitthvað annað"
}
```
### switch
```powershell
switch ($i) {
    1 {"einn"}
    2 {"tveir"}
    3 {"þrír"}
    default {"eithvað annað"}
}
```
## Lykkjur
### foreach
```powershell
$fylki = (1..10)

foreach($stak in $fylki) {
    $stak
}
```
### do-while
```powershell
$i = 0
do {
    $i++
    $i
} while($i -le 10)
```
### while
```powershell
$i = 0
while($i -le 10) {
    $i++
    $i
}
```
### for
```powershell
for($i = 0; $i -le 10; $i++) {
    $i
}
```
## Fylki
```powershell
$tomtFylki = @()

$fylkiBlandad = 1, "texti", 3.4, "annar texti", 2, 0.5
$fylkiBlandad[1] # skilar öðru stakinu, "texti"
$fylkiBlandad[-1] # skilar síðasta stakinu, 0.5
$fylkiBlandad[1] = "texti2"
```
Stærð fylkis er óbreytanleg
```powershell
$fylkiBlandad.Add(25) # virkar ekki
$fylkiBlandad += 25 # eða $fylkiBlandad = $fylkiBlandad + 25
```
## Hashtöflur - Dictionary
```powershell
$tomHashtafla = @{}

$borgir = @{"Ísland" = "Reykjavík"; "Noregur" = "Osló"; "Þýskaland" = "Berlín"}
```
Skrifa út lyklanan (löndin)
```powershell
foreach($land in $borgir.Keys) {
    $land
}
```
Skrifa út gildin (borgirnar)
```powershell
foreach($borg in $borgir.Values) {
    $borg
}
```
Fletta upp eftir lykli
```powershell
$borgir["Noregur"]
```
Bæta við hashtöfluna og eyða úr henni
```powershell
$borgir.Add("England","London")
$borgir.Remove("Noregur")
```

## Föll
```powershell
function nafnAfalli {
    "hér kemur innihald fallsins"
}

nafnAfalli
```
### Færibreytur - einfaldari útfærsla
```powershell
function fallSemTekurFaeribreytu {
    "tók á móti " + $args[0] + " og " + $args[1]
}

fallSemTekurFaeribreytu 25 60
```
### Færibreytur - önnur útfærsla
```powershell
function annadFallSemTekurFaeribreytur ($Faeribreyta1, [int]$Faeribreyta2) {
    "tók á móti $Faeribreyta1 og {}" -f $Faeribreyta2
}
```
### Færibreytur - betri útfærsla
```powershell
function leggjaSamanTvaerTolur {
    param(
        [Parameter(Mandatory=$true, HelpMessage="Sláðu inn tölu.")]
        [int]$TalaA,
        [Parameter(Mandatory=$true, HelpMessage="Sláðu inn tölu.")]
        [int]$TalaB,
        [switch]$Prenta
    )
    $samtala = $TalaA + $TalaB
    if($Prenta) {
        "Samtalan er " + $samtala
    } else {
        return $samtala
    }
}

leggjaSamanTvaerTolur -TalaA 30 -TalaB 40

leggjaSamanTvaerTolur -TalaA 10 -TalaB 25 -Prenta
```
### Splatting
Hægt er að nota hashtöflur til að setja inn færibreytur.
```powershell
$stillingar = @{
    TalaA = 35
    TalaB = 45
    Prenta = $true
}

leggjaSamanTvaerTolur @stillingar
```

## Lesa frá console
```powershell
$a = Read-Host("sláðu inn tölu") # skilar string
# lesið inn sem string
$a.GetType()
# til að breyta í int
$a = $a -as [int]
# eða 
$a = 0 + $a
$a = $a + 0
```
**Athugið** að ef verið er að vinna með ```char``` þarf að nota aðrar aðferðir.
```powershell
[char]$a = '1'
$i = $a.toString() / 1 # $i inniheldur núna töluna 1
```
Til að fá ASCII gildi stafs ná nota:
```powershell
$stafur = 'A'
$asciiGildi = [int][char]$stafur
# $asciiGildi inniheldur 65
```
## Vinna með tölur sem texta
```powershell
$fTala = 2.34567
$iTala = 3
# Fá tvo aukastafi
"fTalan er {0:N2} með tveimur aukastöfum en iTala {0:N3} með þremur aukastöfum" -f $fTala -f $iTala
# eða
"fTalan er {0:N2} með tveimur aukastöfum en iTala {1:N1} með einum aukastaf" -f $fTala, $iTala
```
## Skrifa í CSV skrá
Þægilegasta leiðin til að skrifa eitthvað í CSV skrá er að búa til fylki sem inniheldur gögnin sem skrifa á í skránna.
Gögnin sjálf er svo best að geyma í því sem heitir <code>PSCustomObject</code>.
### Búa til <code>PSCustomObject</code>
Tvær aðferðir má nota til að búa til PSCustomObject
#### Eldri aðferðin (e. legacy)
```powershell
$upplysingar = New-Object PSObject
$upplysingar | Add-Member -MemberType NoteProperty -Name Nafn -Value "Jón Jónsson"
$upplysingar | Add-Member -MemberType NoteProperty -Name Heimilisfang -Value "Hvergigata 7"
```
einnig má nota hashtöflu
```powershell
$htafla = @{}
$htafla.Add("Nafn","Jón Jónsson")
$htafla.Add("Heimilisfang", "Hvergigata 10")
$upplysingar = New-Object PSObject -Property $htafla
```
#### Nýrri aðferðin
Nota hashtöflu ef hún er þegar til
```powershell
$upplysingar = [PSCustomObject]$htafla
```
eða setja gögnin beint inn
```powershell
$upplysingar = [PSCustomObject]@{
  Nafn = "Jón Jónsson"
  Heimilisfang = "Hvergigata 7"
}
```
### Skrifað í CSV skránna
Yfirleitt viljum við geyma PSObject-in í fylki
```powershell
$notendur = @()

$notendur += $upplysingar 

$upplysingar = [PSCustomObject]@{
  Nafn = "Jóna Jónsdóttir"
  Heimilisfang = "Hvergigata 70"
}

$notendur += $upplysingar
```
Núna eru tvö stök í fylkinu og þá getum við annað hvort notað lykkju
```powershell
foreach($n in $notendur) {
    Export-Csv -InputObject $n -Path "C:\Users\Administrator\Desktop\skra.csv" -Append -NoTypeInformation -Encoding Unicode
}
```
eða "pæpað" í <code>Export-CSV</code> skipunina.
```powershell
$notendur | Export-Csv -Path "C:\Users\Administrator\Desktop\skra2.csv" -NoTypeInformation -Encoding Unicode
```
## Athugasemdir í kóða
Einnar línu athugasemdir.
```powershell
# þetta er einnar línu athugasemd
````
Athugasemdir sem ná yfir tvær eða fleiri línur.
```powershell
<#
  Hér er athugasemd 
  sem getur náð yfir 
  margar línur.
#>
```
