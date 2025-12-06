# Lab00 - Uvod v Linux

## 1. Krmarjenje po sistemu
```bash
cd ~
pwd
mkdir linux-vaja
cd linux-vaja
pwd
```

## 2. Delo z datotekami
```bash
touch opis.txt
echo "Martin" > opis.txt
cat opis.txt
mkdir testni
mv opis.txt testni/
ls -l testni/
```

## 3. Premikanje in kopiranje
```bash
cd testni
mv opis.txt moj_profil.txt
cp moj_profil.txt ~/
ls -l ~/moj_profil.txt
```

## 4. Pravice in velikosti
```bash
ls -lh
du -sh ./*
chmod 444 moj_profil.txt
ls -l moj_profil.txt
```

## 5. Sistemske informacije
```bash
whoami
du -sh ~
```
**Rezultat:**
```
kali
304G
```

## Dodatna naloga
```bash
du -ah ~ | sort -rh | head -n 5
```
**Rezultat:**
```
1.9M    /home/kali
1.5M    /home/kali/.cache
1.4M    /home/kali/.cache/gstreamer-1.0/registry.x86_64.bin
1.4M    /home/kali/.cache/gstreamer-1.0
204K    /home/kali/.config

```
