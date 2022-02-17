CO MAMY:

1. Wejdź na **root** i do katalogu root.
```
su root
cd /root
```
Jeżeli jeszcze nie tworzyłeś sobie dostępu do **root** to:
```
sudo passwd
su -
cd /root
```

Voilà.


2. Stwórz backup i wejdź tam:
```
mkdir backup
cd /root/backup
```

#### Tak ogólnie, co mamy do ewakuacji?


3. Utwórz zmienną ze swoją domeną.
```
MOJA_DOMENA=tu_wpisz_swoja_domene
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
- /root/* # Home
- /home/ubuntu/* # AWS

4. Ewakuacja.

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

Kto chce może usunąć użytkownika wraz z jego katalogiem domowym. Wtedy oczywiście tracisz wszystko co masz w użytkowniku którego skasujesz a nie dodałeś do backupu.

```
deluser --remove-home NAZWA_UZYTKOWNIKA
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

#### MAC:

Config jest w .ssh które jest zwykle gdzieś tutaj:
```
/Users/$USER/.ssh/config
```

#### Gotowe!

Teraz została jeszcze jedna rzecz:

Poniżej jest segment "Przywrócenie" :) wróć do niego jeszcze jak stworzysz już użytkownika. W tym kroku podrzucisz swojemu nowemu użytkownikowi folder backup i dasz do niego dostęp.

Najpierw leć do: https://github.com/ZPXD/flaga/blob/main/README.md

Wróć jak zrobisz użytkownika :)

### Przywrócenie

Masz już użytkownika? :) Zaloguj się na **root** i przypisz do zmiennej nazwę Twojego użytkownika.
```
su
TWOJ_UZYTKOWNIK=tu_wpisz_swoj_nowy_login
```
I skopiuj backup do Twojego nowego folderu domowego. Daj sobie też dostęp.
```
cp -r /root/backup /home/$TWOJ_UZYTKOWNIK/
chown -R $TWOJ_UZYTKOWNI:$TWOJ_UZYTKOWNIK /home/$TWOJ_UZYTKOWNIK/backup
```

Wszystko gotowe :) masz u siebie w katalogu domowym backup :)

Jak flaga już stoi to tyle. możesz zacząć się bawić kodem, flagą :) zobacz też klocki



