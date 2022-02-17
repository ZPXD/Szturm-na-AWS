## VSC & Jupyter

##### VSC: Instalacja

1. Download: https://code.visualstudio.com/download
2. Zainstaluj.
3. Utwórz gdzieś skrót.




##### VSC: Połączenie z serwerem



1. Włącz

![o01.png](foto/o01.png)

2. Extensions (5 ikonka po lewej od góry)

![002.png](foto/002.png)

3. W search wpisz: SSH i kliknij w najwyższą pozycję: Remote-SSH i kliknij Install.

![003.png](foto/003.png)

4. Kliknij w Remote Explorer (6 ikonka po lewej od góry)
5. Jeżeli przechodzisz to pokolei, to powinien pojawić Ci się w SSH TARGETS conajmniej 1 punkt do połączenia, zdefiniowany w pliku config (lub Config). Możesz go edytować.
6. Najedź na niego myszką. Po prawej stronie pokaże Ci się przycisk którym połączysz się w nowym oknie z serwerem :)
7. W listwie na górze w nowym oknie spyta się Ciebie o haslo.
- Jeżeli to Cię nie połączy 3 razy i wybierz "more actions" 
- Wybierz Open SSH Configuration File i sprawdź czy tutaj wszystko się zgadza albo spytaj się opomoc.
8. Jesteś na serwerze. Hurra :) To jeszcze raz wyjdź wyłączając to okno.

Od teraz zawsze połączysz się z serwerem w 3 kliknięciach:
- Włączając VSC
- Klikając w Remote Explorer (5 klocek po lewej)/var/www/flaga/app.py
- Kliknij w znaczek po prawej stronie Twojego serwera na liśćie połączeń
- Wpisz hasło i jesteś na swoim serwerze z poziomu VSCt

I jesteś. 

Połącz się i rozłącz kilka razy.

##### Mobilność

1. Otwórz Pierwszy plik.
2. Otwórz Drugi plik obok, w innym folderze.
3. Stwórz Trzeci plik i zapisz.
4. Otwórz Pierwsz i Drugi plik aby były jedncześnie widoczne.
5. Flodery - otwórz katalog jako folder - aby mieć listę plików z lewej.

##### VSC: Terminal

1. Na górze jest listwa szara, na niej jest Terminal. 1 ikonka go otwiera na dole.
2. Jak jesteś u siebie na serwerze, to możesz tu robić rzeczy tak jak na serwerze ze swojego użytkownika.
3. Sprawdź gdzie jesteś, kim jesteś.
```
pwd
echo $USER
```
Jak się zgadza, to idziemy dalej.

#### VSC: Clone

1. Kliknij w 3 klocek od góry z lewej **(Source Controll)**
2. Kliknij w duży niebieski przycisk na dole **(Clone Repository)**
3. Wklej link do repozytorium które chcesz sklonować
```
git clone https://github.com/ZPXD/zajecia_programowania_xd
```
4. Spyta się Ciebie w jakim folderze - podaj katalog domowy
5. Spyta się Cibie czy otworzyć ten folder - powiedz, że tak

![git_clone1.png](foto/git_clone1.png)
![git_clone_2.png](foto/git_clone_2.png)

##### VSC: Jupyter

1. Wejdź na Extensions (listwa z lewej, u mnie 5 ikona)
2. Wpisz w search Jupyter
3. Wyświetli się Jupyter
4. Upewnij się, że niebieski przycisk Install wskazuje na SSH:twoj_serwer
5. Instaluj.
7. Wejdź do sklonowanego w kroku wyżej do repozytorium do katalogu klocki.
8. Otwórz któreś zajęcia np 3 lub 4.
9. Spróbuj dodać coś w jednej z komórek i ją włączyć, np dodaj:
```
print('jupyter dziala')
```
10. Utwórz nowy plik (ctrl+n, ctrl+s, zapisz jako xd.ipynb, wyjdz i wejdz i zobacz czy możesz dodać komórki, kod, zapisać)
11. Jak działa to super, jak nie to leć na pomoc.




