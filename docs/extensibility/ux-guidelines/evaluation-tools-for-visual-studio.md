---
title: "Analysetools f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# Analysetools f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Checkliste für handwerkliches können für Visual Studio  
 Verwenden Sie diese Prüfliste, um benutzererfahrung Qualität Visual und Interaktion Details auszuwerten.  
  
### Übersicht  
  
-   Stellen Sie sicher, dass alle Befehle Feedback führen, die Benutzer darüber informiert, dass ihre Befehle ausgeführt wurden.  
  
-   Stellen Sie sicher, dass alle Elemente der Benutzeroberfläche und Steuerelemente in allen Designs und im Modus für hohe Kontraste sichtbar sind.  
  
-   Stellen Sie sicher, dass inaktive und aktive Auswahl werden immer unterschieden, sowohl in der Standard\- und der Modus für hohe Kontraste.  
  
-   Stellen Sie sicher, dass der Fokus immer sichtbar und offensichtlich ist.  
  
### Leistung  
  
-   Stellen Sie sicher, dass einige Art von "ausgelastet" Indikator angezeigt wird, wenn ein Befehl mehr als eine Sekunde dauert.  
  
-   Überprüfen Sie, ob ein Befehl mehr als 10 Sekunden, eine explizite Statusanzeige, entweder akzeptiert bestimmte \(bevorzugt\) oder unbestimmt ist, wird angezeigt.  
  
### Benutzeroberflächen\-text  
  
-   Stellen Sie sicher, dass alle Bezeichnungen Satz oder Anfangsbuchstaben und kein Text vollständig Kleinbuchstaben ist.  
  
    ||Korrigieren|Falsche|  
    |-|-----------------|-------------|  
    |**Befehlstext \(alle\)**|Großbuchstaben:<br /><br /> **Der Verzeichnisname:**|Der Verzeichnisname:|  
    |**Schaltflächentext \(Client\)**|Große Anfangsbuchstaben:<br /><br /> **\[Als Standard festlegen\]**|SET AS DEFAULT|  
    |**Schaltflächentext \(online\)**|Großbuchstaben:<br /><br /> **\[Als Standard festlegen\]**||  
  
-   Überprüfen Sie alle Bezeichnungen, mit Ausnahme von Kopfzeilen und Schaltflächen, mit einem Doppelpunkt enden und vorausgehen das Steuerelement, mit dem sie verbunden sind.  
  
-   Überprüfen, ob die Schaltflächen, Befehle und Befehlslinks, die zum Erfassen von Benutzereingaben\-Benutzeroberfläche starten Auslassungspunkte enden **\[...\]**.  
  
     Beispiele:  
  
    -   Ein **\[Erweitert\]** auf ein Dialogfeld auf die Schaltfläche.  
  
    -   Der Befehlsoptionen im Menü Extras \(**Tools \> Optionen**\) ein Auslassungszeichen sollte nicht abgerufen werden, da das Dialogfeld selbst starten mit dem Befehl wird.  
  
-   Stellen Sie sicher, dass die Benutzeroberfläche keine Abkürzungen, mit Ausnahme von Industriestandard\-Begriffe enthält. Z. B. müssen HTML weder TCP\/IP, geschrieben werden, obwohl sollten OOM \(nicht genügend Arbeitsspeicher\) und personenbezogene Informationen \(persönlich identifizierbare Informationen\).  
  
### Tastaturzugriff  
  
-   Stellen Sie sicher, dass es eine Möglichkeit für jede Aufgabe mit der Tastatur. In der Regel erfolgt dies über den Zugriff für jedes Steuerelement, aber für einige Bereiche visuell zur Umgehung dieses Problems wie z. B. soll in der Codeansicht akzeptabel ist.  
  
-   Stellen Sie sicher, dass Sie über Steuerelemente in einer logischen Reihenfolge \(links nach rechts und oben nach unten\) TAB\-Taste. Obwohl dies eine bewährte Methode für die meisten Steuerelemente erfordern nicht alle Steuerelemente dieser Ansatz. Überprüfen Sie z. B. dieses Optionsfeld, die Steuerelemente in einer Gruppe mit einer einzelnen Tabstopp.  
  
-   Stellen Sie sicher, dass alle Steuerelemente Bezeichnungen und jede Bezeichnung Mnemonik hat \(Ausnahmen sind einige nicht bezeichnet Steuerelemente, die folgen einem beschrifteten Steuerelement auf der Registerkarte\).  
  
-   Stellen Sie sicher, dass keine mnemonische Konflikte vorhanden sind.  
  
### Schriftarten  
  
-   Überprüfen Sie, ob alle Schriftarten \(Fläche, die Größe und Farbe\) einheitlich verwendet werden und die Hierarchie verwalten.  
  
-   Stellen Sie sicher, dass alle Elemente der Benutzeroberfläche die Umgebung Schriftart\-Dienst verwenden. \(Siehe [Schriftarten und Formatierungen für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)\)  
  
     Um zu überprüfen, ob der Dienst verwendet wird, wechseln Sie zu **Extras \> Optionen \> Schriftarten und Farben**. Wählen Sie in der Dropdownliste Einstellungen Umgebungsschriftart aus und ändern Sie die Schriftart in stylistically anderes \(z. B. Harrington oder Comic Sans\), und legen Sie die Größe auf 12 pt. Klicken Sie dann auf OK. Sie müssen möglicherweise die IDE neu starten, aber die meisten UI wird sofort geändert. Bereiche, die die Änderung der Schriftart auch auf Neustart übernimmt nicht verwenden die Umgebungsschriftart nicht.  
  
-   Stellen Sie sicher, dass Schriftarten, die Ableitung des Diensts \(z. B. fett oder vergrößerte Text\) beibehalten, die Größe und die Formatierung in Bezug auf "normal" Text, wenn der Schriftgrad der Umgebung geändert wird.  
  
-   Stellen Sie sicher, dass keine Fehler Clipping aufgrund vergrößerte Schriftarten vorhanden sind. Schriftarten, die erste abgeschnitten sind wahrscheinlich das Ergebnis feste Höhe Steuerelemente oder feste Höhe Container.  
  
### Dialogfelder  
  
-   Überprüfen, ob der Dialogfeldtitel identisch mit dem Befehl, der es gestartet.  
  
-   Stellen Sie sicher, dass alle Standardsteuerelemente konsistent mit dem Betriebssystem sind: Hintergrundfarbe standard und keine Steuerelemente sollten einen speziellen Re basierenden Stil Standardsteuerelemente anders angezeigt werden erstellt, haben.  
  
-   Stellen Sie sicher, dass Ränder innerhalb des Formulars 12 Pixel und einheitliches und konsistentes sollte angezeigt werden.  
  
-   Stellen Sie sicher, dass Dialoge steht in der Mitte der IDE\-Shell oder das Fenster, das sie erzeugt.  
  
-   Wenn nützlich, sollte Dialogfelder mit veränderbarer Größe sein. Dialoge, die geändert werden kann, stellen Sie sicher, dass beim Ändern der Größe, die entsprechenden Steuerelemente ändern müssen, während andere Teile des Dialogfelds konstant bleiben.  
  
-   Stellen Sie sicher, dass Dialoge mit änderbarer Größe jeder Benutzer angepasst Größe \(Größe, Position, Erweiterung von Dialogfeld\-Steuerelemente usw.\) beibehalten.  
  
-   Stellen Sie sicher, dass es kein Symbol in der Titelleiste wird.  
  
-   Überprüfen Sie, dass keine Schaltflächen zum Minimieren und maximieren, in der Titelleiste angezeigt sind.  
  
#### Dialogfeld vorgangsschaltflächen \(gilt nur für Visual Studio\-Client\)  
  
-   Stellen Sie sicher, dass die Operation Schaltflächen in dieser Reihenfolge: **OK**, **Abbrechen**, **Übernehmen**.  
  
-   Überprüfen Sie, ob **OK** und **Abbrechen** Schaltflächen sind die Standardgröße: 75 x 23 Pixel.  
  
-   Überprüfen Sie, ob **OK** und **Abbrechen** Schaltflächen sind gleich groß unabhängig von der Länge der Zeichenfolge.  
  
-   Wenn die Bezeichnung auf eine Schaltfläche Vorgang Schaltfläche auf breiter als Standard erforderlich ist, überprüfen Sie die entsprechende **Abbrechen** Schaltfläche gleicher Größe ist.  
  
-   Überprüfen, ob es 6\-Pixel\-Abstand zwischen Schaltflächen und die zugehörigen Steuerelemente.  
  
-   Überprüfen Sie, ob die **OK** und **Abbrechen** Schaltflächen keine Zugriffstasten \(Zugriffstasten durch einen unterstrichenen Buchstaben definiert\).  
  
-   Vergewissern Sie sich, eine Schaltfläche \(i. d. r. **OK**\) standardmäßig den Fokus besitzt.  
  
-   Überprüfen Sie, ob **Esc** das Dialogfeld wird abgebrochen  
  
-   Überprüfen Sie, ob **EINGABETASTE** die Standardschaltfläche ausgeführt wird, wenn der Fokus nicht auf ein Steuerelement befindet, die Sie verarbeitet.  
  
-   Überprüfen Sie, ob die **OK** und **Abbrechen** Schaltflächen werden in der unteren rechten Ecke des Dialogfelds positioniert. In wenigen Ausnahmen abgesehen ist es für sie in der oberen rechten Ecke vertikal gestapelt werden.  
  
-   Stellen Sie sicher, dass die vertikale Konfiguration nur verwendet wird, wenn andere Schaltflächen in horizontale Ausrichtung im Dialogfeld sind.  
  
### Steuerelement\-standards  
  
#### Allgemein  
  
-   Stellen Sie sicher, dass, wenn möglich, es gute Standardwerte gibt für die Benutzerinteraktion und stellt Benutzern einen Link zu einem sicheren oder allgemeine Ergebnis zu beschleunigen.  
  
-   Überprüfen Sie, ob die Standardsteuerelemente dasselbe Verhalten, damit Benutzer wissen, was passiert basierend auf frühere Erfahrung.  
  
#### Label\-Steuerelemente  
  
-   Stellen Sie sicher, dass jedes Steuerelement eine Bezeichnung ist und jede Bezeichnung visuell seines Steuerelements \(im Allgemeinen schwanken 4 bis 6 Pixel\) zugeordnet ist, und näher an das entsprechende Steuerelement als für andere Steuerelemente.  
  
-   Stellen Sie sicher, dass Bezeichnungen linksbündig angeordnet werden Links mit dem Steuerelement Kante nach links, oben positioniert und horizontal zentriert, sodass die Baseline der Bezeichnung der Basislinie des Eingabetexts ausgerichtet ist, wenn auf der linken Seite positioniert.  
  
-   Stellen Sie sicher, dass wenn mehrere gestapelte Bezeichnung und Benutzereingabe\-Steuerelemente auf der linken Seite eines Steuerelements positioniert ist, die Bezeichnungen linksbündig werden und nie ein gleichen Abstand zwischen dem Rand des Dialogfelds zu leeren, rechts und Abstand von den Steuerelementen. Paare sollten gleichmäßig verteilt werden, es sei denn, sie zusätzlichen Platz Gruppierung an.  
  
#### Benutzereingabe\-Steuerelemente \(Textfelder und Kombinationsfelder\)  
  
-   Überprüfen Sie bei der Verwendung der Umgebung Standardschriftart Höhe angezeigt für Textfelder, Kombinationsfelder und Schaltflächen alle 23 Pixel.  
  
-   Wenn Hinweistext verwendet wird, stellen Sie sicher, dass die Farbe auf `Environment.ControlEditHintText` mithilfe des Diensts für Farbe.  
  
-   Wenn das Feld ein Pflichtfeld, die als solche identifiziert werden müssen ist, stellen Sie Folgendes sicher:  
  
    -   die der Hintergrund festlegen, um `Environment.ControlEditRequiredBackground` und die Vordergrundfarbe auf festgelegt ist `Environment.ControlEditRequiredHintText`  
  
    -   dass Hinweistext innerhalb des Steuerelements, das ist **"\< Required \>"**  
  
#### Button\-Steuerelemente  
  
-   Überprüfen Sie die Schaltflächen eine Mindestgröße von 75 x 23 Pixel, es sei denn, damit mehr Text.  
  
-   Überprüfen Sie, ob Schaltflächen verlassen haben und mit der rechten Rand von 3 bis 5 Pixel sowie Auffüllung für den Inhalt.  
  
-   Es ist akzeptabel, verwenden Sie eine kleine quadratische Schaltfläche mit nur einer Ellipse **\[...\]** auf anstelle einer **\[durchsuchen...\]** Schaltfläche \(oder eine ähnliche Funktion\). Wenn verwendet, stellen Sie sicher, dass die Schaltfläche 23 x 23 Größe.  
  
-   Wenn es mehr als eine **\[durchsuchen...\]** in einem Dialogfeld, und klicken Sie dann überprüfen Sie, ob die gekürzte Version \(nur Auslassungszeichen **\[...\]**\) für alle dient.  
  
-   Vergewissern Sie sich, mit den drei Punkten **\[...\]** Schaltflächen kein mnemonisches Zeichen. Wenn der Fokus auf das Eingabesteuerelement daneben befindet, sollte einer Registerkarte auf die Schaltfläche mit den Auslassungspunkten Fokus.  
  
-   Überprüfen, ob ein Auslassungszeichen Schaltflächen, Befehle und Befehlslinks, auf dem sekundären Benutzeroberfläche gestartet, der weitere Benutzereingaben erfasst enden muss **\[...\]**.  
  
#### Hyperlinks  
  
-   Überprüfen Sie, ob ein Hyperlink\-Steuerelement nie Rot, wenn aktive blinkt. Dies ist ein Indikator, dass der Dienst Farbe nicht verwendet wird  
  
-   Stellen Sie sicher, dass für die VS\-Farben verwendet werden:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Überprüfen, ob Links nicht zu unterstreichen Blau, es sei denn, in einem Absatz eingebettet werden.  
  
#### Kontrollkästchen  
  
-   Enthält ein Kontrollkästchen mehrzeiligen Text, stellen Sie sicher, dass das Feld mit der ersten Textzeile, die nicht über alle Zeilen vertikal zentriert ausgerichtet.  
  
-   Überprüfen Sie, ob das Kontrollkästchen immer eine binäre hinweisen und nicht den Benutzer oder neuen Fenstern oder Seiten zu öffnen.  
  
-   Ein Kontrollkästchen eine Option, die im Zusammenhang mit einem Eingabesteuerelement vor, überprüfen Sie, ob es bündig links und sehr eng unter das Steuerelement an, dass seine Beziehung positioniert ist.  
  
-   Stellen Sie sicher, dass das Kontrollkästchen **nie** als Möglichkeit verwendet, um den gesamten Inhalt der ein Dialogfeld oder eine Seite zu aktivieren.  
  
#### Gruppenfelder  
  
-   Stellen Sie sicher, dass ein Dialogfeld, das den gesamten Inhalt des Dialogfelds enthält ein einzelnes Gruppenfeld darin nicht enthält.  
  
-   Stellen Sie sicher, dass mindestens zwei Steuerelemente innerhalb jeder Gruppe vorhanden sind.  
  
-   Nur selten sollte mehr als zwei Gruppenfelder auf ein Dialogfeld angezeigt werden.  
  
-   Stellen Sie sicher, dass keine geschachtelte Gruppenfelder vorhanden sind.  
  
### Symbole  
  
-   Überprüfen Sie, ob Symbole in das dunkle Design ordnungsgemäß invertierten angezeigt werden.  
  
-   Stellen Sie sicher, dass alle Symbole auf wichtige Konzepte zu basieren.  
  
-   Stellen Sie sicher, dass jedes Symbol distinct, einfach zu erkennen und nicht mehr als zwei Konzepte \(ohne Status Modifizierer\/Sprache enthält\).  
  
-   Stellen Sie sicher, dass das Basis\-Symbol im Bereich zentriert angezeigt wird.  
  
-   Stellen Sie sicher, dass alle Symbole im Modus für hohe Kontraste lesbar angezeigt werden.  
  
-   Überprüfen Sie, ob eine beliebige Farbe verwendet Farbe Nutzung Standards entspricht.  
  
-   Überprüfen Sie, dass keine Halos \(Rahmen sind\) um Symbole. \(Wenn vorhanden ist, sollte die Halo die Hintergrundfarbe der angrenzenden Benutzeroberfläche entsprechen\).  
  
### Touchscreen\-Benutzeroberfläche  
  
-   Überprüfen Sie, ob interaktive Steuerelemente groß genug ist, werden einfach touchable – minimale **23 x 23 Pixel** Größe  
  
-   Stellen Sie sicher, dass mindestens die am häufigsten verwendeten Steuerelemente sind **40 x 40 Pixel** Größe.  
  
-   Überprüfen Sie, ob interaktive Steuerelemente mindestens **5 Pixel** zwischen ihnen