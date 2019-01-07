# Lernziele Web Tier
Die Studierenden...
- verstehen die Architektur in der die Servlets eingebunden sind.
- kennen die gängigsten Pattern und können diese anwenden.
- wissen welchen Platz Servlets in der Enterprise Applikation haben.
- kennen die Aufgaben die den Servlets zukommen.
- können Servlets anwenden.

## MVC Pattern
JavaEE verwendet für die View-Technologien (JSF - Java Server Faces) das sogenannte "Model 2" (Variante von MVC Pattern).

In der Servlet-Engine gibt es den **Servlet (Controller)**, welcher **JavaBeans (Model)** erzeugt und **Facelets / JSP (View)** erzeugt. Die View verändert das Model. Das Model ist an die Datenbank gebunden. Der Client stellt anfragen an den Controller und erhält antworten von der View.

## 1. Zeigen Sie die Vorteile der Komponenten basierten Entwicklung auf
- Wiederverwendung von Komponenten
- Austausch von Komponenten
- Loose Kopplung
- Getrennte Entwicklung möglich
- Bessere / gezielte Skalierung
- Verschiedene Sprachen
- Verschiedene Environments

## 2. Welches ist das gängigste Pattern in einer Web Applikation?


## 3. Wieso verwendet man Servlets? Zahlen Sie ein paar Vorteile, vielleicht auch Nachteile auf!
**Vorteile**

- Verwaltet Anfragen und Antworten
- Multi Threading
- Benutzt Java Language (write once, run anywhere)
- Verteilbar (RMI, Corba, INDI)
- Ein Heer von Programmierern
- Viele Komponenten verfügbar
- Sehr stabile Container (Tomcat, Jeronimo, Jetty)
- Ideal für kleine Applikationen (Servlets only)

**Nachteile**

- Compile / Deploy Zyklus (Um neue Änderungen am Servlet zu sehen)
- HTML Wissen vorausgesetzt

## 4. Welche 2 Objekte werden sofort zur Verfügung gestellt wenn ein Servlet aufgerufen wird?
HttpServletRequest und HttpServletResponse

## 5. Von welcher Klasse ist ihr selber geschriebenes Servlet abgeleitet?
Entweder *javax.servlet.GenericServlet* oder *javax.servlet.http.HttpServlet*

## 6. Für welche HTTP Request Typen stellt das Servlet Methoden zu deren Verarbeitung zur Verfügung?
GET, POST, HEAD, PUT, DELETE, TRACE, OPTIONS

## 7. Welche Methoden überschreiben Sie wenn Sie eine HTTP POST Anfrage speziell behandeln möchten
```java
public void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException
```

## 8. Wo können Sie obige Methode auch implementieren, resp. von wo aus können Sie sie auch aufrufen?
Villeicht weiter ableiten...

## 9. Zeichnen Sie den Lebenszyklus eines Servlets auf!
init-->loop(do service[get/post])-->destroy

## 10. Wenn Sie bei den Antworten Ihres Servlet einen String entfernen moechten, welches Werkzeug bietet Ihnen der Servlet Standard?
In einem Web-Filter:
```java
public void doFilter (ServletRequest, ServletResponse, FilterChain)
```

## 11. Geben sie mir eine Definition „was ist ein Servlet?“ ab.
Ein Servlet ist ein Java Programm das in einem Webserver läuft und das javax.sevlet.Servlet Interface implementiert. Es gibt Antworten auf Anfragen von Internet Clients über das Standard Protokoll HTTP/HTTPs. Der Webserver gewinnt dadurch zusätzliche Funktionalität. Ein Servlet läuft in einer „threaded“ Umgebung ab.

Ein JSP wird beim ersten Request kompiliert. Instanziiert und Parameter in Form von HttpServletRequest übergeben. Code wird ausgeführt und gibt Response als HttpServletResponse. JSP füllt die Response Daten in Form von XML oder Json ab.

## 12. Versuchen sie die Begriffe Tiers und Layers zu erklären
Die Schichtenarchitektur ist ein Strukturierungsprinzip für die Architektur von Softwaresystemen. Dabei werden einzelne Aspekte des Softwaresystems konzeptionell einer Schicht zugeordnet. Die erlaubten Abhängigkeitsbeziehungen zwischen den Aspekten werden bei einer Schichtenarchitektur dahingehend eingeschränkt, dass Aspekte einer „höheren“ Schicht nur solche „tieferer“ Schichten verwenden dürfen. Durch eine Schichtenarchitektur wird die Komplexität der Abhängigkeiten innerhalb des Systems reduziert und somit eine geringere Kopplung bei gleichzeitig höherer Kohäsion der einzelnen Schichten erreicht. Ein wichtiger Unterschied zwischen Tiers und Layers ist: Ein Layer ein logischer Strukturmechanismus für die Elemente der SW Lösung, währendem ein Tier ein physikalischer Strukturmechanismus für die   Systeminfrastruktur ist.

## 13. Welche Möglichkeiten haben sie für das Session Management?
**Session Cookies**
- Sehr effektiv
- ungeeignet bei grossen Session Data
- am besten nicht über ein paar hundert Bytes
- Client Side im Browser

**Session ID**
- Best Practice
- grosse Session Data Volumen möglich
- Cookies werden „nur noch für Session ID, etc. verwendet
- Unterliegen dem EE Session Management
- Server Side

## 14. Welche Scopes bietet JSF an?
- @ApplicationScoped
- @SessionScoped
- @RequestScoped
- @FlowScoped
- @DependantScoped