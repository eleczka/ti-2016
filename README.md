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


