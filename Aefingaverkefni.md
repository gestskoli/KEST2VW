  # Powershell æfingaverkefni
  Þetta eru æfingaverkefni sem ekki á að skila

  ## 1. Samhverfa (e. polindrome)
Skrifið fall sem finnur samhverfur (orð eða setningar sem hægt er að lesa bæði aftur á bak og áfram). Stórir og litlir stafir skipta ekki máli.

Gerið tvær útfærslur af fallinu, í annari útfærslunni skuluð þið nota ```for``` lykkju og bera saman einstök stök úr strengnum (munið ```$strengur[-1]``` skilar síðasta staf, hverju ætli ```$strengur[-2]``` skili þá?). Í hinni útfærlsunni skuluð þið breyta strengnum í fylki af bókstöfum (skoða ```toCharArray()``` fallið) og snúa svo fylkinu (skoða ```[array]::reverse($fylki)``` fallið) breytið fylkinu svo aftur í streng (skoða ```-join($fylki)```) sjá nánar [hér](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/04/reverse-strings-with-powershell/) hvernig snúa má streng.
```powershell
function samhverfa {
    param(
        [Parameter(Mandatory=$true, HelpMessage="Texti sem athuga á hvort er samhverfur.")]
        [string]$texti
    )
    # TODO
}
```
Dæmi um notkun:
```powershell
samhverfa -texti "Rakar" # skilar True
samhverfa -texti "skóli" # skilar False
```
## Reiknirit Sesars
Útfærið [reiknirit Sesars](https://is.wikipedia.org/wiki/Reiknirit_Sesars) í falli. Fallið þarf að geta dulkóðað of afdulkóðað. Til einföldunar skulum við bara vinna með enska stafrófið og bara annað hvort stóra eða litla stafi og sleppa bilum (e. space).

Dæmi um notkun:
```powershell
Sesar -Texti "I TAEKNISKOLANUM ER GAMAN" -Hlidrun 5
# skilar: NYFJPSNXPTQFSZRJWLFRFS
Sesar -Texti "NYFJPSNXPTQFSZRJWLFRFS" -Hlidrun 5 -Afkodun
# skilar: ITAEKNISKOLANUMERGAMAN
```
Aukaverkefni: 
* Útfæra fallið þannig að það geti tekið á móti texta með pípu (e. pipe) og jafnvel frá skrá.
* Skrifa fall til að brjóta dulkóðunina ef hliðrunartala er ekki þekkt.
* Útfæra [Affine dulkóðun](https://en.wikipedia.org/wiki/Affine_cipher).

## Tugakerfi <-> tvíundarkerfi 
Skrifið fallið tugatvi sem breytir milli talnakerfa. Fallið tekur á móti annað hvort tugakerfistölu (heiltölu) og skilar þá tvíundakerfistölu eða tekur á móti tvíundarkerfistölu (string) og skilar tugakerfistölu. Leysist án þess að nota innbyggð föll.

Dæmi um notkun:
```powershell
tugatvi -tugakerfi 43 # skilar 101011
tugatvi -tvitala "101011" # skilar 43
```
Aukaverkefni:
* Bæta við áttunda- og sextándakerfinu
