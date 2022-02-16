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

Jak sprawdzić czy folder istnieje?
```
ls SCIEZKA_FOLDERU
```
Jak zwraca błąd, to nie istnieje albo nie macie uprawnień :D



#### Opcja A: /root/piaskownica # Home
```
cp -r /root/piaskownica /root/backup
rm -r /root/piaskownica
```

#### Opcja B: /home/ubuntu/piaskownica # AWS
```
cp -r /home/ubuntu/piaskownica /root/backup
rm -r /home/ubuntu/piaskownica
```
#### Opcja C: /var/www/flaga/piaskownica # WTF

Nic nie rób :) 

#### Opcja D: Nie mam piaskownicy :)

To założysz w 9 zajęciach :)


### Ewakuacja innych rzeczy.
- /root/piaskownica # Home
- /home/ubuntu/* # AWS

#### Opcja A: inne rzeczy w /root # Home

```
cp -r /root/* /root/backup/
```

#### Opcja B: inne rzeczy w /home/ubuntu # AWS

```
cp -r /home/ubuntu/* /root/backup/
rm -r /home/ubuntu
```
#### Opcja C: nie mam innych rzeczy

Nic nie rób :) 



### Usuwanie użytkownika:

Kto chce może usunąć użytkownika wraz z jego katalogiem domowym.
```
deluser NAZWA_UZYTKOWNIKA
rm -r /home/NAZWA_UZYTKOWNIKA
```

#### Na komputerze u siebie - plik ~/.ssh/config lub ~/.ssh/Config

Ten plik jest w katalogu głównym użytkownika na Twoim komputerze. Otwórz go notatnikiem albo jak chcesz. PS: folder .ssh jest niewidoczny.

#### Windows:

Ręcznie - wyklikajcie i otwórzcie. 
- Jeżeli go nie ma, to stwórz go. **ALE BEZ ROZSZEŻENIA A NIE .TXT ("Config" a nie "Config.txt") :)**
- Zrób kopie.
- Zostaw pusty.
- Zapisz.

#### Linux:

Jak jest to zapisz go obok jako: config_old. A ten zostawcie pusty.
```
nano /home/$USER/.ssh/config
cp /home/$USER/.ssh/config /home/$USER/.ssh/config_2
```
Jeżeli go nie ma, to stwórz go. 
```
nano /home/$USER/.ssh/config
```

Zostaw pusty i zapisz.


### X

Z roota (su -)

```
TWOJ_UZYTKOWNIK=tu_wpisz_swoj_nowy_login
```

```
cp -r /root/backup /home/$TWOJ_UZYTKOWNIK/
chown -R $TWOJ_UZYTKOWNI:$TWOJ_UZYTKOWNIK /home/$TWOJ_UZYTKOWNIK/backup
```
