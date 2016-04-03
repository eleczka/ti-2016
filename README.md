## Krotkie przygotowanie srodowiska pracy do edycji i uruchomienia projektu napisanego w Java Spring

Notatka ta powstala podczas wspoltworzenia projektu wykonywanego w ramach [Koduj dla Polski](http://kodujdlapolski.pl/), projekt *Inteligentny system w zarzadzaniu mieniem komunalnym na przykladzie Gdanska*.

**Czym jest Koduj dla Polski?**

> Wiemy że technologia oferuje ona nowe możliwości działania, jednak nie jest panaceum na wszystkie problemy. Dlatego stworzyliśmy przestrzeń do dyskusji i współpracy, aby pozwolić nam wszystkim wypracować optymalne rozwiązania. Budując na zrozumieniu interakcji międzyludzkich i procesów społecznych staramy się wdrażać rozwiązania technologiczne tam, gdzie będą one miały największy pozytywny wpływ.
> 
> Wspólnie dyskutujemy, motywujemy się do działania, budujemy bazę wiedzy i wdrażamy aplikacje i serwisy internetowe.

 * [Trojmiejska strona Koduj dla Polski](http://kodujdlapolski.pl/cities/trojmiasto/)
 * [Trójmiejska grupa na Facebook](https://web.facebook.com/groups/kodujdlapolski.trojmiasto)
 * [Trójmiejska grupa na Meetup](http://www.meetup.com/Koduj-dla-Polski-Trojmiasto/)

Nic, tylko zapisac sie i dzialac z nami! :yum:

### Wprowadzenie

Do wykonania zadania potrzeba nam:
 1. Gotowy projekt wykonany w Spring (oczywiscie pobrany przez jakis Git :smiling_imp: )
 2. Apache Maven
 3. Eclipse JavaEE
 4. MySQL Workbench

Oczywiscie nie jest wymagane stosowanie Eclipse oraz MySQL Workbench. Mozna zastosowac inne srodowiska, jednak ta notatka bedzie opierala sie wlasnie na tych programach. :innocent:

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
![mvn-v](https://github.com/ElektroITmatyk/TI-2016/blob/master/img/maven.png)

### Eclipse JavaEE

Po uruchomieniu srodowiska Eclipse wybieramy katalog, w ktorym bedzie nasza *przestrzen robocza* czyli Workspace. Nastepnie w oknie Project Explorer klikamy prawym przyciskiem Import:
![Import](https://github.com/ElektroITmatyk/TI-2016/blob/master/img/eclipse-import.png)

Jako zrodlo wybieramy `Maven` i `Existing Maven Projects` po czym wciskamy *Next*. Podajemy sciezke dostepu, w ktorej znajduje sie sciagniety przez Git projekt. Jesli wszystko jest prawidlowo, powinien zostac wyswietlony checkbox z plikiem `pom.xml`.

Moze zdarzyc sie, ze w pobranym projekcie brakuje niektorych plikow i Eclipse zglosi nam bledy ikona z czerwonym wykrzyknikiem. W tej sytuacji nalezy w dolnym oknie roboczym wybrac zakladke *Markers*, gdzie otrzymamy informacje o brakujacych plikach i katalogach, w ktorych takie pliki powinny sie znajdowac.
![Markers](https://github.com/ElektroITmatyk/TI-2016/blob/master/img/eclipse-markers.png)

Pliki te mozna latwo znalezc wpisujac ich nazwy w Google, zwykle beda pod pierwszym linkiem na stronie [MVN Repository](http://mvnrepository.com/).

**Wazna uwaga**

Mozna przygotowac projekt do pracy jeszcze z poziomu Mavena (w koncu do tego sluzy) tak, zeby dalo sie pracowac w Eclipse. W tym celu w wierszu polecen przechodzimy do katalogu naszego projektu i wpisujemy komende:
```
mvn eclipse:eclipse
```
Oczywiscie trzeba miec dostep do internetu, by Maven pobral wszelkie potrzebne pliki. Trzeba jednak z tym bardzo uwazac, poniewaz w moim przypadku zbudowanie projektu w ten sposob co prawda przyczynilo sie do umozliwienia dzialania calego projektu, ale nie dzialalo polaczenie z MySQL. Zatem mozna najpierw skorzystac z powyzszej metody, a jesli nie zadziala baza danych, przygotowac caly Workspace od nowa i pobrac niezbedne pliki recznie, jak zostalo to pokazane wyzej.

### MySQL Workbench i MySQL Server

W MySQL Installer - Community wybieramy do instalacji zarówno Workbench jak i Server.
MySQL Server jest programem tworzacym lokalny serwer dla bazy danych, ktora bedziemy zarzadzali w MySQL Workbench.

Podczas instalacji MySQL Server bedziemy wybierali domyslny port dla adresu localhost (127.0.0.1). Instalator proponuje port *3306* i tak najlepiej to zostawic. Dodatkowo wybieramy login uzytkownika (najlepiej zostawic *root*) oraz haslo, ktore bedzie obowiazywalo podczas logowowania do **wszystkich** naszych baz danych. Do swoich drobnych projektow nie musi byc wiec zbyt skomplikowane, ale do wazniejszych juz z pewnoscia trzeba wybrac jak najsilniejsze.

W moim przypadku po zainstalowaniu w katalogu Program Files (wersja 64-bitowa) zabraklo katalogu *data*, w ktorym umieszczane sa logi o bledach. Jesli utworzymy sami taki katalog, nie bedzie dalszych problemow.

Instalacja MySQL Workbench nie jest zbyt skomplikowana, ale juz konfiguracja wymaga wiecej pracy. Po uruchomieniu programu klikmay na znaczek :heavy_plus_sign: aby dodac nowe polaczenie:
![Nowy serwer](https://github.com/ElektroITmatyk/TI-2016/blob/master/img/mysql-new1.png)

Podajemy wybrana nazwe oraz wpisujemy login i haslo, ktore wybralismy podczas instalacji MySQL Server. Nastepnie klikamy *Configure Server Management...* (mozna tez zatwierdzic obecne ustawienia, a nastepnie kliknac prawym przyciskiem na ikonie utworzonego serwera i wybrac *Edit*).
![plik konfiguracyjny](https://github.com/ElektroITmatyk/TI-2016/blob/master/img/mysql-new2.png)

Domyslnie wybierana jest sciezka do wspolnego pliku konfiguracyjnego *my.ini*, jednak mozna tez stworzyc taki plik o innej nazwie dla roznych serwerow. W tym celu tworzymy kopie pliku *my.ini* i zmieniamy nazwe na wlasciwa, poniewaz wskazujac sciezke podczas konfiguracji plik taki musi juz istniec.

Kolejnym krokiem bedzie konfiguracja serwera. Przechodzimy wiec przez kolejne etapy az do ponizszego kroku, w ktorym wybieramy *I'd like to review the settings again*.
![Konfiguracja serwera](https://github.com/ElektroITmatyk/TI-2016/blob/master/img/mysql-new3.png)

Zaznaczamy *Change Parameters* i przechodzimy dalej, do najwazniejszego okna, w ktorym podajemy sciezke do pliku serwera `mysqld.exe`.
![mysqld](https://github.com/ElektroITmatyk/TI-2016/blob/master/img/mysql-new4.png)

Musimy tutaj wskazac dokladna sciezke dostepu do tego pliku. Zwykle bedzie on w podkatalogu `bin` instalacji MySQL Server, np.:
```
C:\Program Files\MySQL\MySQL Server 5.7\bin\mysqld
```
I to wlasciwie wszystko, jesli chodzi o podstawowa konfiguracje. Nastepnie serwer mozna uruchomic i jesli jeszcze nie mamy bazy danych, to utworzyc ja, a jesli juz jest gotowa, to z menu *Server* wykonac `Import`.

### Dalsze przygotowania Eclipse

Jesli nasz projekt w Eclipse nie posiada pliku sluzacego do komunikacji z baza danych MySQL, musimy go wprowadzic.
Najpierw wchodzimy na strone [MySQL Connector/J](https://dev.mysql.com/downloads/connector/j/), gdzie pobieramy archiwum i wypakowujemy do katalogu *naszWorkspace/nazwaProjektu/lib*. Nastepnie w dolnym oknie roboczym Eclipse wybieramy zakladke `Data Source Explorer`, klikamy prawym przyciskiem i wybieramy *New...*. Wybieramy *MySQL*, a potem w prawym gornym rogu klikamy *New Driver Definition*, gdzie podajemy sciezke do pliku `.jar` w katalogu `lib`. W kolejnym kroku podajemy dane do serwera:
![Eclipse - serwer](https://github.com/ElektroITmatyk/TI-2016/blob/master/img/eclipse-mysql.png)

W polu *Database:* podajemy nazwe bazy danych, ktora stworzylismy w MySQL Workbench. W polu *URL* podajemy sciezke lokalnego serwera, ktory musi wygladac tak: `jdbc:mysql://localhost:3306/`, czyli nie podajemy tu nazwy bazy danych, co sugeruje Eclipse. Oczywiscie podajemy tez login i haslo do serwera.

W naszym projekcie musi znajdowac sie plik, w ktorym bedzie sciezka do bazy danych oraz dane do logowania. W przypadku framework Spring w podkatalogu `src/main/resources/` powinien znajdowac sie plik `application.properties`, w ktorym musi znalezc sie ponizszy kod:
```
spring.datasource.url = jdbc:mysql://localhost:3306/nazwa_bazy_danych
spring.datasource.username = root      // lub inny login
spring.datasource.password = haslo_serwera
spring.jpa.hibernate.naming_strategy = org.hibernate.cfg.EJB3NamingStrategy   //jesli uzywamy H2 do uruchomienia poprzez Tomcat
```

### Uruchomienie aplikacji

Aplikacje mozemy uruchomic na dwa sposoby.
 1. Komenda w wierszu polecen,
 2. W Eclipse.

**1. Wiersz polecen**

Przechodzimy do katalogu, w ktorym mamy projekt i wpisujemy ponizsza komende:
```
mvn spring-boot:run
```

**2. Eclipse**

W menu *Run* wchodzimy do *Run Configurations...* i wpisujemy jak ponizej:
![Run](https://github.com/ElektroITmatyk/TI-2016/blob/master/img/eclipse-run.png)

Jesli wczesniej mielismy wszystko dobrze skonfigurowane, to apilkacja powinna prawidlowo uruchomic sie i mozemy otworzyc strone w przegladarce pod adresem `localhost:8080`

### Nareszcie koniec!

I to w zasadzie wszystko! Tak skonfigurowane srodowiska powinny zapewnic nam przynajmniej na poczatku bezproblemowa prace.  :relaxed:
Jesli w tekscie znajduja sie bledy lub nieaktualne dane, prosze smialo zglaszajcie w [Issues](https://github.com/ElektroITmatyk/TI-2016/issues).

Dziekuje za przeczytanie i zycze przyjemnego programowania. :blush:
