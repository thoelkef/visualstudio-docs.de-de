---
title: Menüs und Befehle für Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 16f67faf7ffe3a3fd119b7ddf002ab463822a830
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="menus-and-commands-for-visual-studio"></a>Menüs und Befehle für Visual Studio
## <a name="command-usage"></a>Zur Verwendung des Befehls  
  
### <a name="overview"></a>Übersicht  
 Im Gegensatz zu Microsoft Office, d. h. eine Sammlung, die viele einzelne Produkte umfasst, enthält Visual Studio viele Produkte, die jeweils ihre Befehlssätze, globale Visual Studio-IDE beitragen. Die IDE verwaltet die Komplexität von Tausenden von Befehlen durch Filtern der Funktionalität, die dem Benutzer basierend auf den Kontext zur Verfügung.  
  
 Wenn der Kontext eines Benutzers geändert wird – z. B. eine Entwurfsfenster umstellen, um ein Bearbeitungsfenster Code - Funktionalität unabhängig vom stagingstatus verschwindet neue Kontext aus. Zur gleichen Zeit neue Funktionalität Flächen zusammen mit verwandten dynamische Informationen, z. B. Eigenschaften und Toolbox-Optionen. Der Benutzer sollte nicht beachten Sie die Auslagerung für den Befehlssatz verfügbar. Wenn der Benutzer abgelenkt oder verwechseln von Befehlen, die angezeigt oder ausgeblendet ist, benötigt das Design der Benutzeroberfläche Anpassung. Aktuelle Kontext des Benutzers wird immer in eine oder mehrere Möglichkeiten, wie z. B. in der IDE-Titelleiste, Eigenschaftenfenster oder im Dialogfeld "Eigenschaftenseiten" angegeben.  
  
 Befehlsleisten ermöglichen Flexibilität in der Benutzeroberfläche. Der einzige Befehl-Strukturen inhärenten in Visual Studio im Hauptmenü und der Haupt-Befehlsleiste kann beide angepasst und werden selbst ausgeblendet sind. Andere Befehlsleisten angezeigt und ausgeblendet basierend auf den Zustand der Anwendung. Toolfenster und Editoren Dokument können auch eingebettete Symbolleisten in die Fensterränder enthalten.  
  
#### <a name="basic-guidelines"></a>Grundlegende Richtlinien  
  
##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Verwenden Sie die vorhandenen freigegebenen Befehle, Befehlsgruppen und Menüs, wann immer möglich.  
 Da Befehle in der Regel basierend auf den Kontext angezeigt werden, wird sichergestellt, dass Verwendung von vorhandenen freigegebenen Menüs und Befehlsgruppen, dass die Befehlsstruktur zwischen Änderungen im Kontext relativ konstant bleibt. Wiederverwenden von gemeinsamen Befehle und platzieren neue Befehle in der Nähe verwandter freigegebenen Befehle reduziert die Komplexität der IDE und erstellt eine benutzerfreundlichere Oberfläche. Wenn Sie ein neuer Befehl muss definiert werden, versuchen Sie, platzieren Sie es in eine vorhandene freigegebene Befehlsgruppe. Wenn eine neue Gruppe werden definiert muss, fügen Sie ihn vor dem Erstellen eines neuen Menüs der obersten Ebene in einem vorhandenen freigegebenen Menü in der Nähe eine verwandte Befehlsgruppe.  
  
##### <a name="do-not-create-icons-for-every-command"></a>Symbole für jeden Befehl nicht erstellt werden.  
 Muss sorgfältig durchdacht werden ein Symbol "Befehl" zu erstellen. Symbole, die nur für Befehle erstellt werden soll, die:  
  
-   eine Standardsymbolleiste angezeigt.  
  
-   wahrscheinlich von Benutzern hinzugefügt werden, um eine Symbolleiste über dem **anpassen...**  Dialogfeld.  
  
-   haben Sie ein Symbol, das die gleiche Aktion in einem anderen Microsoft-Produkt zugeordnet.  
  
##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Beschränken Sie das Hinzufügen von Tastenkombinationen  
 Die meisten Benutzer aber einen kleinen Anteil der alle verfügbaren Tastenkombinationen gibt. Binden Sie im Zweifelsfall die Funktion nicht an eine Tastenkombination ist. Arbeiten mit Ihrem Benutzerkonto auftreten Team vor dem Hinzufügen von neuen Verknüpfungen.  
  
##### <a name="give-commands-a-default-menu-placement"></a>Geben Sie eine standardmäßige Menü-Platzierung Befehle.  
 Denken Sie daran, dass Ihre Befehle von anderen Benutzern angepasst werden werden und entsprechend zu entwerfen. Es gibt keine solche als ausgeblendete Befehl. Alle Visual Studio-Befehle angezeigt, der **Tools > Anpassen** Dialogfeld, das Befehlsfenster, automatische Vervollständigung der **Tools > Optionen > Tastatur** Dialogfeld und Development Tools-Umgebung (DTE). Stellen Sie sicher, dass Ihre Befehle einen Namen und eine QuickInfo in der CTC-Datei geben, sodass Benutzer sie leicht finden können.  
  
##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Duplizieren Sie freigegebene Befehle in einem eingebetteten Symbolleiste nicht.  
 Es ist hilfreich, um Befehle in der Nähe zu den Clientbereich der Benutzer den Fokus zu platzieren. Eine Möglichkeit hierfür besteht darin eine eingebettete Symbolleiste am oberen Rand der Tool- oder ein Dokument-Editor zu erstellen. Die Befehle auf der Symbolleiste platziert sollte für den Inhaltsbereich innerhalb des Fensters spezifisch sein. Duplizieren Sie freigegebene Befehle auf diesen Symbolleisten nicht. Beispielsweise nie platzieren Sie ein Symbol "Speichern" in einer eingebetteten Symbolleiste.  
  
### <a name="content-and-command-visibility"></a>Sichtbarkeit von Inhalt und Befehl  
 Befehle vorhanden sind, in den folgenden Bereichen: **Umgebung**, **Hierarchie**, und **Dokument**. Kennen Sie jeden Bereich, um den Befehl Platzierung vertrauen können.  
  
 Befehle in der **Umgebung** Bereich primären Kontext herzustellen und zwischen mehreren Kontexten freigegeben werden. Ändern der Sichtbarkeit oder die Anordnung von Dokumenten und Toolfenster. Die Befehle in der Umgebung Bereich zählen **neues Projekt**, **Verbindung mit Server herstellen**, **Prozess anhängen**, **Ausschneiden**,  **Kopie**, **einfügen**, **suchen**, **Optionen**, **anpassen**, **neues Fenster**, und **Hilfe anzeigen**.  
  
 Befehle in der **Hierarchie** Bereich Verwalten von Hierarchien in Visual Studio, einschließlich **Projekt**, **Team**, und **Daten**. Sie beziehen sich auf ein Projekt Unterkontext – z. B. **Debuggen**, **erstellen**, **Test**, **Architektur**, oder **analysieren** . Die Befehle in der Hierarchie Bereich gehören **neues Element hinzufügen**, **neue Abfrage**, **Projekteinstellungen**, **neue Datenquelle hinzufügen**, **Leistungs-Assistenten starten**, und **neues Diagramm**.  
  
 Befehle in der **Dokument** Bereich Act auf den Inhalt eines Dokuments, wie Code, Entwurf oder einer Arbeitsaufgabenabfrage (WIQ). Sie auch, wirken sich auf die Ansicht eines Toolfensters oder anderweitig zu diesem Toolfenster spezifisch sind. Dokument Bereich Befehle auch fungieren, in der File-Objekten, die selbst hierarchiespezifischen, z. B. werden **aus dem Projekt entfernen**. Zwischen den Kommentaren in einem Dokument Bereich sind **Umgestalten > Umbenennen**, **Kopie der Arbeitsaufgabe erstellen**, **alle erweitern**, **alle reduzieren**, und **Benutzeraufgabe erstellen**.  
  
### <a name="command-placement-decisions"></a>Befehl Platzierung Entscheidungen  
 Nachdem Sie entschieden haben, einen Befehl zu erstellen, müssen Sie die Platzierung geeigneten und angibt, ob eine Tastenkombination erstellen zu bestimmen. Führen Sie diese Entscheidung Pfad zum Einrichten von platzieren Sie den Befehl aus:  
  
 ![Zur befehlspositionierung](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501 A_CommandPlacement")  
  
 **Pfad der Entscheidung für die Platzierung der Befehl in Visual Studio**  
  
### <a name="command-placement-in-menus"></a>Befehl Platzierung in Menüs  
  
#### <a name="main-menu-bar"></a>Hauptmenüleiste  
 Der Hauptmenüleiste sollte am Standardspeicherort für alle Pakete, die kontextspezifische Befehle, die an die Benutzeroberfläche beitragen. Der Hauptmenüleiste unterscheidet sich von anderen Befehlsstrukturen, da die Umgebung zum Steuerelement verwendet welche Befehle angezeigt werden. Deaktivieren Sie alle anderen Befehlsleisten einfach Befehle, die außerhalb des Kontexts, sind, ob sie in einem Menü oder auf einer Symbolleiste so platziert werden.  
  
 Die Umgebung definiert eine Reihe von Befehlen, die in der Hauptmenüleiste integriert und mehrere Domänen der Aufgabe und die gesamte IDE gemeinsam sind. Diese Befehle sind immer sichtbar unabhängig von denen VSPackages werden in der Umgebung geladen. Obwohl VSPackages dieser Satz von Befehlen erweitern können, ist der Befehlssatz aus jedes Produkt und die Platzierung von ihren Befehlen die Zuständigkeit für jedes Team an.  
  
 Die Struktur der Visual Studio im Hauptmenü kann in die folgenden Menüs Kategorien unterteilt:  
  
##### <a name="core-menus"></a>Core-Menüs  
  
-   Datei  
  
-   Bearbeiten  
  
-   Ansicht  
  
-   Tools  
  
-   Fenster  
  
-   Hilfe  
  
##### <a name="project-specific-menus"></a>Projektspezifische Menüs  
  
-   Projekt  
  
-   Build  
  
-   Debug  
  
##### <a name="context-specific-menus"></a>Kontextspezifisch Menüs  
  
-   Team  
  
-   Daten  
  
-   Test  
  
-   Architektur  
  
-   Analysieren  
  
##### <a name="document-specific-menus"></a>Dokumentspezifische Menüs  
  
-   Format  
  
-   Tabelle  
  
##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Bei Hauptmenüs entwerfen möchten, befolgen Sie die folgenden Regeln:  
  
-   Nicht mehr als 25 Elemente der obersten Ebene in einem gegebenen Kontext  
  
-   Menüs sollte niemals mehr als 600 Pixel hoch.  
  
-   Auswerten von einem Hauptmenü in mehreren Kontexten wie z. B. in Ultimate SKU und das allgemeine Profil.  
  
-   Dropdown-Menüs sind zulässig.  
  
-   Dropdown-Menüs sollte mindestens drei Elemente und nicht mehr als sieben enthalten.  
  
-   Dropdown-Menüs sollte nur eine Ebene tief go - einige Visual Studio-Menüelemente haben kaskadierende Untermenüs, aber dieses Muster wird nicht empfohlen.  
  
-   Verwenden Sie nicht mehr als sechs Trennzeichen. Gruppierungen sollte der folgenden Abbildung entsprechen:  
  
     ![Richtlinien für die Gruppierung des Hauptmenüs](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501 B_MainMenus")  
  
-   Während es nicht für jede Gruppierung aufweisen, in der Abbildung erforderlich ist, ist das Hinzufügen von zusätzlichen Gruppierungen beschränkt.  
  
-   Jede Gruppe sollte zwischen zwei und sieben Menüelemente haben.  
  
#### <a name="main-menu-ordering"></a>Hauptmenü Sortierung  
 Berücksichtigen Sie vor dem Hinzufügen eines neuen Elements der obersten Ebene, platzieren den Befehl in einem vorhandenen Menü der obersten Ebene aus. Wenn Sie ein neues Menü der obersten Ebene hinzufügen, achten Sie darauf, dass Sie sie am richtigen Speicherort zu platzieren. Entscheiden Sie, ob das Menü für das Projekt, Kontext oder Dokument spezifisch ist. Halten Sie den Namen des Menüs der obersten Ebene präzise und verwenden Sie nur ein Wort.  
  
 Die Core-Menüs sollten Buchstütze den Rest der Befehle. Datei, bearbeiten und anzeigen sollte immer auf der linken und Tools, Fenster und Hilfe sollte immer auf der rechten Seite sein.  
  
#### <a name="context-menus"></a>Kontextmenüs  
 Platzieren zu viel Funktionalität in den Kontextmenüs führt zu einer Schnittstelle schwierig zu lernen. Alle wichtigen Funktionen sollten über der Hauptmenüleiste verfügbar sein. Platzierung von Befehlen sollten mit vorhandenen Befehle zur Vermeidung von doppelten Befehle abgestimmt werden. Kontextmenüs definiert in die Shell Standardmenü-Gruppen, die je nachdem, ob das Kontextmenü für die Projektmappe, die einen Projektknoten oder ein Projektelement enthalten sein sollen.  
  
 Beim Entwerfen von Kontextmenüs folgen Sie denselben Regeln wie für das Hauptmenü und darüber hinaus:  
  
-   Überschreiten Sie 25 Menüelemente auf oberster Ebene nicht.  
  
-   Dropdown-Menüs sind zulässig muss, jedoch nicht mehr als eine Ebene tief - nie verwenden kaskadierende Flyouts.  
  
-   Verwenden Sie nicht mehr als sechs Trennzeichen.  
  
### <a name="command-placement-in-toolbars"></a>Befehl Platzierung in Symbolleisten  
  
#### <a name="general-toolbars"></a>Allgemeine Symbolleisten  
 Beim Entwerfen und Symbolleisten anordnen, führen Sie diese Standards:  
  
-   Verwenden Sie nicht mehr als ein Verb pro Schaltfläche. Eine Schaltfläche = einer Aktion.  
  
-   Verwenden Sie Text neben dem Symbol, nur, wenn sie mit der Bezeichnung gestärkt werden muss.  
  
-   Verwenden Sie ausschließlich für Eigenschaften, die in einer Sitzung mehrfach gewechselt werden, werden ein Kombinationsfeld. Verfügbar zu machen, andernfalls an anderer Stelle die Eigenschaft an.  
  
-   Die Breite eines Kombinationsfelds muss die Breite des längsten Elements innerhalb der im Feld + 30 % entsprechen. Wenn Sie der längsten 200 Pixel ist, sollte im Kombinationsfeld z. B. 260 Pixel breit sein.  
  
-   Schränken Sie die Verwendung von Trennzeichen. Die Verwendung eines Trennzeichens neben der Dropdownliste ist ein Antimuster aus, da die Form der Dropdownliste selbst als einen visuellen Trennzeichens fungiert.  
  
-   Symbol für Gruppen sollte zwischen 3 und sechs Symbole enthalten.  
  
-   Wenn mehrere nützliche Befehle Qualifizierer ergeben, verwenden Sie eine unterteilte Schaltfläche, die die letzte Einstellung speichert:  
  
     ![Unterteilte Schaltflächen in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501 C_SplitButtons")  
  
     **Beispiel einer unterteilten Schaltfläche. Die sechs Befehle auf der linken Seite können in ein einzelnes Optionsfeld stattdessen entsprechen.**  
  
#### <a name="product-specific-toolbars"></a>Produktspezifische Symbolleisten  
 Jedes Produkt bieten, dass standardmäßig Symbolleiste enthält häufig verwendet und wichtige Befehle, und jedes Produkt Standardsymbolleiste erstmalig angezeigt werden, wenn Visual Studio gestartet wird, nachdem das Produkt installiert ist.  
  
 Produkte sollte auch freigegebene Befehlsgruppen und Menüs, die von der IDE bereitgestellt nutzen. Jeder freigegebene Befehlsgruppe befindet sich in einem freigegebenen Menü zum Organisieren verwandter Befehle auf sinnvolle Weise für den Benutzer vorgesehen. Es ist wichtig, diese freigegebene Befehlsstruktur zu nutzen, um die Komplexität zu reduzieren.  
  
#### <a name="global-toolbars"></a>Globale Symbolleisten  
 Globale Symbolleisten sind erforderlich, um auf eine Zeile rechts gebrauchsfertigen passen. Wenn Sie eine neue globale Symbolleiste zu erstellen, befolgen Sie die Richtlinien für diesen Symbolleistentyp aus.  
  
 **Allgemeine Symbolleiste Richtlinien:**  
  
-   Jede Symbolleiste ist 24 Pixel in allgemeine Steuerelemente (ziehelements, Überlauf).  
  
-   Jede Symbolleisten-Schaltfläche ist 22 Pixel, einschließlich Füllzeichen dar. Machen dem Symbol eine unterteilte Schaltfläche fügt einen anderen 11 Pixel Breite.  
  
-   Duplizieren der Befehle in Symbolleisten ist zulässig.  
  
 **Dokumentspezifische Symbolleisten** angezeigt, wenn Sie ein bestimmten Dateityp aktiv ist und nicht mehr angezeigt, wenn ein anderes Dateiformat aktiv ist.  
  
-   Dokumentspezifische Symbolleisten möglicherweise nicht mehr als 12 Schaltflächen.  
  
-   Die Gesamtbreite der Symbolleiste überschreiten 300 Pixel nicht.  
  
-   Jeder Dateityp kann einen eingebetteten Symbolleiste oder einer globalen dokumentspezifische-Symbolleiste verwenden, aber nicht beides aufweisen.  
  
 **Kontextspezifisch Symbolleisten** angezeigt, wenn einem bestimmten Kontext festgelegt ist und in der Regel für längere Zeit aktiv bleiben.  
  
-   Die Schaltfläche für alle kontextspezifisch Symbolleisten beträgt 18.  
  
-   Wenn die meisten Benutzer konsistent Befehle der Symbolleiste einsetzen wird nicht, wenn der Kontext aktiviert ist, klicken Sie dann nicht zuordnen dieser Symbolleiste mit einem Kontext.  
  
-   Stellen Sie sicher, dass die Symbolleiste wird nicht beim Beenden von Kontext mehr. Keines dieser Symbolleisten sollte beim Start angezeigt werden.  
  
 **Symbolleisten mit kein Kontext** nie automatisch angezeigt. Diese zeigen nur, wenn sie der Benutzer aktiviert. Behalten Sie die maximale Breite unter 200 Pixel.  
  
### <a name="general-organization-and-shell-defined-groups"></a>Gesamtorganisation und Shell definierte Gruppen  
 Verwenden Sie die vorhandenen freigegebenen Befehle, Befehlsgruppen und Menüs. Wenn Sie ein neuer Befehl muss definiert werden, versuchen Sie, platzieren Sie es in eine vorhandene freigegebene Befehlsgruppe. Wenn eine neue Gruppe werden definiert muss, versuchen Sie es vor dem Erstellen eines neuen Menüs der obersten Ebene in einem vorhandenen freigegebenen Menü nahe bei einer entsprechenden Befehlsgruppe platzieren. Dies reduziert die Komplexität der Befehl, und gleichzeitig sicherstellen von konsistenten Befehl Platzierung in der IDE.  
  
 Die gemeinsam verwendete **Format** Menü, in der Regel im Kontext des Designer-Stil-Dokumentfenster angezeigt wird in der folgenden Abbildung veranschaulicht:  
  
 ![Menü für Visual Studio-Format mit Beschriftungen](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501 D_FormatMenu")  
  
 **Menügruppen im Visual Studio**  
  
### <a name="reducing-and-reusing-commands"></a>Reduzieren und Wiederverwenden von Befehlen  
 Befehle werden in der Regel angezeigt basierend auf den Kontext, um die Anzahl der Befehle zu reduzieren, die Benutzer zu einem beliebigen Zeitpunkt angezeigt wird. Allerdings sollten Sie auch vorhandenen freigegebenen Menüs wiederverwenden und Befehlsgruppen aus, um sicherzustellen, dass die Befehlsstruktur relativ bleibt zwischen Änderungen im Kontext stabil.  
  
 Wiederverwenden von gemeinsamen Befehle aus, und platzieren neue Befehle in der Nähe verwandter freigegebenen Befehle reduziert die Komplexität der IDE und erstellt eine benutzerfreundlichere Oberfläche.  
  
## <a name="naming-commands"></a>Benennen von Befehlen  
  
### <a name="naming-conventions"></a>Namenskonventionen   
 Benennen von konsistent Befehl ist wichtig, damit Benutzer suchen und Ausführen von Befehlen, indem Sie entweder mithilfe der Befehlszeile oder Binden an eine Tastenkombination können. Befehlsnamen können auch den Benutzer verstehen, welchen Zweck ein Befehl dient, wenn er auf einer Symbolleiste oder in einer cascading oder im Kontextmenü angezeigt wird.  
  
#### <a name="when-naming-commands"></a>Wenn Befehle benennen:  
  
-   Text zu erstellen, sodass sie problemlos lokalisiert ist. Weitere Informationen zum Lokalisieren von Text, finden Sie unter [World Bereitschaft für Visual Studio](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Werden Sie präziser. Befehle sollten nicht mehr als drei Wörtern verwenden.  
  
-   Verwenden Sie die Anfangsbuchstaben Groß-/Kleinschreibung: der erste Buchstabe jedes Worts groß geschrieben werden soll. Weitere Informationen zur textformatierung in Visual Studio finden Sie unter [Textart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Berücksichtigen Sie, wo der Befehl platziert werden. Handelt es sich in einem Menü der obersten Ebene oder ein Flyout? Z. B. wenn Gruppierung Ausrichtung Befehle in einem Flyout, der obersten Ebene Befehl "Ausrichten" und die Flyout-Befehle werden sollen sollte "Links" "Rechts", "Center", "Ausrichtung" werden, und so weiter. Wäre redundant, benennen Sie die Befehle Flyout "Linksbündig" oder "Align-Right".  
  
     ![Visual Studio-Format im Menü](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502 A_FormatMenu")  
  
### <a name="using-icons-with-commands"></a>Symbole verwendet mit Befehlen.  
 Werden bei der Verwendung eines Symbols mit Befehlen Kopplung Ersatz. Obwohl die Möglichkeit des Benutzers zur Identifizierung dieses Befehls einen Befehl ein eindeutiges Image zuordnen beschleunigt werden, erfolgen, visuellen durcheinanders und Ineffizienz mit Bild übermäßige Nutzung. Die folgenden Regeln helfen bei der Entscheidung, ob ein Symbol "Befehl" erstellt.  
  
#### <a name="use-an-icon-with-a-command-only-if"></a>Verwenden Sie ein Symbol mit einem Befehl nur, wenn:  
  
-   Die gleiche Befehl verfügt über ein Symbol in ein anderes deutliche Microsoft-Produkt wie z. B. Microsoft Office-Anwendung zugeordnet.  
  
-   Der Befehl wird in einer Standardsymbolleiste platziert werden.  
  
-   Der Befehl ist eine Spezialisierung-Befehl, der Benutzer wahrscheinlich eine Symbolleiste mit hinzufügen werden die **"Anpassen..."** Dialogfeld.  
  
## <a name="access-and-shortcut-keys"></a>Zugriff und Tastenkombinationen  
  
### <a name="overview"></a>Übersicht  
 Es gibt zwei Arten der Tastenbelegung für Schlüssel:  
  
-   **Zugriffsschlüssel** (auch bekannt als Zugriffstasten) ermöglichen den Zugriff über die Menüs für Befehle und zu jeder Bezeichnung im Dialogfeld "UI". Zugriffsschlüssel werden hauptsächlich für Eingabehilfen Zwecke, alle Menüs und die meisten Dialogfeldsteuerelemente zugewiesen sind, sollen nicht gespeichert werden, betreffen nur das aktuelle Fenster und lokalisiert werden.  
  
-   **Tastenkombinationen** verwenden meistens-Steuerelement (STRG) und -Funktion (Fn) folgen. Sie sind besser für fortgeschrittene Benutzer und hinsichtlich der Produktivität entwickelt. Sie werden nur für die häufigsten verwendete Befehle zugewiesen und ermöglichen schnellen Zugriff als Umgehung im Hauptmenü. Tastenkombinationen gespeichert werden sollen, und für diese Ursache muss zugewiesen werden konsistent mit dem Profil-Schema. Wichtige Tastenkombinationsschemas können aus einem Profil zu variieren. Ein Benutzer kann über Tastenkombinationen anpassen **Extras > Optionen > Tastatur**.  
  
### <a name="assigning-access-keys"></a>Zuordnen von Tastenkombinationen  
 Zugriffstasten bestehen aus Alt plus alphanumerische enthalten. Zuweisen einer Zugriffstaste für jedes Menüelement ohne Ausnahme an. Führen Sie die Windows und allgemeine Konventionen für das Zuordnen von Tastenkombinationen. z. B. den Zugriffsschlüssel für **Datei > neues** muss immer **Alt, F, N**.  
  
 Nicht verwenden Sie einzelne Pixelbreite Buchstaben, z. B. "i" (in Groß- oder Kleinbuchstabe) oder ein Kleinbuchstabe "l", und vermeiden Sie Zeichen mit Unterlängen bestimmt (g, j, p, Q und y) verwenden, da diese schwierig zu unterscheiden sind.  
  
 Verwenden Sie doppelte Schlüssel, wenn möglich. In Fällen, in denen Duplizierung unvermeidlich ist, verarbeitet die Menüsystem Konflikte durch durchlaufen alle Befehle, die den Schlüssel verwenden. Als Beispiel für eine hypothetische "Zahl"-Befehl im Menü "Datei", die den Zugriffsschlüssel "N", um Duplikate **Alt, F, N** würde eine neue Datei erstellen und **Alt, F, N, N** würde den Befehl "Number" ausführen.  
  
### <a name="assigning-shortcut-keys"></a>Zuordnen von Tastenkombinationen  
 Vermeiden Sie die neuen Tastenkombinationen zuweisen, da sie nicht für jeden Befehl erforderlich sind, und das System (und die Benutzerspeicher) steuern, wenn übermäßig beansprucht. Daten aus der Customer Experience Improvement Program (CEIP) gibt an, dass Visual Studio-Benutzer nur eine kleine Teilmenge der integrierten Tastenkombinationen verwenden.  
  
 Wenn Sie Verknüpfungen zu definieren, führen Sie diese Regeln:  
  
-   **Verwenden Sie-Steuerelement (STRG) und -Funktion (Fn) folgen.**  
  
-   **Beibehalten von häufig verwendeten Tastenkombinationen.** Behalten Sie die am häufigsten verwendeten Tastenkombinationen.  
  
-   **Erleichtern Sie Tastenkombinationen für den Editor eingeben.** Binden Sie einfach auf den Typ Verknüpfungen auf Befehle, die Entwickler benötigen, die meisten beim Schreiben von Code. Beispielsweise **Edit.InvokeSmartTag** benötigt eine schnelle Tastenkombinationen wie STRG c++ / und nicht Alt + Umschalt + F10.  
  
-   **Bemühen Sie konsistent Designs Tastenkombinationen.**  
  
-   **Führen Sie die Windows-Richtlinien, um zu bestimmen, welche Modifizierer Schlüsseln einsetzen.** Verwenden Sie STRG-Tastenkombinationen für Befehle, die umfangreiche Auswirkungen, wie z. B. Befehle haben, die für ein gesamtes Dokument gelten. Verwenden Sie UMSCHALT-Taste-Kombinationen für Befehle, die erweitern oder die Aktionen der Standardtastenkombinationen ergänzen. Verwenden Sie nicht STRG + Alt + Kombinationen aus.  
  
-   **Entfernen Sie unnötige Verknüpfungen.** Wenn Sie eine ältere Funktion haben, sollten Sie, entfernen Verknüpfungen, die mit extremer Seltenheit (weniger als 10 Mal von der CEIP-Daten) oder Mittel Seltenheit (weniger als 100 Mal von der CEIP-Daten) verwendet werden, wenn eine Zugriffstaste schnellen Zugriff auf den gleichen Befehl bereitstellt. Zum Beispiel: Alt, H, C wird Inhalt-Hilfe geöffnet.  
  
 Es ist keine einfache Möglichkeit zum Kontextmenü Verfügbarkeit zu überprüfen. Wenn Sie eine Verknüpfung hinzufügen möchten, gehen Sie folgendermaßen vor:  
  
1.  Überprüfen Sie die Liste der [Tastenkombinationen für Visual Studio 2013](http://visualstudioshortcuts.com/2013/) zu bestimmen, ob es sind ähnliche Befehle aus, um Ihre mit gruppieren.  
  
2.  Wechseln Sie zu **Extras > Optionen > Umgebung > Tastatur** und Testen Sie die Verknüpfung. Überprüfen Sie, dass jede Tastaturzuordnungsschema unter aufgeführt "die folgenden zusätzliches Tastaturzuordnungsschema anwenden". Überprüfen Sie Allgemein, c#, VB und C++-Profile aus, wie die eindeutige Tastenkombinationen freigeben. Die Verknüpfung ist verfügbar, wenn er nicht in einem dieser Orte zugeordnet ist.