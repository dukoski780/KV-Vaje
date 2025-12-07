# Lab04 - MetaOSINT – Kaj vse razkrije fotografija?

## Priprava okolja

**Namestitev exiftool:**
```bash
sudo apt install libimage-exiftool-perl
exiftool --version
```


## Analiza EXIF metapodatkov

**Uporabljeni ukaz:**
```bash
exiftool slika.jpg
```

**Rezultati:**

```
ExifTool Version Number         : 12.25
File Name                       : slika.jpg
File Size                       : 3.0 MiB
Make                            : samsung
Camera Model Name               : SM-G935F
Software                        : G935FXXS3ERHD
Date/Time Original              : 2018:12:23 19:59:36
Create Date                     : 2018:12:23 19:59:36
GPS Latitude                    : 46° 5' 20.00" N
GPS Longitude                   : 14° 30' 45.00" E
GPS Position                    : 46° 5' 20.00" N, 14° 30' 45.00" E
GPS Altitude                    : 351 m Above Sea Level
GPS Date/Time                   : 2018:12:23 18:59:18Z
Image Width                     : 4032
Image Height                    : 2268
Megapixels                      : 9.1
ISO                             : 320
F Number                        : 1.7
Exposure Time                   : 1/10
Focal Length                    : 4.2 mm (35mm equivalent: 26.0 mm)
```

---

## Analiza in poročilo

**Kakšna je bila natančna lokacija (koordinate in naslov)?**

GPS koordinate: 46°05'20.00"N, 14°30'45.00"E
Lokacija: Ljubljana, Slovenija
Nadmorska višina: 351 m

**Kdaj je bila slika posneta?**

Datum: 23. december 2018
Čas: 19:59:36 (lokalni čas)
GPS čas: 18:59:18 UTC

**Katere druge metapodatke si zaznal?**

- Proizvajalec: Samsung
- Model kamere: SM-G935F (Galaxy S7 Edge)
- Programska oprema: G935FXXS3ERHD
- Resolucija: 4032 × 2268 pikslov (9.1 MP)
- Velikost datoteke: 3.0 MiB
- F število: 1.7
- ISO: 320
- Hitrost zaklopa: 1/10
- Goriščna razdalja: 4.2 mm (26 mm ekvivalent 35mm)

**Kaj vas je presenetilo?**

Presenetila me je količina podatkov, ki je shranjena v eni sami fotografiji. Predvsem GPS koordinate, ki točno razkrijejo lokacijo in čas posnetka. S temi podatki lahko natančno določimo kje in kdaj je bila fotografija posneta, kar je lahko velika grožnja zasebnosti.

**Kaj bi priporočali osebi, ki redno objavlja slike na spletu?**

- Izklop geolokacije na fotoaparatu/telefonu
- Odstranjevanje EXIF podatkov pred objavo
- Premislek o tem, kaj sama vsebina slike razkrije (prepoznavne zgradbe, ulice)
- Objava fotografij z zamikom, ne takoj (npr. po koncu potovanja)

---

## Odstranjevanje EXIF metapodatkov

**Ukaz za odstranitev vseh metapodatkov:**
```bash
exiftool -all= slika.jpg
```

**Rezultat:**
```
1 image files updated
```

**Preverjanje po odstranitvi:**
```bash
exiftool slika.jpg
```

**Rezultat:**
```
ExifTool Version Number         : 12.25
File Name                       : slika.jpg
File Size                       : 3.0 MiB
File Type                       : JPEG
Image Width                     : 4032
Image Height                    : 2268
Megapixels                      : 9.1
```

Vsi GPS podatki, datum, čas in informacije o kameri so odstranjeni. Ostanejo samo osnovni podatki o velikosti in resoluciji slike.

---

## Refleksija

**Ali bi moral vsak pred objavo slike odstraniti EXIF podatke?**

Ne nujno vsi. Odvisno od situacije:
- Pri osebnih fotografijah na družbenih omrežjih: priporočljivo
- Pri profesionalni fotografiji za promocijo: lahko ostanejo
- Pri fotografijah otrok ali občutljivih lokacij: obvezno odstraniti

Večina ljudi se ne zaveda, da fotografije vsebujejo te podatke, zato bi bilo dobro, da platforme družbenih omrežij to avtomatsko odstranijo.

**Kako se lahko zaščitimo pred zlorabo takšnih informacij?**

- Izklop lokacije v nastavitvah fotoaparata
- Uporaba orodij za odstranjevanje metapodatkov (exiftool)
- Preverjanje nastavitev zasebnosti na družbenih omrežjih
- Ne objavljanje fotografij v realnem času (čakanje do konca dogodka/potovanja)
- Razmislek o tem, kaj je vidno na fotografiji

**Ali si že kdaj objavil sliko, ki je vsebovala takšne metapodatke? Kakšen bi bil tvoj odziv danes?**

Ja, večina fotografij, ki sem jih objavil, je verjetno vsebovala EXIF podatke. Nisem se zavedal, da je toliko informacij shranjenih v vsaki fotografiji.

Danes bi:
- Preveril nastavitve telefona in izključil GPS za fotoaparat
- Uporabil exiftool za čiščenje metapodatkov pred objavo
- Bil bolj pazljiv pri objavljanju fotografij v realnem času
- Ozaveščal druge o tej problematiki
