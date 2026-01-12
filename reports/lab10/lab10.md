# Lab10 - CTF vaja HackyCorp

## 1. Odkrivanje ranljivosti iz znanih URL naslovov
- https://hackycorp.com/admin/
  - key: ad1d44d6-ab73-4640-8291-c5bf2343e2a5

- https://hackycorp.com/login/

## 2. Odkrivanje ranljivosti iz javnih datotek
- https://assets.hackycorp.com/key.txt
  - key: aeaee57f-2a82-41da-bc4c-d081c8cddfc8

## 3. Odkrivanje ranljivosti v Javascript datotekah
- https://assets.hackycorp.com/js/script.js
  - key: d6b75269-97a3-44de-be32-fff0dd55e7ef

## 4. Odkrivanje ranljivosti na spletnem strežniku
- curl -I https://hackycorp.com/
  - key: 99d0738b-1e52-4a00-8885-b15894b2c79e

- https://hackycorp.com/robots.txt
  - key: af9c328a-02b4-439d-91c6-f46ab4a0835b

- https://hackycorp.com/.well-known/security.txt
  - key: 99685e30-7061-4ac0-83bf-4ccc0409faac

## 5. Odkrivanje ranljivosti preko IP naslova
- dig hackycorp.com +short
  - 51.158.147.132
- curl http://51.158.147.132/
  - key: 5cf83b5d-eb6c-4eee-af6c-945f9aed8dfd

## 6. Odkrivanje ranljivosti v Github repozitorijih
- https://github.com/hackycorpdev/test1/blob/master/TEST
  - key: 80cb2045-c8bf-4357-8931-a28dd0f3fbb9

- https://github.com/hackycorp/repo3
  - git checkout test
  - key: 08be82ba-e5fd-4fae-b2c2-272a18d31f80

- https://github.com/hackycorp/repo4/blob/test/KEY
  - key: a60b4aee-642a-483b-9262-ccfc2ed46f0d

- git clone https://github.com/hackycorp/repo9.git
  - git log --diff-filter=D --summary
  - git show 397a2a64461258112821015221a9b33220ece058:KEY.txt
  - key: 3ee505c2-8aa9-4d5e-810e-921778dce1e6

- git clone https://github.com/hackycorp/repo0a.git
  - git log --oneline
  - git log --oneline --grep=key -i
  - git show [commit]
  - key: 5c75cfe9-52dd-475b-8cfa-7ffc492abeca

## 7. Odkrivanje ranljivosti v DNS zapisih
- dig TXT key.z.hackycorp.com +short
  - key: 9f883f22-6ea5-4631-bbe8-95841ad63f56

## 8. Uporaba mehanizma za sinhronizacijo DNS zapisov (AXFR)
- dig AXFR z.hackycorp.com @z.hackycorp.com
  - key: e5fce970-6d94-43c1-bdd5-a06c2b235f9c

## 9. Razkrivanje informacij s pomočjo poizvedb programske opreme
- dig -c chaos -t txt VERSION.BIND @z.hackycorp.com
  - key: 4e5e76e1-728a-49be-aea8-4591ba11e588

## 10. Skriptno programiranje in avtomatizacija
- chmod +x script1.sh
- ./script1.sh
- chmod +x script2.sh
- ./script2.sh
- 0x81.a.hackycorp.com
