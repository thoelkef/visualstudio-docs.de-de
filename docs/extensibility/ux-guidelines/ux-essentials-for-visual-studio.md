---
title: "UX Essentials f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# UX Essentials f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Bewährte Methoden  
  
### 1. In der Visual Studio\-Umgebung konsistent sein.  
  
-   Führen Sie die vorhandene Aktivität Muster innerhalb der Shell.  
  
-   Entwerfen Sie Funktionen mit der Shell Sehvermögen Sprache und handwerkliches können konsistent sein.  
  
-   Verwenden Sie freigegebene Befehle und Steuerelemente, wenn sie vorhanden sind.  
  
-   Verstehen der Visual Studio\-Hierarchie sowie zu deren wird Kontext und die Benutzeroberfläche steuert.  
  
### 2. Verwenden Sie den Dienst der Umgebung für Schriftarten und Farben.  
  
-   Benutzeroberfläche berücksichtigt die aktuelle Umgebung Schriftart\-Einstellung, wenn es für die Anpassung auf der Seite Schriftarten und Farben im Dialogfeld "Optionen" verfügbar gemacht wird.  
  
-   UI\-Elemente müssen die VSColor Service, mit gemeinsam genutzten Umgebung Token oder spezifische Token verwenden.  
  
### 3. Stellen Sie alle Bilder konsistent mit den neuen VS\-Stil.  
  
-   Führen Sie Visual Studio\-Entwurfsprinzipien für Symbole, Symbole und andere Grafik aus.  
  
-   Fügen Sie Text nicht in Grafikelemente.  
  
### 4. Vom Standpunkt der benutzerzentrierte entwerfen.  
  
-   Der Aufgabenverlauf, bevor die einzelnen Funktionen darin zu erstellen.  
  
-   Mit Ihren Benutzern vertraut sein, und dieses Wissen in Ihrer Spezifikation explizit zu machen.  
  
-   Bei der Überprüfung der Benutzeroberfläche bewerten Sie die umfassende Erfahrung als auch die Details.  
  
-   Entwerfen der Benutzeroberfläche, sodass funktionsfähig und unabhängig vom Gebietsschema oder der Sprache attraktiv bleibt.  
  
## Auflösung  
  
### Minimale Auflösung  
 Die minimale Auflösung für Visual Studio\-Dev14 wird 1280 x 1024. Dies bedeutet, dass *mögliche* Visual Studio in diesem Fall verwendet, obwohl es möglicherweise eine optimale Umgebung nicht. Es gibt keine Garantie, dass alle Aspekte bei einer Auflösung von 1280 x 1024 kleiner verwendbar.  
  
 Anfängliche Dialogfeldgröße sollte 1000 Pixel hoch, um im Rahmen der IDE innerhalb dieser minimale Auflösung mit 96 dpi passen nicht überschreiten.  
  
### HD\-angezeigt.  
 Die Benutzeroberfläche in Visual Studio muss funktionieren gut alle DPI\-Skalierung Faktoren, die standardmäßig unterstützt: 150 %, 200 % und 250 %.  
  
## Antimuster  
 Visual Studio enthält zahlreiche Beispiele für Benutzeroberfläche, die unsere Richtlinien und bewährte Methoden folgen. Im bemühen, konsistent leihen Entwickler häufig von Produkt UI\-Entwurfsmuster ähnelt, die sie entwickeln. Obwohl dies ein guter Ansatz, hilft uns Konsistenz bei der Interaktion des Benutzers und den visuellen Entwurf Laufwerk, in manchen Fällen Funktionen mit ein paar Details liefern wir, die nicht erfüllt unsere Richtlinien aufgrund von Zeitplan oder austragen Priorisierung ist. In diesen Fällen soll erst auf die Teams, kopieren Sie eine dieser "Anti\-Muster", weil sie ungültige oder inkonsistente Benutzeroberfläche in Visual Studio\-Umgebung angelegt.  
  
### Erforderliche Felder\/Einstellungen, die standardmäßig im Status "Fehler" angezeigt  
  
#### Feature\-Team\-Ziele  
  
-   Benachrichtigen Sie die Benutzer, dass sie ein Element hinzugefügt haben, die konfiguriert werden müssen.  
  
-   Zeichnen Sie die Aufmerksamkeit des Benutzers auf die Bereiche, die Eingabe benötigen.  
  
#### Antimuster für Projektmappen  
 Setzen Sie, sobald der Benutzer eine Aktion initiiert hat, und bevor sie die Aufgabe abgeschlossen haben, sofort kritischen Fehler Symbole neben den Bereichen, die Konfiguration.  
  
#### Beispiel: Manifest\-Designer\-Deklarationen  
 Sofort eine Deklaration zu der Liste hinzufügen werden in einem Fehlerzustand, der erhalten bleibt, bis der Benutzer die erforderlichen Eigenschaften festgelegt.  
  
 In diesem Fall gibt es eine zusätzliche Bedeutung ist, da das Symbol für die Warnung ein "X" enthält, so entfernen Sie die allgemeine nicht Symbol neben dem verwendet werden. Daher verwendet die Benutzeroberfläche eine Schaltfläche entfernen, ein Steuerelement mehr umständlich.  
  
 ![Manifest Designer error declaration anti&#45;pattern](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti\-pattern")  
  
 **Benutzeroberfläche ist in einem Fehlerzustand standardmäßig ein Visual Studio\-Anti\-Muster.**  
  
#### Alternativen  
 Eine bessere Lösung für dieses Problem wäre an:  
  
-   Ermöglichen Sie Benutzern das Hinzufügen einer Deklaration ohne Warnung, und verschieben Sie sofort zum Festlegen von Eigenschaften für das Element.  
  
-   Fügen Sie das Warnsymbol \(gold Dreieck\) Wenn der Fokus wechselt von einem Element, z. B. eine Deklaration aus der Liste hinzufügen oder Registerkarten im Designer ändern.  
  
-   Pop\-ein Dialogfeld darauf hingewiesen, dass die Anwendung nicht erstellen, wenn der Benutzer versucht, Registerkarten, die vor dem Festlegen von Eigenschaften für alle Deklarationen ändern, \(oder beliebige auswirkt\), bis die Warnungen aufgelöst werden. Wenn der Benutzer das Dialogfeld schließt und Registerkarten wird trotzdem dann ein Symbol \(kritisch oder Warnung, nach Bedarf\) auf der Registerkarte Deklarationen hinzugefügt.  
  
### Erzwingen des Benutzers zum Lesen von Text vor dem Schließen der Benutzeroberfläche  
  
#### Feature\-Team\-Ziele  
 Lassen Sie nicht des Benutzers die Benutzeroberfläche zu schließen, ohne zuerst den erläuternden Text anzuzeigen.  
  
#### Antimuster  
 Das Team die verknüpften Videos in verschiedenen Stellen in der Visual Studio\-Benutzeroberfläche entschieden, das allgemeine Muster der X einfügen Schließen Schaltfläche und QuickInfo Erklärung gemäß UX, und stattdessen implementiert eine Dropdown\-Liste und einen Link "Nicht mehr anzeigen".  
  
 ![Explanatory text anti&#45;pattern &#45; incorrect](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **Falsch: Erzwingen des Benutzers erklärenden Text zu lesen, vor dem Schließen der Benutzeroberfläche ist ein Anti\-Muster in Visual Studio.**  
  
#### Ergebnis  
 Anstelle einer einfachen Schaltfläche "Schließen" \(Mausklick\) wird der Benutzer gezwungen, zwei aufeinander folgende Mausklicks verwenden einfach die Benutzeroberfläche an jeder Stelle zu schließen, die die verknüpften Videos angezeigt werden.  
  
#### Alternativen  
 Der richtige Entwurf in dieser Situation wäre das allgemeine Muster zu Internet Explorer, Office und Visual Studio folgen: Wenn darauf gezeigt wird, den Benutzer in der QuickInfo\-Beschreibung angezeigt, und mit einem Klick wird die Benutzeroberfläche ausgeblendet.  
  
 ![Explanatory text anti&#45;pattern &#45; correct](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti\-pattern\-correct")  
  
 **Richtig: wie entwickelt, sollten video Links eine QuickInfo mit weiteren Informationen angezeigt, wenn darauf gezeigt wird, und auf das "X" sollte die Meldung ohne weitere Interaktion schließen.**  
  
### Mithilfe dieser Befehlsleisten\-Einstellungen  
 ![Command bar anti&#45;pattern &#45; Figure A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti\-pattern\-FigureA")  
  
 **Abbildung A: Antimuster Befehlsleiste**  
  
 **Abbildung A** dieser Antimuster darstellt: setzen eine Einstellung unter eine Befehlsschaltfläche, die auf mehr als nur den Befehl angewendet wird. Bei dieser Version stehen die folgenden Befehle zusätzlich Debuggen starten – wie im Browser starten ohne Debuggen und Einzelschritt – berücksichtigt, die die ausgewählte Einstellung.  
  
 ![Command bar anti&#45;pattern &#45; Figure B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti\-pattern\-FigureB")  
  
 **Abbildung b besser, aber immer noch eine Antimuster für Befehlsleiste**  
  
 Ist leistungsfähiger, aber dennoch unerwünschtem Nichtvorhandensein Einstellungen dieses Typs in den Symbolleisten Siehe **Abbildung B**. Während der Trennschaltfläche belegen weniger Speicherplatz und daher eine Verbesserung über Dropdownlisten verwenden beide Entwürfe etwas höher stufen, die wirklich ein Befehl nicht immer noch eine Symbolleiste.  
  
 ![Command bar anti&#45;pattern &#45; Figure C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti\-pattern\-FigureC")  
  
 **Abbildung c richtig verwenden des Visual Studio\-Befehl Balken\-Musters**  
  
 In **Abbildung C**, die Einstellung an eine Reihe von Befehlen gebunden ist. Es gibt keine globalen Einstellung wird festgelegt, und wir sind gerade Wechseln zwischen vier Befehle. Dies ist die einzige Situation, in der Befehle in der Symbolleiste zulässig sind.  
  
### Anti\-Steuerelementmuster  
 Antimuster sind einfach falsche Verwendung oder Präsentation eines Steuerelements oder einer Gruppe von Steuerelementen.  
  
#### Unterstreichung verwendet wird, während eine gruppenbezeichnung kein hyperlink  
 Unterstrichenen Text sollte nur für Links verwendet werden.  
  
 **Ungültige:**  
  
 ![Underlining anti&#45;pattern in group labels](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102\-g\_GroupLabelIncorrect")  
  
 **Unterstrichener Text, der keinen Hyperlink ist ein Visual Studio\-Anti\-Muster.**  
  
 **Gute:**  
  
 ![Underlining anti&#45;pattern in group labels &#40;correct&#41;](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102\-h\_GroupLabelCorrect")  
  
 **Richtig formatiert wurde, nicht Hyperlinktext einfacher in der Umgebungsschriftart angezeigt.**  
  
#### Durch Klicken auf ein Kontrollkästchen Ergebnisse in einem Popup\-Dialogfeld  
 Durch Klicken auf das Kontrollkästchen "Remotedesktop für alle Rollen aktivieren" im Assistenten "Windows Azure\-Anwendung veröffentlichen" sofort wird ein Popup\-Dialogfeld ein Visual Studio\-Anti\-Muster. Darüber hinaus das Kontrollkästchen ist nicht ausfüllen des Feldes mit einem Kontrollkästchen nach der Auswahl, eine andere Aktivität Anti\-Muster.  
  
 ![Checkbox pop&#45;up anti&#45;pattern](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102\-i\_CheckboxPopup")  
  
 **Nach dem Klicken auf ein Kontrollkästchen ein Visual Studio\-Anti\-Muster wird aufzurufen ein Dialogfeld.**  
  
### Antimuster für Hyperlink  
 Das folgende Beispiel enthält zwei Antimuster.  
  
1.  Hover einschalten roten Vordergrund bedeutet, dass die richtige freigegebene Farbe aus dem Schriftartdienst nicht verwendet wird.  
  
2.  "Weitere Informationen" ist nicht der entsprechende Text für einen Link zu einem Thema. Ziel des Benutzers ist nicht mehr, erfahren es um die Auswirkungen ihrer Wahl zu verstehen ist.  
  
 ![Hyperlink anti&#45;patterns](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102\-j\_HyperlinkIncorrect")  
  
 **Den Color\-Dienst werden ignoriert, und mithilfe von "Weitere" für Hyperlinks sind Antimuster für Visual Studio.**  
  
 **Bessere Lösung:** stellten die Frage, die der Benutzer durch Klicken auf den Link gefragt werden würde.  
  
-   Wie funktionieren die Windows Azure\-Dienste?  
  
-   Wann benötige ich ein Windows Azure Mobile Services\-Projekt?  
  
#### Mithilfe von "Hier klicken" Links  
 Links sollte selbsterklärend sein. Es ist ein Anti\-Muster verwenden "Hier klicken" oder eine beliebige ähnlich.  
  
 **Ungültige:** "Klicken Sie hier Informationen zum Erstellen eines neuen Projekts."  
  
 **Gute:** "Wie erstelle ich ein neues Projekt aus?"