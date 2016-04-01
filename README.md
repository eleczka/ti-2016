## Krótkie przygotowanie srodowiska pracy do edycji i uruchomienia projektu napisanego w Java Spring

Notatka ta powstala podczas wspoltworzenia projektu wykonywanego w ramach Koduj dla Polski, projekt *Inteligentny system w zarzadzaniu mieniem komunalnym na przykladzie Gdanska*.

Do wykonania zadania potrzeba nam:
 1. Gotowy projekt wykonany w Spring (oczywiscie pobrany przez jakis Git :smiling_imp: )
 2. Apache Maven
 3. Eclipse JavaEE
 4. MySQL Workbench

Oczywicie nie jest wymagane stosowanie Eclipse oraz MySQL Workbench. Można zastosować inne srodowiska, jednak ta notatka bedzie opierala sie wlasnie na tych programach. :innocent:

Programy do sciagniecia:

* [Apache Maven](https://maven.apache.org/)
* [Eclipse JavaEE](https://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/mars2)
* [MySQL Workbench](https://dev.mysql.com/downloads/installer/) W tym wypadku najlepiej skorzystać z instalatora, ponieważ       bedzie instalowanych kilka programow.

Dodatkowo nalezy miec zainstalowana [Java SE SDK](http://www.oracle.com/technetwork/java/javase/overview/index.html).

### Apache Maven

Pliki Maven zapisujemy w wybranym przez siebie katalogu. Aby wszystko dzialalo prawidlowo, nalezy dodac zmienne srodowiskowe:

W zmiennej path dodajemy w wierszu polecen lub w Windowsie: System :arrow_right: Zmienne srodowiskowe :arrow_right: path

Na przyklad: 
```
C:\Programy\apache-maven-3.3.9\bin
```
Oprocz tego musimy stworzyc nowa zmienna systemowa o nazwie `JAVA_HOME`. W niej umieszczamy sciezke do zainstalowanego SDK Javy, np.:
```
C:\Program Files\Java\jdk1.8.0_66
```
Aby upewnic sie, ze wszystko wykonalismy dobrze, w wierszu polecen mozna sprawdzic dzialanie Mavena wpisujac komende:
```
mvn -v
```
Jesli wszystko wykonalo sie poprawnie i widzimy efekt podobny do ponizszego, mozna przejsc do kolejnej instalacji.
![mvn-v](https://github.com/ElektroITmatyk/TI-2016/blob/master/maven.png)

### Eclipse JavaEE

Po uruchomieniu srodowiska Eclipse wybieramy katalog, w ktorym bedzie nasza *przestrzen robocza* czyli Workspace. Nastepnie w oknie Project Explorer klikamy prawym przyciskiem Import:
![Import](https://github.com/ElektroITmatyk/TI-2016/blob/master/eclipse-import.png)

Jako zrodlo wybieramy `Maven` i `Existing Maven Projects` po czym wciskamy *Next*. Podajemy sciezke dostepu, w ktorej znajduje sie sciagniety przez Git projekt. Jesli wszystko jest prawidlowo, powinien zostac wyswietlony checkbox z plikiem `pom.xml`.

Moze zdarzyc sie, ze w pobranym projekcie brakuje niektorych plikow i Eclipse zglosi nam bledy ikona z czerwonym wykrzyknikiem. W tej sytuacji nalezy w dolnym oknie roboczym wybrac zakladke *Markers*, gdzie otrzymamy informacje o brakujacych plikach i katalogach, w ktorych takie pliki powinny sie znajdowac.
![Markers](https://github.com/ElektroITmatyk/TI-2016/blob/master/eclipse-markers.png)

Pliki te mozna latwo znalezc wpisujac ich nazwy w Google, zwykle beda pod pierwszym linkiem na stronie [MVN Repository](http://mvnrepository.com/).

**Wazna uwaga**
Mozna przygotowac projekt do pracy jeszcze z poziomu Mavena (w koncu do tego sluzy) tak, zeby dalo sie pracowac w Eclipse. W tym celu w wierszu polecen przechodzimy do katalogu naszego projektu i wpisujemy komende:
```
mvn eclipse:eclipse
```
Oczywiscie trzeba miec dostep do internetu, by Maven pobral wszelkie potrzebne pliki. Trzeba jednak z tym bardzo uwazac, poniewaz w moim przypadku zbudowanie projektu w ten sposob co prawda przyczynilo sie do umozliwienia dzialania calego projektu, ale nie dzialalo polaczenie z MySQL. Zatem mozna najpierw skorzystac z powyzszej metody, a jesli nie zadziala baza danych, przygotowac caly Workspace od nowa i pobrac niezbedne pliki.

### MySQL Workbench i MySQL Server

W MySQL Installer - Community wybieramy do instalacji zarówno Workbench jak i Server.
MySQL Server jest programem tworzacym lokalny serwer dla bazy danych, ktora bedziemy zarzadzali w MySQL Workbench.

Podczas instalacji MySQL Server bedziemy wybierali domyslny port dla adresu localhost (127.0.0.1). Instalator proponuje port *3306* i tak najlepiej to zostawic. Dodatkowo wybieramy login uzytkownika (najlepiej zostawic *root*) oraz (cdn)
