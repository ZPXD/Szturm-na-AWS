CO MAMY:

1. Wejdź na **root** i do katalogu root.
```
su root
cd /root
```
2. Stwórz backup i wejdź tam:
```
mkdir backup
cd /root/backup
```
3. Utwórz zmienną ze swoją domeną.
```
MOJA_DOMENA=tu_wpisz_swoja_domene
```
4.

Skopiuj pliki z flagi do backupu:
```
cp -r /var/www/flaga /root/backup
cp /etc/systemd/system/flaga.service /root/backup/flaga
cp /etc/nginx/sites-available/$MOJA_DOMENA /root/backup/flaga
```

```
rm -r /var/www/flaga
rm /etc/systemd/system/flaga.service
rm /etc/nginx/sites-available/$MOJA_DOMENA
rm /etc/nginx/sites-enabled/$MOJA_DOMENA
```

FLAGA:
- /var/www/flaga
- /etc/systemd/system/flaga.service
- /etc/nginx/sites-available/$MOJA_DOMENA
- /etc/nginx/sites-enabled/$MOJA_DOMENA

PIASKOWNICA:
- /root/piaskownica # Home
- /home/ubuntu/piaskownica # AWS
- /var/www/flaga/piaskownica # WTF


INNE RZECZY:
- /root/piaskownica # Home
- /home/ubuntu/* # AWS

