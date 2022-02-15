## Porządek po zajęciach #007 :)

#### 1. Sprzatamy w domowym lapie.


### Porządek u siebie na kompie:

#### folder xD w przeglądarce.
1. Jak nie masz, to stwórz w swojej przeglądarce folder xD
2. Wyciągnij ten folder gdzieś na wierzch
3. Dodaj do niego potrzebne linki: github swój, ZPXD, może gmail.
4. Jak pojawi się coś ważnego co do zajęć, wrzuć tutaj.

#### Jak się włacza terminal/powershell?
Windows: kliknij ścieżkę w folderze xD
Linux: shift+ctrl+x

#### folder xD na kompie
1. Kto nie ma to tworzymy katalog na zajęcia. Katalog xD. Na wierzchu gdzieś. I wrzuć tam klucze do serwera jak masz jakieś (AWS ma, Home miał hasło tylko. Co do przenoszenia kluczy to chyba, że masz je już w .ssh, to ogarniasz i pozdrowienia. Ale reszta instrukcji będzie jednak zakładała, że narazie masz te klucze w folderze xD. Może w przyszłości zamienimy to na odrazu .ssh :) ale narazie xD.
2. Wejdź do folderu xD i
- usun wszystkie stare klucze (poza poza 1 .pem jezeli jestes na AWS)
- usun inne pierdoly tutaj poza notatkami chyba ze masz cos waznego.
- gdzieś, w folderze Twojego użytkownika jest folder .ssh masz plik config lub Config - usuń stare bloki (każde bloki po kilka linii zaczynających się od 'Host') z które są Twoim IP z zajęć xD. Albo lepiej, skopiuj je narazie do notatek. Jak skończysz ten skrypt, to będziesz mógł usunąć.

#### 2. Sprzątamy na serwerze i ustawiamy root.
1. logujemy sie na ubuntu(AWS)/root(Home) jak zawsze.
2. piszemy:
```
echo $USER
```
komu nie pisze root to się loguje na roota. A kto nie zrobił root'a to robi teraz (reszta idzie dalej): 
```
sudo passwd
su -
```

Tutaj teraz kazdy jest na root albo nie idzie dalej.

#### 3. Starzy użytkownicy:
- najlatwiej bedzie wejsc do home i wylistowac:
```
cd /home 
ls
```
Jak nic nie widzisz tutaj (poza ubuntu jak jestes na AWS) - to idz do kroku 4. Jak widzisz, to dla kazdeg folderu tutaj (nazwa tych folderow jest rowna nazwom uzytkownikow - to sa foldery domowe) poza ubuntu jak jestes na AWS wykonujemy:
```
deluser NAZWA_FOLDERU
rm -r /home/NAZWA_FOLDERU
```
ewentualnie można dodać:
```
sudo delgroup NAZWA_FOLDERU
```
i komenda sprawdzajaca czy ubylo o 1 folder:
```
ls /home
```
i powtarzaj 4 komendy dla każdego folderu (użytkownika) aż komenda ls /home da pusty wynik albo zostanie sam ubuntu jeżeli jesteś na AWS.


#### 4. Użytkownicy i łączenie się

Teraz przejdź jeszcze raz etap 5, bo tu dałem trochę nowych rzeczy. 
Zobacz etap 5 na https://github.com/ZPXD/flaga
- utworzysz użytkownika
- utworzysz klucz RSA
- liźniesz trochę Linuxa
- no i będziesz się łączyć z serwerem pisząc jedynie: "ssh moj_serwerek" z dowolnego folderu.

#### 5. Szczerze? Etap 7 i 8 też przejdź jeszcze raz.

Z poziomu Twojego użytkownika. Trochę go poprawiłem. Dałem opcję turbo. 
Z nią zabierze Ci to razem 2 minuty.

To teraz jest jeszcze fajnejsze, a wartość z powtórki jest ogromna.

Co zrobić ze starą flaga? Przenieśmy ją do "backupu". Jak masz tu coś cennego, to będziesz mógł tu zawsze wejść, przekopiować ten kod tam gdzie chcesz. Już jako użytkownik zrób:
```
mkdir /home/$USER/backup/
cd /var/www
sudo cp -r flaga /home/$USER/backup/
sudo chown $USER:$USER /home/$USER/backup/
sudo rm -r flaga
```
I zacznij od nowa! https://github.com/ZPXD/flaga

Zobacz tryb turbo: www w 2min.


#### 6. Zostaje piaskownica. 

To prościzna. Z tego co widziałem do tej pory, są 3 główne opcje.

Jak masz piaskownicę to zobacz gdzie jest i zrób to samo. Przenieś ją gdzie trzeba i nadaj jej uprawnienia Twojego użytkownika i zobacz czy działa. 

Np. jeżeli masz piaskownicę w folderze root (Home):
```
sudo cp -r /root/piaskownica /home/$USER/piaskownica
```
Np. jeżeli masz piaskownicę w folderze /home/ubuntu (AWS):
```
sudo cp -r /home/ubuntu/piaskownica /home/$USER/piaskownica
```
Jest też szansa, że zrobiłeś ją we fladze. Wtedy bierzemy ją z backupu:
```
sudo cp -r /home/$USER/flaga/piaskownica /home/$USER/piaskownica
```
Ostatnia opcja, to że masz więcej niż 1 piaskownicę... wtedy, skądkolwiek ją kopiujesz, użyj piaskownica_2, piaskownica_3 etc. Np.
```
sudo cp -r /root/flaga/piaskownica /home/$USER/piaskownica
sudo cp -r /home/ubuntu/piaskownica /home/$USER/piaskownica_2
sudo cp -r /home/$USER/flaga/piaskownica /home/$USER/piaskownica_3
```
W późniejszych krokach wpisuj też dla każdej z piaskownic osobn komende chown.

Powinieneś zobaczyć ja u siebie w katalogu domowym. Jak jest, to nadaj właściwe uprawnienia i zrobione.
```
ls -la /home/$USER
sudo chown $USER:$USER /home/$USER/piaskownica
```
Gotowe. 

Od teraz wszystkie uprawnienia są zrobione i czuj się jak u siebie w domu.

Logujesz się z dowolnego folderu w terminalu/powershellu pisząc:
```
ssh moj_serwerek
```

A co z VSC i Jupyterem? To w kolejnej części :)
