---
title: "Men&#252;s und Befehlen f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Men&#252;s und Befehlen f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Zur Verwendung des Befehls  
  
### Übersicht  
 Im Gegensatz zu Microsoft Office, die eine Suite viele einzelne Produkte umfasst, enthält Visual Studio viele Produkte, die jeweils ihre Befehlssätze, globale Visual Studio\-IDE beitragen. Die IDE verwaltet die Komplexität von Tausenden von Befehlen durch Filtern der Funktionen für den Benutzer anhand des Kontexts.  
  
 Wenn der Kontext eines Benutzers geändert wird – z. B. ein Entwurfsfenster umstellen, um ein Bearbeitungsfenster Code – Funktionen, die nicht mit wird nicht mehr der neue Kontext. Zur gleichen Zeit neue Funktionalität Flächen sowie verknüpfte dynamische Informationen, z. B. Eigenschaften und Toolbox\-Optionen. Der Benutzer sollte nicht bemerkt Austausch der den Satz der verfügbaren Befehle. Wenn der Benutzer abgelenkt oder verwechselt von Befehlen, die angezeigt oder ausgeblendet ist, benötigt das Design der Benutzeroberfläche Anpassung. Aktuellen Kontext des Benutzers wird immer in eine oder mehrere Methoden, wie z. B. in der Titelleiste der IDE, das Fenster Eigenschaften oder das Dialogfeld Eigenschaftenseiten angegeben.  
  
 Befehlsleisten ermöglichen Flexibilität in der Benutzeroberfläche. Der einzige Befehl Datenstrukturen von Visual Studio\-Umgebung stehen im Hauptmenü und die wichtigsten Befehlsleiste, kann beide angepasst und sogar ausgeblendet. Andere Befehlsleisten angezeigt und ausgeblendet basierend auf den Zustand der Anwendung. Toolfenster und Editoren Dokument können auch eingebettete Symbolleisten Fensterränder enthalten.  
  
#### Grundlegende Richtlinien  
  
##### Verwenden Sie vorhandenen freigegebenen Befehle Befehlsgruppen und Menüs, wann immer möglich.  
 Da Befehle in der Regel basierend auf dem Kontext angezeigt werden, wird mit der vorhandenen freigegebenen Menüs und Befehlsgruppen die Befehlsstruktur zwischen Änderungen im Kontext relativ konstant bleibt. Freigegebene Befehle erneut aus, und platzieren neue Befehle nahe verwandter freigegebenen Befehle auch verringert die Komplexität der IDE, und erstellt eine benutzerfreundlichere Umgebung. Wenn ein neuer Befehl werden definiert muss, versuchen Sie, eine vorhandene freigegebene Befehlsgruppe platzieren. Wenn eine neue Gruppe werden definiert muss, fügen Sie ihn in das vorhandene freigegebene Menü nahe an eine Befehlsgruppe von verwandten vor dem Erstellen eines neuen Menüs der obersten Ebene.  
  
##### Symbole für jeden Befehl nicht erstellt werden.  
 Überlegen Sie genau, bevor Sie ein Befehlssymbol erstellen. Symbole, die nur für Befehle erstellt werden soll, die:  
  
-   in einer Standardsymbolleiste angezeigt.  
  
-   wahrscheinlich von Benutzern hinzugefügt werden, auf eine Symbolleiste, über die **anpassen...** Dialogfeld.  
  
-   haben Sie ein Symbol für die gleiche Aktion in einem anderen Microsoft\-Produkt.  
  
##### Beschränken Sie das Hinzufügen von Tastenkombinationen  
 Die Mehrzahl der Benutzer nutzen einen kleinen Bruchteil alle verfügbaren Tastenkombinationen. Binden Sie im Zweifelsfall das Feature nicht auf eine Tastenkombination ist. Arbeiten mit Ihrer Benutzer kommen Team vor dem Hinzufügen neuer Tastenkombinationen.  
  
##### Kommuniziert die Platzierung einer Standard\-Menü.  
 Denken Sie daran, dass die Befehle von anderen angepasst werden und entsprechend zu entwerfen. Es ist also als ausgeblendete Befehl. Alle Visual Studio\-Befehle angezeigt, der **Tools \> Anpassen** Dialogfeld, das Befehlsfenster, automatische Vervollständigung der **Tools \> Optionen \> Tastatur** Dialogfeld und Development Tools\-Umgebung \(DTE\). Vergewissern Sie sich auf Ihre Befehle einen Namen und eine QuickInfo in der Datei .ctc geben, sodass Benutzer sie leicht finden können.  
  
##### Duplizieren Sie freigegebene Befehle auf eine eingebettete Symbolleiste nicht.  
 Es ist hilfreich, um Befehle in der Nähe der Bereich des Benutzers zu platzieren. Eine Möglichkeit hierzu ist eine eingebettete Symbolleiste am oberen Rand der Tool\- oder ein Dokument\-Editor erstellen. Die Befehle auf der Symbolleiste platziert sollte für den Inhaltsbereich innerhalb des Fensters. Duplizieren Sie diese freigegebenen Befehle nicht. Beispielsweise nie platzieren Sie ein Symbol "Speichern" in eine eingebettete Symbolleiste.  
  
### Inhalt und der Sichtbarkeit  
 Befehle vorhanden sind, in den folgenden Bereichen: **Umgebung**, **Hierarchie**, und **Dokument**. Kennen Sie jeden Bereich, um die Platzierung der Befehl vertrauen können.  
  
 Befehle in der **Umgebung** Bereich primären Kontext herzustellen und zwischen mehreren Kontexten freigegeben werden. Ändern der Sichtbarkeit oder Anordnung von Dokumenten und Toolfenster. Zwischen den Befehlen in der Umgebung Bereich sind **Neues Projekt**, **Verbindung mit Server herstellen**, **Prozess anhängen**, **Ausschneiden**, **Kopie**, **Einfügen**, **Suchen**, **Optionen**, **Anpassen**, **Neues Fenster**, und **Hilfe anzeigen**.  
  
 Befehle in der **Hierarchie** Bereich Verwalten von Hierarchien in Visual Studio, einschließlich **Projekt**, **Team**, und **Daten**. Im Zusammenhang mit einem Projekt Unterkontext – z. B. **Debuggen**, **Erstellen**, **Test**, **Architektur**, oder **Analysieren**. Zwischen den Befehlen in der Hierarchie Bereich sind **Neues Element hinzufügen**, **neue Abfrage**, **Projekteinstellungen**, **Neue Datenquelle hinzufügen**, **Leistungs\-Assistenten starten**, und **Neues Diagramm**.  
  
 Befehle in der **Dokument** Bereich auf den Inhalt eines Dokuments, z. B. Code, Entwurf oder eine Arbeitsaufgabenabfrage \(WIQ\) reagieren. Sie auch für die Sicht eines Toolfensters fungieren oder andernfalls für diese Toolfenster spezifisch sind. Dokument Bereich Befehle auch fungieren, auf die Dateiobjekte selbst Hierarchie\-spezifisch ist, wie z. B. **aus dem Projekt entfernen**. Zu den Befehlen im Dokument Bereich zählen **Umgestalten \> Umbenennen**, **Kopie von Arbeitsaufgabe erstellen**, **Alle erweitern**, **Alle reduzieren**, und **Benutzeraufgabe erstellen**.  
  
### Befehl entscheiden  
 Nachdem Sie sich entschieden haben, erstellen Sie einen Befehl, müssen Sie die entsprechenden Platzierung und, ob Sie eine Tastenkombination erstellen zu bestimmen. Führen Sie diesen Pfad Entscheidung, um festzulegen, wo Sie den Befehl aus:  
  
 ![Command placement decision chart](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501\-a\_CommandPlacement")  
  
 **Pfad der Entscheidung für die Platzierung von Befehl in Visual Studio**  
  
### Platzierung von Befehl in Menüs  
  
#### Hauptmenü  
 Der Hauptmenüleiste sollte der Standardspeicherort für alle Pakete kontextspezifische Befehle, die an die Benutzeroberfläche beitragen. Der Hauptmenüleiste unterscheidet sich von anderen Befehl Strukturen, da die Umgebung zu steuern verwendet der Befehle angezeigt werden. Deaktivieren Sie alle anderen Befehlsleisten einfach Befehle, die außerhalb des Kontexts, ob sie in einem Menü oder einer Symbolleiste platziert werden.  
  
 Die Umgebung definiert eine Reihe von Befehlen in der Hauptmenüleiste integriert, die für die gesamte IDE und mehrere Task\-Domänen sind. Diese Befehle sind immer sichtbar unabhängig von denen VSPackages werden in die Umgebung geladen. Obwohl VSPackages dieser Satz von Befehlen erweitern können, ist der Befehlssatz in jedes Produkt und die Platzierung der Befehle für die die Verantwortung für die einzelnen Teams.  
  
 Die Struktur der Visual Studio\-Hauptmenü kann in folgende Menükategorien im unterteilt:  
  
##### Core\-Menüs  
  
-   Datei  
  
-   Bearbeiten  
  
-   Ansicht  
  
-   Tools  
  
-   Fenster  
  
-   Hilfe  
  
##### Projektspezifische Menüs  
  
-   Projekt  
  
-   Build  
  
-   Debug  
  
##### Kontextabhängige Menüs  
  
-   Team  
  
-   Daten  
  
-   Test  
  
-   Architektur  
  
-   Analysieren  
  
##### Für die spezifischen Menüs  
  
-   Format  
  
-   Tabelle  
  
##### Beim Entwerfen von Hauptmenüs befolgen Sie die folgenden Regeln:  
  
-   Nicht mehr als 25 Elemente der obersten Ebene in einem bestimmten Kontext  
  
-   Menüs sollte niemals mehr als 600 Pixel hoch.  
  
-   Ein Hauptmenü in mehreren Kontexten, z. B. in Ultimate SKU und das allgemeine Profil auswerten.  
  
-   Dropdown\-Menüs sind zulässig.  
  
-   Reduzierte Menüs sollte mindestens drei Elemente und nicht mehr als sieben enthalten.  
  
-   Reduzierte Menüs sollte nur eine Ebene tief gehen – einige Visual Studio\-Menüelemente cascading Untermenüs haben, aber dieses Muster wird nicht empfohlen.  
  
-   Verwenden Sie nicht mehr als sechs Trennzeichen. Gruppen sollten in der folgenden Abbildung entsprechen:  
  
     ![Guidelines for main menu grouping](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501\-b\_MainMenus")  
  
-   Während es nicht erforderlich ist, müssen jede Gruppe in der Abbildung, ist das Hinzufügen von zusätzlichen Gruppierungen beschränkt.  
  
-   Jede Gruppe sollte aus zwei bis sieben Menüelemente verfügen.  
  
#### Hauptmenü Sortierung  
 Vor dem Hinzufügen eines neuen Elements der obersten Ebene, sollten Sie den Befehl in einem vorhandenen Menü der obersten Ebene. Wenn Sie ein neues Menü der obersten Ebene hinzufügen, achten Sie darauf, dass Sie an der richtigen Position platzieren. Entscheiden Sie, ob Sie im Menü Projekt, Kontext oder Dokument spezifisch ist. Halten Sie den Namen des Menüs der obersten Ebene präzise und verwenden Sie ein einzelnes Wort.  
  
 Die Core\-Menüs sollten Buchstütze die restlichen Befehle. Datei, bearbeiten und Ansicht sollte immer auf der linken und Tools, Fenster und Hilfe sollte immer auf der rechten Seite.  
  
#### Kontextmenüs  
 Platzieren zu viele Funktionen in den Kontextmenüs führt eine schwierig zu erlernendes\-Schnittstelle. Alle wichtigen Funktionen sollte der Hauptmenüleiste verfügbar. Position der Befehle sollten vorhandene Befehle zum Vermeiden Sie doppelte Befehle abgestimmt werden. Für Kontextmenüs definiert die Shell Standardmenü\-Gruppen, die abhängig davon, ob das Kontextmenü für die Projektmappe, einen Projektknoten oder ein Projektelement enthalten sein soll.  
  
 Beim Entwerfen von Kontextmenüs folgen Sie denselben Regeln wie für das Hauptmenü, und darüber hinaus:  
  
-   Überschreiten Sie 25 Menüelemente der obersten Ebene nicht.  
  
-   Dropdown\-Menüs sind zulässig muss, aber nicht mehr als eine Ebene tief – verwenden Sie niemals cascading Flyouts.  
  
-   Verwenden Sie nicht mehr als sechs Trennzeichen.  
  
### Befehl Platzierung in Symbolleisten  
  
#### Allgemeine Symbolleisten  
 Beim Entwerfen und Anordnen von Symbolleisten, führen Sie diese Standards:  
  
-   Verwenden Sie nicht mehr als ein Verb pro Schaltfläche. Eine Schaltfläche eine Aktion \=.  
  
-   Verwenden Sie Text neben dem Symbol, nur, wenn sie mit der Bezeichnung gestärkt werden muss.  
  
-   Verwenden Sie ein Kombinationsfeld, ausschließlich für Eigenschaften, die mehrmals in einer Sitzung eingefügt werden. Andernfalls machen Sie Eigenschaft an anderer Stelle verfügbar.  
  
-   Die Breite eines Kombinationsfelds sollte die Breite des längsten Elements in das Feld \+ 30 % entsprechen. Wenn Sie der längsten 200 Pixel ist, sollte das Kombinationsfeld z. B. 260 Pixel breit sein.  
  
-   Beschränken Sie die Verwendung von Trennzeichen. Die Verwendung eines Trennzeichens neben einer Dropdownliste ist als Antimuster, da die Form der Dropdown\-Liste als visual Trennzeichen fungiert.  
  
-   Symbol für Gruppen sollten drei und sechs Symbole enthalten.  
  
-   Wenn Qualifizierer in mehrere nützliche Befehle zur Folge haben, verwenden Sie eine Trennschaltfläche, in dem die letzte Einstellung gespeichert:  
  
     ![Split buttons in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501\-c\_SplitButtons")  
  
     **Beispiel für eine Trennschaltfläche. Die sechs Befehle auf der linken Seite können stattdessen in einer Schaltfläche angepasst.**  
  
#### Produktspezifische Symbolleisten  
 Jedes Produkt kann stellen, Standardsymbolleiste enthält häufig verwendete und wichtige Befehle und jedes Produkt Standardsymbolleiste beim ersten erscheinen soll, wenn Visual Studio gestartet wird, nachdem das Produkt installiert ist.  
  
 Produkte sollten auch freigegebene Befehlsgruppen und Menüs von der IDE aus nutzen. Jede freigegebene Befehlsgruppe befindet sich in einem freigegebenen Menü sollen, Organisieren verwandte Befehle auf sinnvolle Weise für den Benutzer. Es ist wichtig, diese freigegebenen Befehlsstruktur zu nutzen, um die Komplexität zu reduzieren.  
  
#### Globale Symbolleisten  
 Globale Symbolleisten sind erforderlich, um auf eine Zeile direkt nach dem Feld passen. Wenn Sie eine neue globale Symbolleiste erstellen, befolgen Sie die Richtlinien für diesen Symbolleistentyp aus.  
  
 **Allgemeine Symbolleiste Richtlinien:**  
  
-   Jede Werkzeugleiste hat 24 Pixel in allgemeine Steuerelemente \(Ziehpunkt, Überlauf\).  
  
-   Jede Symbolleisten\-Schaltfläche ist 22 Pixel, einschließlich Füllzeichen dar. Machen dem Symbol einer Trennschaltfläche Fügt eine andere 11 Pixel Breite.  
  
-   Duplizierung der Befehle auf Symbolleisten ist zulässig.  
  
 **Dokumentspezifische Symbolleisten** angezeigt, wenn Sie ein bestimmten Dateityp aktiv ist und entfernt werden, wenn Sie ein anderen Dateityp aktiviert wird.  
  
-   Für die spezifischen Symbolleisten möglicherweise nicht mehr als 12 Tasten.  
  
-   Die Gesamtbreite der Symbolleiste überschreiten 300 Pixel nicht.  
  
-   Jeder Dateityp haben einen eingebetteten Symbolleiste oder eine globale dokumentspezifische\-Symbolleiste, aber nicht beide.  
  
 **Kontextspezifische Symbolleisten** angezeigt werden, wenn in einem bestimmten Kontext festgelegt ist und in der Regel für einen längeren Zeitraum aktiv bleiben.  
  
-   Die Schaltfläche für alle Kontext\-spezifische Symbolleisten beträgt 18.  
  
-   Wenn die meisten Benutzer konsistent Befehle der Symbolleiste einsetzen wird nicht, wenn der Kontext aktiv ist, klicken Sie dann nicht diese Symbolleiste einen Kontext zuzuordnen.  
  
-   Stellen Sie sicher, dass die Symbolleiste beim Beenden der Kontext verschwindet. Keines dieser Symbolleisten sollte beim Start angezeigt werden.  
  
 **Symbolleisten ohne Kontext** nie automatisch angezeigt wird. Diese zeigen nur, wenn sie der Benutzer aktiviert. Halten Sie die maximale Breite unter 200 Pixel.  
  
### Allgemeine Organisation und Shell definierte Gruppen  
 Verwenden Sie die vorhandenen freigegebenen Befehle Befehlsgruppen und Menüs. Wenn ein neuer Befehl werden definiert muss, versuchen Sie, eine vorhandene freigegebene Befehlsgruppe platzieren. Wenn eine neue Gruppe werden definiert muss, versuchen Sie es vor dem Erstellen eines neuen Menüs der obersten Ebene in einem vorhandenen freigegebenen Menü nahe bei einer entsprechenden Befehlsgruppe zu platzieren. Dies reduziert die Komplexität der Befehl, und stellen gleichzeitig sicher konsistent Befehl Platzierung in der IDE.  
  
 Der freigegebene **Format** Menü, in der Regel im Kontext des Windows\-Designer\-Dokument, wird in der folgenden Abbildung dargestellt:  
  
 ![Visual Studio Format menu with callouts](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501\-d\_FormatMenu")  
  
 **Menügruppen in Visual Studio**  
  
### Reduzieren und Wiederverwendung von Befehlen  
 Befehle werden normalerweise angezeigt basierend auf dem Kontext, um die Anzahl der Befehle zu reduzieren, die Benutzer zu einem beliebigen Zeitpunkt angezeigt wird. Allerdings sollten Sie auch vorhandene freigegebene Menüs wiederverwenden und Befehlsgruppen sicherstellen, dass die Befehlsstruktur relativ bleibt zwischen Änderungen im Kontext stabil.  
  
 Freigegebene Befehle erneut aus, und platzieren neue Befehle nahe verwandter freigegebenen Befehle verringert die Komplexität der IDE, und erstellt eine benutzerfreundlichere Umgebung.  
  
## Benennen von Befehlen  
  
### Namenskonventionen  
 Benennen von konsistenten Befehl ist wichtig, damit Benutzer suchen und Ausführen von Befehlen, entweder mithilfe der Befehlszeile oder an eine Tastenkombination binden können. Befehlsnamen besser auch verstehen, welchen Zweck ein Befehl angegeben wird, wenn er auf einer Symbolleiste oder in einem cascading oder im Kontextmenü angezeigt wird.  
  
#### Wenn Befehle benennen:  
  
-   Erstellen Sie Text, damit es problemlos lokalisiert ist. Weitere Informationen zum Lokalisieren von Text finden Sie unter [World Readiness für Visual Studio](http://msdn.microsoft.com/de-de/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Prägnant sein. Befehle sollten nicht mehr als drei Wörter verwenden.  
  
-   Verwenden Sie die Anfangsbuchstaben Groß\-\/Kleinschreibung: der erste Buchstabe jedes Worts groß geschrieben werden soll. Weitere Informationen zu\-Text\-Format in Visual Studio finden Sie unter [Textstil](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Berücksichtigen Sie, wo der Befehl platziert werden. Handelt es sich in einem Menü der obersten Ebene oder ein Flyout? Z. B. wenn Gruppierung Ausrichtung Befehle in ein Flyout, der obersten Ebene Befehl "Ausrichten" und der Flyout\-Befehle werden sollen sollten "Left",""Right","Center","Ausrichtung"werden, usw. Es wäre redundant, nennen Sie die Flyout\-Befehle "Linksbündig" oder "Ausrichten Right."  
  
     ![Visual Studio Format menu](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502\-a\_FormatMenu")  
  
### Verwenden Symbole mit Befehlen  
 Werden bei der Verwendung des Symbols Kopplung mit Befehlen Ersatz. Obwohl die Möglichkeit eines Benutzers zum Identifizieren dieser Befehls einen Befehl ein eindeutiger Bild zuordnen beschleunigt werden, auftreten Übersichtlichkeit und Ineffizienz Bild Überlastung. Die folgenden Regeln helfen zu entscheiden, ob ein Befehlssymbol zu erstellen.  
  
#### Verwenden Sie ein Symbol mit einem Befehl nur, wenn:  
  
-   Der gleiche Befehl verfügt über ein Symbol in einem anderen wichtigen Microsoft\-Produkt wie z. B. Microsoft Office\-Anwendung zugeordnet.  
  
-   Der Befehl wird in einer Standardsymbolleiste platziert werden.  
  
-   Der Befehl ist ein Specialty\-Befehl, der Benutzer wahrscheinlich eine Symbolleiste mit hinzufügen werden die **"Anpassen..."** Dialogfeld.  
  
## Zugriffstasten und Tastenkombinationen  
  
### Übersicht  
 Es gibt zwei Arten von Key Tastenbelegung:  
  
-   **Zugriffstasten** \(auch bekannt als Beschleuniger\) ermöglichen den Zugriff über die Menüs für Befehle und zu jeder Bezeichnung im Dialogfeld\-Benutzeroberfläche. Zugriffstasten werden hauptsächlich für Zugriff, alle Menüs und Steuerelemente für die meisten Dialogfelder zugewiesen sind, sollen nicht gespeichert werden, betreffen nur das aktuelle Fenster und lokalisiert werden.  
  
-   **Tastenkombinationen** verwenden Steuerungstaste \(STRG\) und \-Funktion \(Fn\) folgen. Sie sind für fortgeschrittene Benutzer und mehr Produktivität entwickelt. Sie werden nur die häufigsten verwendete Befehle zugewiesen, und ermöglichen schnellen Zugriff während im Hauptmenü übergangen. Tastenkombinationen gespeichert werden sollen, und für diesen Grund muss zugewiesen konsistent mit dem Profil\-Schema. Wichtige Tastenkombinationsschemas variieren von Profilen. Ein Benutzer kann über Tastenkombinationen anpassen **Extras \> Optionen \> Tastatur**.  
  
### Zuordnen von Tastenkombinationen  
 Zugriffstasten bestehen aus Alt sowie alphanumerische Schlüssel. Zuweisen einer Zugriffstaste auf jedes Menüelement ohne Ausnahme. Führen Sie Windows und die allgemeinen Konventionen für die Zuweisung von Zugriffstasten. z. B. die Zugriffstaste für **Datei \> Neu** werden **Alt, F, N**.  
  
 Nicht verwenden Sie Single\-Pixel\-Zeichen wie z. B. "i" \(in Groß\- oder Kleinbuchstaben\) oder ein Kleinbuchstabe "l", und vermeiden Sie die Verwendung von Zeichen mit Unterlängen \(g, j, p, Q und y\), wie diese schwer zu unterscheiden sind.  
  
 Verwenden Sie keine doppelten Schlüssel, wenn möglich. In Fällen, in denen Duplizierung unvermeidlich ist, behandelt das Menüsystem Konflikte durch durchlaufen alle Befehle, die den Schlüssel verwenden. Als Beispiel für eine hypothetische "Zahl"\-Befehl im Menü Datei, die den Zugriffsschlüssel "N" dupliziert **Alt, F, N** würde eine neue Datei erstellen und **Alt "," F "," N "," N** 'Anzahl'\-Befehl durchführen würden.  
  
### Zuordnen von Tastenkombinationen  
 Vermeiden Sie die neuen Tastenkombinationen zuweisen, da sie nicht für jeden Befehl erforderlich sind, und das System \(und Benutzerspeicher\) steuern, wenn übermäßig beansprucht. Daten aus dem Customer Experience Improvement Program \(CEIP\) gibt an, dass Visual Studio\-Benutzer nur eine kleine Teilmenge der integrierten Tastenkombinationen verwenden.  
  
 Beim Definieren von Tastenkombinationen gelten Sie folgende Regeln:  
  
-   **Verwenden Sie die Steuerungstaste \(STRG\) und \-Funktion \(Fn\) folgen.**  
  
-   **Häufig verwendete Tastenkombinationen zu erhalten.** Behalten Sie die am häufigsten verwendeten Tastenkombinationen.  
  
-   **Erleichtern Sie Tastenkombinationen für den Editor eingeben.** Binden Sie Verknüpfungen einfach auf den Typ auf Befehle, dass Entwickler die meisten beim Schreiben von Code erforderlich. Beispielsweise **Edit.InvokeSmartTag** benötigt eine schnelle Tastenkombinationen wie STRG \+ \/ und nicht Alt \+ Umschalt \+ F10.  
  
-   **So weit wie konsistent versehene Verknüpfungen.**  
  
-   **Führen Sie die Windows\-Richtlinien, um festzustellen, welche Modifizierer Schlüssel einsetzen.** Verwenden Sie STRG\-Tastenkombinationen für Befehle, die umfangreiche verursachen, z. B. Befehle, die für das gesamte Dokument angewendet. Verwenden Sie UMSCHALT\-Taste\-Kombinationen für Befehle, die erweitern oder ergänzen die Aktionen der Standardtastenkombinationen. Verwenden Sie Strg \+ Alt können Sie nicht.  
  
-   **Entfernen von äußeren Verknüpfungen.** Wenn Sie eine ältere Funktion haben, sollten Sie Verknüpfungen, die mit extreme Seltenheit \(weniger als 10 Mal von der CEIP\-Daten\) oder mittlere Seltenheit \(weniger als 100 Mal von der CEIP\-Daten\) verwendet werden, wenn eine Zugriffstaste schnellen Zugriff auf den gleichen Befehl bietet entfernen. Zum Beispiel: Alt, H, C wird Inhalt\-Hilfe geöffnet.  
  
 Es ist keine einfache Möglichkeit zum Kontextmenü Verfügbarkeit zu überprüfen. Wenn Sie eine Verknüpfung hinzufügen möchten, gehen Sie folgendermaßen vor:  
  
1.  Überprüfen Sie die Liste der [Visual Studio 2013\-Verknüpfungen](http://visualstudioshortcuts.com/2013/) zu bestimmen, ob ähnliche Befehle wie Ihre mit gruppieren.  
  
2.  Wechseln Sie zu **Extras \> Optionen \> Umgebung \> Tastatur** und Testen Sie die Verknüpfung. Überprüfen Sie jede Tastaturzuordnungsschema unter aufgeführten "die folgenden zusätzliches Tastaturzuordnungsschema anwenden." Überprüfen Sie Allgemein, c\#, VB und C\+\+\-Profilen, wie die eindeutige Tastenkombinationen freigeben. Die Verknüpfung ist verfügbar, wenn sie nicht in allen diesen zugeordnet ist.