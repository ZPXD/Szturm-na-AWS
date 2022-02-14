
# PORZĄDKI

## PLAN:

Planujemy tak aby działało na Ubuntu AWS/Home/Innych serverach z ~gołym Ubuntu też. Sprawdzamy.

Nie róbcie tego raczej sami, będziemy to ustawiać w poniedziałek o 19:00 14stego :)

### Porządek u siebie na kompie:

#### PORZĄDKI U SIEBIE: Jak się włacza terminal/powershell?
Windows: kliknij ścieżkę w folderze xD
Linux: shift+ctrl+x
Mac: ?

#### PORZĄDEK U SIEBIE: folder xD w przeglądarce.
1. Jak nie masz, to stwórz w swojej przeglądarce folder xD
2. Wyciągnij ten folder gdzieś na wierzch
3. Dodaj do niego potrzebne linki: github swój, ZPXD, może gmail.
4. Jak pojawi się coś ważnego co do zajęć, wrzuć tutaj.

#### PORZĄDEK U SIEBIE: foler xD na kompie
1. Katalog xD tworzymy kto nie zrobił. Na wierzchu gdzieś.  I wrzuć tam klucze do serwera jak masz jakieś (AWS ma, Home miał hasło tylko. Co do przenoszenia kluczy to chyba, że masz je już w .ssh, to ogarniasz i pozdrowienia. Ale reszta instrukcji będzie jednak zakładała, że narazie masz te klucze w folderze xD. Może w przyszłości zamienimy to na odrazu .ssh :) ale narazie xD.
2. Wejdź do folderu xD
3. Powershell/terminal:
Windows: kliknij ścieżkę w folderze xD
Linux: shift+ctrl+x

6. pwd
```
pwd
```
Powinieneś być w folderze xD. Chodźmy dalej.

### Porządek na serwie:

#### AWS:

Wchodzimy na serwer przez powershell/windows wpisując.

```
ssh -i nazwaklucza.pem ubuntu@1.1.1.1 
```

#### Home:

```
ssh root@1.1.1.1
```


#### USTAWIAMY UŻYTKOWNIKA: 

1. Ustawiamy użytkownika o nazwie takiej jak chcesz np. luke:
```
adduser NAZWA_UZYTKOWNIKA_TWOJA
adduser --ingroup www-data --disabled-password NAZWA_UZYTKOWNIKA_TWOJA
adduser NAZWA_UZYTKOWNIKA_TWOJA sudo
su NAZWA_UZYTKOWNIKA_TWOJA
```

2. Sprawdź czy jesteś w grupie www-data
```        
groups $USER 
```

#### TWORZENIE KLUCZA ".rsa"

Stwórz klucz:

```
cd /home/$USER # czy sie da, jak nie nowy katalog
mkdir /home/$USER/.ssh
chmod 700 .ssh
cd  /home/$USER/.ssh
ssh-keygen -f /home/$USER/.ssh/xd_NAZWA_UZYTKOWNIKA_TWOJA -C $USER -N ''
cat ~/.ssh/xd_NAZWA_UZYTKOWNIKA_TWOJA.pub > authorized_keys
chmod 700 xd_NAZWA_UZYTKOWNIKA_TWOJA
```

Sprawdź, czy klucz został stworzony. 

```
ls
```
Pojawią się 2 klucze o nazwie xd_$USER. W przeciwnym razie powtórz albo daj znać, 
że potrzebujesz pomocy.

#### POBRANIE KLUCZA rsa .pub

1. Wchodzisz do katalogu xD w terminal/powershell
2. Uprawnienia katalogu 

```
scp root@46.41.135.4:/var/www/zpxd NAZWA_KLUCZA NAZWA_KLUCZA
scp -i twoj_klucz.pem ubuntu@46.41.135.4:/home/$USER/.ssh/NAZWA_KLUCZA NAZWA_KLUCZA
```
3. Zobacz ls, powinieneś widzieć plik NAZWA_KLUCZA. 
```
ls
```

4. Skopiuj swoją ścieżkę folderu xD i wklej do notatnika podreczne_xd. Dodaj do tego po ukośniku NAZWA_KLUCZA.

Na linuxie to było by:

```
sciezka_pliku_pub = /home/$USER/xD/NAZWA_KLUCZA
```
Na windowsie:

```
sciezka_pliku_pub = C://......
```

Zapisz ją w notatkach podreczne_xd.

#### ŁĄCZENIE PRZEZ KLUCZ ".rsa"

1. Otwórz terminal/powershell w katalogu i wpisz:

```
ssh -i NAZWA_KLUCZA $USER@$$IP
```

Działa? Zostaw w tle, przyda się potem. Nie działa? Spróbuj jeszcze raz, pomyśl, albo daj znać na pomocy.


#### Visual Studio Code

1. Upewnij się, że nadal masz otwarty swój notatnik z folderu xD gdzie trzymasz ścieżkę do Twojego pliku 
1. Instalacja i otwarcie,

2. Instalacja Open-SSH.

3. Połaczenie ze swoim serwerem przez ssh.
- linux
- ssh
- config
- kliknij w edycje konfiga
- otwórz swój notatnik podreczne_xd - i wstaw z tego pliku nastepujace wartości do poniższego szablonu: nazwa_serwera_xd, adres_ip, nazwa_użytkownika, sciezka_pliku_pub.
```
Host moj_nazwa_serwera_xd
  HostName adres_op
  User nazwa_użytkownika
  IdentityFile sciezka_pliku_pub
```

Przykładowo:

```
Host moj_serwerek
  HostName 1.2.3.4
  User rafal_paczes
  IdentityFile /home/rafal_paczes/xD/potezny_klucz_rafiego.pub
```

- jak coś jest w konfigu poza tym co wkleiles z ip Twojego serwera, to to usuń
- zapisz plik
- kontynuuj łaczenie się
- gratuluję, połączyłeś się. sprawdź gdzie jesteś:

```
pwd
```

Od teraz zawsze po zalogowaniu będziesz tutaj, w swoim w "domowym" folderze.

Jeżeli zastanawiasz się co z uprawnieniami, to nie przejmuj się, zaraz wszystko
posprzątamy.

#### Posprzątamy foldery.

#### Posprzatanie flagi:

1. user folderu flagi i plików w środku
2. uprawnienia folderu flagi i plików w środku
3. czy sa pliki ktore zawieraja ustawienia do zmiany? jak tak to zmiana.
4. sprzatamy czyli wyrzucamy wszystkie pliki poza tymi ktore sa konieczne dla istnienia flagi oraz nasze dodatki jak kubus.html i reload.py. Reszta? Przenosimy do piaskownicy. Wiec czy cos tu nie powinno byc a jest? np piaskownica? Jak tak to:
```
chown $USER:$USER piaskownica
cp -r piaskownica /home/$USER/piaskownica
```
5. cos jeszcze? z kazdym plikiem ktory powinien byc w piaskownicy zrob to samo.
```
chown $USER:$USER NAZWA_PLIK
cp NAZWA_PLIKU /home/$USER/piaskownica/NAZWA_PLIKU
```
6. cos jeszcze? z kazdym folderem ktory powinien byc w piaskownicy zrob to samo.
```
chown $USER:$USER NAZWA_FOLDERU
cp -r NAZWA_FOLDERU /home/$USER/piaskownica/NAZWA_FOLDERU
```

#### Posprzatanie piaskownicy:

1. Gdzieś masz piaskownicę. Jeżeli wszystko poszło według planu, 

To albo jest w:
```
ls /root/piaskownica
```
Albo tutaj:
```
ls /home/ubuntu/piaskownica
```
Jeżeli te komendy nie pokazały Ci wylistowanych plików ale dały błąd, to znaczy, że Twoja piaskownica jest gdzie indziej. Poszukaj jej, jak byś miał problemy, pisz na dziale pomoc. Ewentualnie Twoja piaskownica była we fladze (/var/www/flaga) i przerzucilismy ja do Twojego katalogu domowego dzień temu. 

2. wejdź do folderu zawierającego folder piaskownica. 

np jak Twoja piaskownica jest w /root/piaskownica to wpisz:
```
cd /root
chown $USER:$USER piaskownica
cp -r /root/piaskownica /home/$USER/piaskownica
```
a jak Twoja piaskownica jest w /home/ubuntu/piaskownica to wpisz:
```
cd /home/ubuntu
chown $USER:$USER piaskownica
cp -r /home/ubuntu/piaskownica /home/$USER/piaskownica
```

3. Sprawdź czy wszystko się zgadza:
```
cd /home/$USER
ls -la
```
Powinno wyświetlić listę folderów w Twoim folderze domowym, w tym /piaskownica z uprawnieniami $USER. Przykładowo:
```
drwxrwxr-x 2 $USER $USER 4096 Feb 13 06:51 piaskownica
```
Wejdź do folderu /piaskownica i zobacz jakie uprawnienia mają foldery i pliki:
```
cd piaskownica
ls -la
```
Powinno być:
```
drwxrwxr-x 2 $USER $USER 4096 Feb 13 06:51 plik
```

I jest w porządku. Gotowe. Od teraz wszystko będzie pod $USER. Sporadycznie będziesz korzystać też z root do robienia rzeczy z tymi uprawnieniami. 

4. Połączenie z serwerem przez klucz a nie hasło.

Zablokujmy teraz łączenie się do Twojego konta bez klucza. Logowanie przez hasło nie będzie już potrzebne.

```
nano /etc/ssh/sshd_config
```
Znajdź linię PasswordAuthentication=YES i ustaw jej wartość na "NO" i zapisz plik. Od teraz nie można się logować bez klucza. 

```
PasswordAuthentication=YES
```

Gotowe? To tyle. Sprawdźmy jeszcze raz czy wszystko działa.

5. Sprawdźmy czy działa łączenie się przez ssh.

Zamiast ścieżki pliku pub, jeżeli jesteś w folderze gdzie znajduje się klucz, możesz **po prostu podać jego nazwę zamiast całej ścieżki.**

```
ssh -i sciezka_pliku_pub $USER@adres_ip
```

6. Upewnijmuy się, że nie można się logować hasłem.

```
ssh $USER@adres_ip
ssh root@adres_ip
```

Oba powinny zwrócić błąd.

7. Wyłącz i włącz VSC. Sprawdź czy możesz:
- się połączyć z serwerem,
- jak włączysz terminal to jakim użytkownikiem jesteś
- w jakim katalogu jesteś?
- czy możesz tworzyć i modyfikować pliki?
- czy możesz robić to także we fladze oraz piaskownicy?

Jeżeli tak, to wszystko się udało. Gratulacje. To tyle. Powodzenia!

#### Jupyter

1. Wyłącz i włącz VSC, połącz się z serwerem.
2. Otwórz rozszeżenia.
3. Wpisz Jupyter i wybierz właściwy plik do instalacji.
4. Upewnij się, że masz na niebieskim przycisku instalacji napis SSH:1.1.1.1
5. Jak tak to instaluj, to będzie na Twój serwer. Jak nie, to połącz się z serwerem w nowym oknie i spróbuj ponownie.
6. Sprawdź czy działa. Wejdź w terminal i pobierz
```
cd /home/$USER/
git clone testowy_git_z_notebookiem
cd NAZWA_REPO
```
Kliknij na "otwórz plik" i wybierz nowopobrany plik w Twoim folderze domowym w folderze NAZWA_REPO.

7. Wyświetla się plik Jupytera? Fajny, nie?
8. Kliknij w komórkę z kodem. Czy możesz po niej chodzić?
9. Czy możesz ją odpalić? (ctrl+enter)
10. Czy możesz ją modyfikować i odpalić?

Jeżeli na dowolne z tych pytań padła negatywna odpowiedź, leć na pomoc. Jeżeli nie? Gratulacje! Zrobione! 

Od teraz możesz przeglądać Jupyter Notebooki w VSC i uczyć się w nich, testować kod!


#### Git.
1. Wyłącz i włącz VSC.

2. Git. Git jest. Stestujmy to. Utwórz katalog testowy dla gita
```
mkdir git_test
cd git_test
```
3. Spróbujmy sklonować repo. Klikamy tu a tu. W terminaly było by to:
```
git clone REPO_LINUXA
```
4. Teraz zobacz co się stanie jak dodam nowy plik. Klikamy tu a tu. W terminalu to było by:
```
cd REPO_LINUXA
git pull
ls
```

Pojawił się plik_do_testowego_pulla? Super.

Umiesz już:
1. Pobrać repo. (sklonować).
2. Zupdatować repo.
3. Fetchowe tematy.

Na początek starczy. Ale w przyszłości będziemy robić jeszcze trochę rzeczy. 

Np. chcemy opublikować zadanie domowe jako repo. 
Albo oddać je na głowną stronę zajęć.

##### Git - Praca własnia

Np. zadania domowe. Jak zrobisz zadanie domowe, to jak je dodasz?

1. Otwórz nowe okno VSC i połącz się z serwerem.
2. Utwórz katalog projektu.
3. Utwórz pierwszy plik.
4. Wyklikaj aby popchnąć na gita ten folder jako repo.
5. Zobacz czy widać na Twoim gicie :)
6. Modyfikuj plik, dodaj linie.
7. Add, commit, sync.
8. Zobacz czy jest :) super.
9. Usun 1 linie :)
10. Add, commit, sync :)
11. Zobacz czy jest :)
12. Dodaj plik :)
13. Add, commit, sync :) i zobacz na przeglądarce.
14. Usuń plik :)
15. Add, commit, sync :) i zobacz na przeglądarce.
16. Dodaj folder. 
17. Add, commit, sync :) i zobacz na przeglądarce.


##### Git - Pull Requests - prace domowe,

1. Zróbmy test. Pobierz w swoim folderze domowym repo zajecia_programowania_xd

```
git pull zajecia_zaprogramowania_xd
cd zajecia_zaprogramowania_xd
cd /1_piaskownica
cd /007
cd /zadania_domowe
```

2. Utwórz tutaj nowy plik o takiej nazwie jak masz na gicie. Wyklikaj w VSC. Np.

```
luke_007_xd.py
```
3. Dodaj.

W terminalu to by było:
```
git add luke_007_xd.py
```

4. Commituj. I dodaj wiadomość.

W terminalu to by było:
```
git commit -m "Treść Twojej wiadomosći."
```

5. Podrzuć to na głowne repozytorium do zatwierdzenia. Do tego będzie trzeba doistalować rozszeżenie Github. Wyklijak

[IMG]
[IMG]
[IMG]

6. Kliknij PR.

Dodaj wiadomość.


[IMG]
[IMG]

7. Poszło? Powinieneś zobaczyć:

[IMG]

8. Jeżeli tak to się udało. Możesz się rozłożyć i poczekać aż PR zostanie zatwierdzony.

W tym czasie, rzuć okiem na klocki :)


Podsumujmy.
- posprzątaliśmy kwestie użytkowników
- posprzątaliśmy uprawnienia na serwerze
- zainstalowaliśmy VSC i SSH - od teraz tak będziesz łączyć się z plikami na serwerze.
- zrobiliśmy klucze. więc jak byś chciał się łączyć przez ssh z terminala to z kluczem.
- zrobiliśmy Jupytera - teraz możesz tworzyć, używać, modyfikować notebooki.
- umiesz już klonować repozytoria
- oraz dodać do nich plik od siebie.


Trzymaj się! do następnego!
