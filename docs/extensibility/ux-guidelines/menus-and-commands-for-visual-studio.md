---
title: Menüs und Befehle für Visual Studio | Microsoft-Dokumentation
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
ms.openlocfilehash: 8f5686f96ce0125cac98ca08582e8407c4e1e926
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937953"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menüs und Befehle für Visual Studio
## <a name="command-usage"></a>Zur Verwendung des Befehls  
  
### <a name="overview"></a>Übersicht  
 Im Gegensatz zu Microsoft Office, das eine Sammlung, die viele einzelne Produkte umfasst ist, enthält Visual Studio viele Produkte, die jeweils ihre Befehlssätze, globale Visual Studio-IDE beitragen. Die IDE verwaltet die Komplexität von Tausenden von Befehlen von Filterfunktionen für den Benutzer basierend auf dem Kontext verfügbar.  
  
 Wenn der Kontext eines Benutzers geändert wird – beispielsweise über ein Design-Fenster ein Fenster für die codebearbeitung - Funktionen, die nicht mit nicht mehr angezeigt wird der neue Kontext. Zur gleichen Zeit, neue Funktionen Oberflächen zusammen mit dynamischen Informationen, z. B. Eigenschaften und Toolbox-Optionen. Der Benutzer muss nicht beachten Sie den Tauschvorgang für den verfügbaren Befehlssatz. Wenn der Benutzer abgelenkt oder verwechseln von Befehlen angezeigt oder ausgeblendet ist, benötigt das Design der Benutzeroberfläche Anpassung. Aktuelle Kontext des Benutzers wird immer in eine oder mehrere Möglichkeiten, wie z. B. in der Titelleiste der IDE, das Fenster "Eigenschaften" oder das Dialogfeld "Eigenschaftenseiten" angegeben.  
  
 Befehlsleisten ermöglicht Flexibilität bei der Benutzeroberfläche. Der einzige Befehl Strukturen inhärenter Lösungen für Visual Studio im Hauptmenü und die wichtigsten Befehlsleiste, die beide angepasst und werden auch ausgeblendet sind. Andere Befehlsleisten angezeigt und ausgeblendet werden auf den Zustand der Anwendung. Toolfenster und Editoren für Dokument können auch eingebettete Symbolleisten in ihre Fensterränder enthalten.  
  
#### <a name="basic-guidelines"></a>Grundlegende Richtlinien  
  
##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Verwenden Sie die vorhandenen freigegebenen Befehle, Befehlsgruppen und Menüs, wann immer möglich.  
 Da Befehle in der Regel basierend auf dem Kontext angezeigt werden, wird Sie Verwendung eines vorhandenen freigegebenen Menüs und Befehlsgruppen sichergestellt, dass die Befehlsstruktur zwischen Änderungen im Kontext relativ konstant bleibt. Wiederverwenden von gemeinsamen Befehle aus, und platzieren die neue Befehle in der Nähe verwandter, freigegebenen Befehle außerdem verringert die Komplexität der IDE, und erstellt eine benutzerfreundlichere Oberfläche. Wenn ein neuer Befehl werden definiert muss, versuchen Sie es an eine vorhandene freigegebene Befehlsgruppe platzieren. Wenn eine neue Gruppe definiert werden muss, platzieren Sie es in einem vorhandenen freigegebenen Menü in der Nähe einer Gruppe von entsprechenden Befehl vor dem Erstellen eines neuen Menüs für der obersten Ebene ein.  
  
##### <a name="do-not-create-icons-for-every-command"></a>Erstellen Sie Symbole für jeden Befehl nicht.  
 Stellen Sie sich sorgfältig durch, bevor Sie ein Befehlssymbol zu erstellen. Symbole, die nur für Befehle erstellt werden soll, die:  
  
-   in einer Standardsymbolleiste angezeigt.  
  
-   voraussichtlich von Benutzern hinzugefügt werden, um eine Symbolleiste über dem **anpassen...**  Dialogfeld.  
  
-   haben Sie ein Symbol, das die gleiche Aktion in einem anderen Microsoft-Produkt zugeordnet.  
  
##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Beschränken Sie das Hinzufügen von Tastenkombinationen in Visual Studio  
 Die große Mehrheit der Benutzer nutzen einen kleinen Bruchteil alle verfügbaren Tastenkombinationen. Binden Sie im Zweifelsfall das Feature nicht auf eine Tastenkombination ist. Arbeiten mit Ihrer Benutzer kommen Team vor dem Hinzufügen neuer Tastenkombinationen.  
  
##### <a name="give-commands-a-default-menu-placement"></a>Geben Sie eine standardmäßige Menü-Platzierung Befehle.  
 Denken Sie daran, dass Ihre Befehle von anderen angepasst werden und entsprechend zu entwerfen. Es gibt keine als ausgeblendete Befehl. Alle Visual Studio-Befehle angezeigt werden, der **Tools > Anpassen** Dialogfeld, das Befehlsfenster, automatische Vervollständigung der **Tools > Optionen > Tastatur** Dialogfeld ein, und die Entwicklung Tools-Umgebung (DTE). Stellen Sie sicher, um Ihre Befehle einen Namen und eine QuickInfo in der .ctc-Datei zu gewähren, damit Benutzer sie leicht finden können.  
  
##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Duplizieren Sie freigegebenen Befehle in einer eingebetteten Symbolleiste nicht.  
 Es ist hilfreich, um Befehle in der Nähe der Benutzer den Fokus auf den zu platzieren. Eine Möglichkeit hierzu ist eine eingebettete Symbolleiste am oberen Rand Ihrer Tool- oder ein Dokument-Editor erstellen. Sollte der Inhaltsbereich im Fenster für die Befehle, die auf die Symbolleiste platziert. Duplizieren Sie freigegebene Befehle auf der diese Symbolleiste nicht. Beispiel: Legen Sie niemals ein Symbol "Speichern" in einer eingebetteten Symbolleiste ein.  
  
### <a name="content-and-command-visibility"></a>Sichtbarkeit von Inhalt und Befehl  
 Befehle vorhanden sind, in den folgenden Bereichen: **Umgebung**, **Hierarchie**, und **Dokument**. Kennen Sie jeden Bereich, um die Platzierung der Befehl vertrauen können.  
  
 Befehle in der **Umgebung** Bereich primären Kontext herzustellen, und zwischen mehreren Kontexten freigegeben werden. Ändern der Sichtbarkeit oder die Anordnung von Dokumenten und Toolfenster. Zwischen den Befehlen in der Umgebung sind **neues Projekt**, **Herstellen einer Verbindung mit Server**, **Prozess anhängen**, **Ausschneiden**,  **Kopie**, **einfügen**, **finden**, **Optionen**, **anpassen**, **neues Fenster**, und **Hilfe anzeigen**.  
  
 Befehle in der **Hierarchie** Bereich Verwalten von Hierarchien in Visual Studio, einschließlich **Projekt**, **Team**, und **Daten**. Hängen sie mit eines Projekts unterkontextbehälter – z. B. **Debuggen**, **erstellen**, **Test**, **Architektur**, oder **analysieren** . Zwischen den Befehlen in der Hierarchie gelten **neues Element hinzufügen**, **neue Abfrage**, **Projekteinstellungen**, **neue Datenquelle hinzufügen**, **Leistungs-Assistenten starten**, und **neues Diagramm**.  
  
 Befehle in der **Dokument** Bereich Act auf dem Inhalt eines Dokuments, z. B. Code, entwerfen oder eine Arbeitselementabfrage ("WIQ"). Klicken sie auch wirken sich auf die Ansicht eines Toolfensters oder andernfalls für dieses Toolfenster spezifisch sind. Bereich standarddokumentbefehle auch fungieren, auf die Dateiobjekte, die Hierarchie-spezifisch ist, z. B. sind **aus Projekt entfernen**. Zwischen den Befehlen im Dokument sind **Umgestalten > Umbenennen**, **Kopie der Arbeitsaufgabe erstellen**, **alle erweitern**, **alle reduzieren**, und **Benutzeraufgabe erstellen**.  
  
### <a name="command-placement-decisions"></a>Befehl Platzierung Entscheidungen  
 Nachdem Sie entschieden haben, um einen Befehl erstellen, müssen Sie die entsprechende Platzierung und angibt, ob eine Tastenkombination erstellen zu bestimmen. Führen Sie diese Entscheidung Pfad zum Einrichten von platzieren Sie den Befehl aus:  
  
 ![Befehlspositionierung](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-A_CommandPlacement")  
  
 **Pfad der Entscheidung für die Platzierung der Befehl in Visual Studio**  
  
### <a name="command-placement-in-menus"></a>Befehl Platzierung in Menüs  
  
#### <a name="main-menu-bar"></a>Menüleiste "Main"  
 Die Hauptmenüleiste sollte im Standardspeicherort für alle Pakete kontextspezifische Befehle, die an der Benutzeroberfläche beitragen. Die Hauptmenüleiste unterscheidet sich von anderen Befehlsstrukturen, da die Umgebung steuern verwendet welche Befehle angezeigt werden. Deaktivieren Sie alle anderen Befehlsleisten einfach Befehle, die aus dem Kontext sind, ob sie in einem Menü oder auf einer Symbolleiste platziert werden.  
  
 Die Umgebung definiert eine Reihe von Befehlen, die in der Hauptmenüleiste integriert, die über die gesamte IDE und mehrere Task-Domänen hinweg gemeinsam sind. Diese Befehle sind immer sichtbar unabhängig davon, ob der VSPackages in der Umgebung geladen. Auch wenn dieser Satz von Befehlen von VSPackages erweitern können, ist der Befehlssatz in jedes Produkt und die Positionierung der Befehle für die die Verantwortung für jedes Team.  
  
 Die Struktur im Visual Studio-Hauptmenü kann in der folgenden Menükategorien unterteilt:  
  
##### <a name="core-menus"></a>Core-Menüs  
  
-   Datei  
  
-   Bearbeiten  
  
-   Ansicht  
  
-   Tools  
  
-   Fenster  
  
-   Help  
  
##### <a name="project-specific-menus"></a>Projektspezifische Menüs  
  
-   Projekt  
  
-   Build  
  
-   Debug  
  
##### <a name="context-specific-menus"></a>Kontextspezifische-Menüs  
  
-   Team  
  
-   Daten  
  
-   Test  
  
-   Architektur  
  
-   Analysieren  
  
##### <a name="document-specific-menus"></a>Für die spezifischen-Menüs  
  
-   Format  
  
-   Tabelle  
  
##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Beim Entwerfen von Hauptmenüs, befolgen Sie die folgenden Regeln:  
  
-   Nicht mehr als 25 Elemente der obersten Ebene in einem bestimmten Kontext  
  
-   Menüs sollte niemals mehr als 600 Pixel hoch.  
  
-   Auswerten von ein Hauptmenü in mehreren Kontexten wie z. B. in die Ultimate-SKU und des allgemeinen Profils.  
  
-   Flyout-Menüs sind zulässig.  
  
-   Flyout-Menüs sollte mindestens drei Elemente und nicht mehr als sieben enthalten.  
  
-   Flyout-Menüs gesendet werden sollen nur eine Ebene tief – einige Visual Studio-Menüelemente haben cascading Untermenüs, aber dieses Muster wird nicht empfohlen.  
  
-   Verwenden Sie nicht mehr als sechs Trennzeichen. Gruppierungen sollte der folgenden Abbildung entsprechen:  
  
     ![Richtlinien für die Gruppierung des Hauptmenüs](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-B_MainMenus")  
  
-   Es ist zwar nicht erforderlich, jede Gruppe in der Abbildung zu erhalten, ist das Hinzufügen von zusätzlichen Gruppierungen, beschränkt.  
  
-   Jede Gruppe sollte zwischen zwei und sieben Menüelemente verfügen.  
  
#### <a name="main-menu-ordering"></a>Sortieren im Hauptmenü  
 Erwägen Sie vor dem Hinzufügen eines neuen Elements für der obersten Ebene, platzieren den Befehl in einem vorhandenen Menü für der obersten Ebene aus. Wenn Sie ein neues Hauptebenen-Menüelement hinzufügen, achten Sie darauf, dass Sie an der aktuellen Position platzieren. Entscheiden Sie, ob das Menü für Projekt, Kontext oder Dokument spezifisch ist. Behalten Sie den Namen des Menüs der obersten Ebene präzise, und verwenden Sie nur aus einem Wort.  
  
 Die Core-Menüs sollten Stütze für die restlichen Befehle. Datei, bearbeiten und anzeigen sollte immer auf der linken und der Tools, Fenster und Hilfe sollte immer auf der rechten Seite sein.  
  
#### <a name="context-menus"></a>Kontextmenüs  
 Zu viele Funktionen in den Kontextmenüs führt eine schwierig zu erlernendes-Schnittstelle. Alle wichtigen Funktionen sollte der Hauptmenüleiste verfügbar. Position der Befehle sollten mit vorhandenen Befehle aus, um doppelte Befehle vermeiden abgestimmt werden. Kontextmenüs zu sehen definiert in die Shell Standardmenü-Gruppen, die abhängig davon, ob das Kontextmenü für die Lösung, einen Projektknoten aus, oder ein Projektelement enthalten sein sollen.  
  
 Beim Entwerfen von Kontextmenüs, halten Sie den gleichen Regeln wie für das Hauptmenü, und darüber hinaus:  
  
-   Überschreiten Sie 25 Menüelemente der obersten Ebene nicht.  
  
-   Flyout-Menüs sind zulässig muss, aber nicht mehr als eine Ebene tief – verwenden Sie niemals kaskadierende Flyouts.  
  
-   Verwenden Sie nicht mehr als sechs Trennzeichen.  
  
### <a name="command-placement-in-toolbars"></a>Befehl Platzierung in Symbolleisten  
  
#### <a name="general-toolbars"></a>Allgemeine Symbolleisten  
 Beim Entwerfen und Anordnen von Symbolleisten, führen Sie diese Standards:  
  
-   Verwenden Sie nicht mehr als ein Verb pro Schaltfläche. Eine Schaltfläche eine Aktion =.  
  
-   Verwenden Sie Text neben dem Symbol an, nur, wenn sie mit der Bezeichnung gestärkt werden muss.  
  
-   Verwenden Sie ein Kombinationsfeld, ausschließlich für die Eigenschaften, die mehrere Male in einer Sitzung gewechselt werden. Andernfalls machen Sie Eigenschaft an anderer Stelle verfügbar.  
  
-   Die Breite eines Kombinationsfelds sollte es sich um die Breite des am längsten Elements in der Box + 30 % entsprechen. Wenn Sie der längsten 200 Pixel ist, sollte im Kombinationsfeld z. B. 260 Pixel breit sein.  
  
-   Schränken Sie die Verwendung von Trennzeichen. Die Verwendung eines Trennzeichens neben einer Dropdownliste ist als Antimuster, da die Form im Dropdownmenü auf sich selbst als visual Trennzeichen fungiert.  
  
-   Symbol für Gruppen müssen drei bis sechs Symbole enthalten.  
  
-   Wenn mehrere hilfreiche Befehle Qualifizierer führen, verwenden Sie eine unterteilte Schaltfläche, die die letzte Einstellung speichert:  
  
     ![Unterteilte Schaltflächen in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-C_SplitButtons")  
  
     **Beispiel für eine unterteilte Schaltfläche. Die sechs Befehle auf der linken Seite passt sich stattdessen in einer einzelnen Schaltfläche.**  
  
#### <a name="product-specific-toolbars"></a>Produktspezifische Symbolleisten  
 Jedes Produkt bieten, dass standardmäßig Symbolleiste enthält häufig verwendete und wichtige Befehle und jedes Produkt in der Standardsymbolleiste das erstmalige anzeigen sollte, wenn Visual Studio gestartet wird, nachdem das Produkt installiert ist.  
  
 Produkte sollte auch nutzen, freigegebene Befehlsgruppen und Menüs, die von der IDE bereitgestellt. Jede freigegebene Befehlsgruppe befindet sich in einem freigegebenen Menü zum Organisieren verwandter Befehle auf sinnvolle Weise für den Benutzer vorgesehen. Es ist wichtig, diese freigegebenen Befehlsstruktur zu nutzen, um die Komplexität zu reduzieren.  
  
#### <a name="global-toolbars"></a>Globale Symbolleisten  
 Globale Symbolleisten sind erforderlich, um auf eine Zeile direkt integriert und passen. Wenn Sie eine neue globale Symbolleiste zu erstellen, führen Sie die Richtlinien für diesen Symbolleistentyp aus.  
  
 **Richtlinien für die allgemeine Symbolleiste:**  
  
- Jede Symbolleiste ist 24 Pixel in allgemeine Steuerelemente (ziehelements, Überlauf).  
  
- Jede Symbolleisten-Schaltfläche ist 22 Pixel breit ist, einschließlich der Auffüllung. Machen dem Symbol eine unterteilte Schaltfläche fügt eine andere 11 Pixel Breite.  
  
- Duplizierung der Befehle in Symbolleisten ist zulässig.  
  
  **Für die spezifischen Symbolleisten** angezeigt werden, wenn Sie ein bestimmten Dateityp aktiv ist und nicht mehr angezeigt, wenn ein anderes Dateiformat aktiv wird.  
  
- Für die spezifischen Symbolleisten verfügen möglicherweise nicht mehr als 12 Tasten.  
  
- Die gesamte Breite der Symbolleiste darf 300 Pixel nicht überschreiten.  
  
- Jeder Dateityp haben einen eingebetteten Symbolleiste oder einen globalen dokumentspezifische-Symbolleiste, aber nicht beide.  
  
  **Kontextspezifische Symbolleisten** angezeigt werden, wenn einem bestimmten Kontext festgelegt ist und in der Regel für einen längeren Zeitraum aktiv bleiben.  
  
- Die Schaltfläche für alle kontextspezifische Symbolleisten beträgt 18.  
  
- Wenn die meisten Benutzer konsistent Befehle der Symbolleiste verwenden wird nicht, wenn der Kontext aktiv ist, klicken Sie dann nicht zuordnen dieser Symbolleiste mit einem Kontext.  
  
- Stellen Sie sicher, dass die Symbolleiste nicht mehr angezeigt, beim Beenden von Kontext wird. Beim Start sollte keinem dieser Symbolleisten angezeigt werden.  
  
  **Symbolleisten ohne Kontext** nie automatisch angezeigt. Diese zeigen nur, wenn sie der Benutzer aktiviert. Behalten Sie die maximale Breite unter 200 Pixel.  
  
### <a name="general-organization-and-shell-defined-groups"></a>Allgemeine Organisation und Shell definierte Gruppen  
 Verwenden Sie die vorhandenen freigegebenen Befehle, Befehlsgruppen und Menüs. Wenn ein neuer Befehl werden definiert muss, versuchen Sie es an eine vorhandene freigegebene Befehlsgruppe platzieren. Wenn eine neue Gruppe werden definiert muss, versuchen Sie es vor dem Erstellen eines neuen Menüs für der obersten Ebene in einem vorhandenen freigegebenen Menü in der Nähe einer Gruppe von entsprechenden Befehl zu platzieren. Dies reduziert die Komplexität der Befehl, und gleichzeitig sicherstellen von konsistenten Befehl Platzierung in der IDE.  
  
 Der gemeinsam verwendeten **Format** im Kontext des Designer-Stil Dokumentfenstern, in der Regel dargestellte Menü wird in der folgenden Abbildung veranschaulicht:  
  
 ![Im Menü von Visual Studio-Format mit Beschriftungen](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-D_FormatMenu")  
  
 **Menügruppen im Visual Studio**  
  
### <a name="reducing-and-reusing-commands"></a>Reduzieren und die Wiederverwendung von Befehlen  
 Befehle sind in der Regel angezeigt, basierend auf dem Kontext, um die Anzahl der Befehle, die dem Benutzer angezeigt, zu jedem Zeitpunkt wird, zu reduzieren. Allerdings sollten Sie auch vorhandene freigegebene Menüs wiederverwenden und Befehlsgruppen aus, um sicherzustellen, dass die Befehlsstruktur relativ bleibt zwischen Änderungen im Kontext stabil.  
  
 Wiederverwenden von gemeinsamen Befehle aus, und platzieren die neue Befehle in der Nähe verwandter, freigegebenen Befehle verringert die Komplexität der IDE, und erstellt eine benutzerfreundlichere Oberfläche.  
  
## <a name="naming-commands"></a>Benennen die Befehle  
  
### <a name="naming-conventions"></a>Namenskonventionen   
 Benennen von konsistenten Befehl ist wichtig, damit Benutzer finden und Ausführen von Befehlen, indem Sie entweder mithilfe der Befehlszeile oder Bindung an eine Tastenkombination können. Befehlsnamen können auch die Benutzer wissen, welchem Zweck ein Befehl angegeben wird, wenn er auf einer Symbolleiste oder in einem cascading oder Kontext-Menü angezeigt wird.  
  
#### <a name="when-naming-commands"></a>Wenn Befehle benennen:  
  
-   Erstellen Sie Text aus, sodass sie problemlos lokalisiert ist. Weitere Informationen zum Lokalisieren von Text finden Sie unter [World Readiness für Visual Studio](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Werden Sie präzise. Befehle sollten nicht mehr als drei Wörter verwenden.  
  
-   Verwenden Sie große Anfangsbuchstaben Groß-/Kleinschreibung: der erste Buchstabe jedes Worts groß geschrieben werden soll. Weitere Informationen zur textformatierung, die in Visual Studio finden Sie unter [Textart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Berücksichtigen Sie, wo der Befehl platziert werden. Handelt es sich in einem Menü der obersten Ebene oder ein Flyout? Z. B. wenn Gruppierung Ausrichten von Befehlen in ein Flyout, den obersten Ebene Befehl "Align" und der Flyout-Befehle werden sollen sollte "Left" "Right", "Center", "Blocksatz" sein, und so weiter. Es wäre redundant, benennen Sie die Flyout-Befehle "Linksbündig" oder "Align Right."  
  
     ![Visual Studio-Format zum Menü ","](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-A_FormatMenu")  
  
### <a name="using-icons-with-commands"></a>Mithilfe von Symbolen mit Befehlen  
 Das Ersetzen Sie werden bei der Verwendung des Symbols, die Kopplung mit Befehlen. Zwar die Fähigkeit des Benutzers, um diesen Befehl zu identifizieren. Zuordnung ein eindeutiges Image mit einem Befehl beschleunigt werden, werden visuelle Überfrachtung und Ineffizienz mit Bild übermäßige auftreten. Die folgenden Regeln helfen bei der Entscheidung, ob ein Befehlssymbol zu erstellen.  
  
#### <a name="use-an-icon-with-a-command-only-if"></a>Verwenden Sie ein Symbol mit nur ein Befehl, wenn ein:  
  
-   Der gleiche Befehl verfügt über ein Symbol in einem anderen deutliche Microsoft-Produkt wie z. B. Microsoft Office-Anwendung zugeordnet.  
  
-   Der Befehl wird in einer Standardsymbolleiste platziert werden.  
  
-   Der Befehl ist eine spezielle-Befehl, der Benutzer wahrscheinlich eine Symbolleiste mit hinzugefügt werden die **"Anpassen..."** Dialogfeld.  
  
## <a name="access-and-shortcut-keys"></a>Zugriff und die Tastenkombinationen  
  
### <a name="overview"></a>Übersicht  
 Es gibt zwei Arten von Tastenbelegung für Schlüssel:  
  
-   **Zugriffsschlüssel** (auch bekannt als Zugriffstasten) ermöglichen den Zugriff über die Menüs für die Befehlseingabe und zu jeder Bezeichnung im Dialogfeld "UI". Zugriffsschlüssel werden hauptsächlich für die Barrierefreiheit zu, alle Menüs und die meisten Dialogfeld-Steuerelementen zugewiesen sind, sind nicht dafür vorgesehen, Sie werden merken können, wirken sich auf nur das aktuelle Fenster und lokalisiert werden.  
  
-   **Tastenkombinationen für den** verwenden STRG- und -Funktion (Fn) folgen. Sie wurden mehr Produktivität für fortgeschrittene Benutzer und Hilfe entwickelt. Sie werden nur die häufigsten verwendete Befehle zugewiesen und ermöglichen schnellen Zugriff beim umgehen im Hauptmenü. Tastenkombinationen für den merken können, werden sollen, und für diesen Grund muss zugewiesen werden konsistent mit dem Profil-Schema. Wichtige Tastenkombinationsschemas variieren von Profilen. Ein Benutzer möglicherweise Tastenkombinationen über anpassen **Tools > Optionen > Tastatur**.  
  
### <a name="assigning-access-keys"></a>Zuordnen von Tastenkombinationen  
 Zugriffsschlüssel bestehen aus Alt plus alphanumerische Schlüssel. Weisen Sie jedes Menüelement ausnahmslos eine Zugriffstaste hinzu zu. Führen Sie Windows und allgemeine Konventionen für das Zuordnen von Tastenkombinationen. z. B. den Zugriffsschlüssel für **Datei > Neu** muss immer **Alt, F, N**.  
  
 Nicht verwenden Sie Single-Pixel-Width-Buchstaben, z. B. "i" (in Groß- oder Kleinbuchstabe) oder den Kleinbuchstaben "l", und vermeiden Sie die Verwendung von Zeichen mit Unterlängen (g, j, p, Q und y), da dies schwierig zu unterscheiden sind.  
  
 Verwenden Sie doppelte Schlüssel, sofern möglich. In Fällen, in denen Duplizierung unvermeidlich ist, verarbeitet das Menüsystem Konflikte durch durchlaufen alle Befehle, die den Schlüssel zu verwenden. Als Beispiel für eine hypothetische "Zahl"-Befehl im Menü "File", die den Zugriffsschlüssel für "N", um Duplikate **Alt, F, N** würde eine neue Datei erstellen und **Alt, F, N, N** würde den "Number"-Befehl ausführen.  
  
### <a name="assigning-shortcut-keys"></a>Zuweisen von Tastenkombinationen  
 Vermeiden Sie das Zuweisen von neuen Tastenkombinationen, da sie nicht für jeden Befehl erforderlich sind, und steuern das System (und die Benutzerspeicher) ein, wenn übermäßig beansprucht. Daten aus der Gruppenrichtlinien-Verwaltungskonsole (Customer Experience Improvement Program, CEIP) gibt an, dass Visual Studio-Benutzer nur eine kleine Teilmenge dieser integrierten Tastenkombinationen verwenden.  
  
 Wenn Sie Verknüpfungen zu definieren, gelten Sie folgende Regeln:  
  
- **Verwenden Sie die STRG- und -Funktion (Fn) folgen.**  
  
- **Häufig verwendete Tastenkombinationen zu erhalten.** Behalten Sie die am häufigsten verwendeten Verknüpfungen.  
  
- **Stellen Sie die Tastenkombinationen für Editoren einfach zu geben.** Binden Sie einfach auf den Typ Tastenkombinationen für Befehle, dass Entwickler die meisten beim Schreiben von Code benötigen. Z. B. **Edit.InvokeSmartTag** benötigt eine schnelle Tastenkombination wie STRG / und nicht Alt + Umschalt + F10.  
  
- **Ziel ist es für konsistent mit Design Verknüpfungen.**  
  
- **Führen Sie die Windows-Richtlinien, um zu bestimmen, welche Modifizierer Schlüssel verwenden.** Verwenden Sie STRG-Tastenkombinationen für Befehle, die umfangreiche Auswirkungen, z. B. Befehle haben, die für ein ganzes Dokument gelten. Verwenden Sie UMSCHALT-Taste-Kombinationen für Befehle, die erweitern oder ergänzen die Aktionen der standardmäßige Tastenkombination. Verwenden Sie nicht STRG + Alt + Kombinationen aus.  
  
- **Entfernen Sie überflüssige Verknüpfungen.** Wenn Sie eine ältere Funktion verfügen, sollten Sie die Verknüpfungen, die mit extrem Seltenheit (weniger als 10 Mal von der CEIP-Daten) oder moderate Seltenheit (weniger als 100 Mal von der CEIP-Daten) verwendet werden, wenn eine Tastenkombination schnellen Zugriff auf den gleichen Befehl ermöglicht werden entfernt. Zum Beispiel: Alt, H, B wird Inhalt-Hilfe geöffnet.  
  
  Es ist keine einfache Möglichkeit zum Prüfen der Verfügbarkeit der Verknüpfung. Wenn Sie eine Verknüpfung hinzufügen möchten, gehen Sie wie folgt vor:  
  
1.  Überprüfen Sie die Liste der [Tastenkombinationen für Visual Studio 2013](http://visualstudioshortcuts.com/2013/) zu ermitteln, ob ähnliche Befehle, um Ihre mit zu gruppieren.  
  
2.  Wechseln Sie zu **Tools > Optionen > Umgebung > Tastatur** und Ihre Verknüpfung testen. Überprüfen Sie, dass jede Tastaturzuordnungsschema unter aufgeführt "die folgenden zusätzliches Tastaturzuordnungsschema anwenden." Überprüfen Sie Allgemein, c#, VB und C++-Profilen, wie die eindeutige Tastenkombinationen freigeben. Die Verknüpfung ist verfügbar, falls es nicht in allen diesen zugeordnet ist.