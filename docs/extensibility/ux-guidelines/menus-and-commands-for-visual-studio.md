---
title: Menüs und Befehle für Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f22b7ac4377b600208c079b6af1eff7fc3cbfc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698387"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menüs und Befehle für Visual Studio
## <a name="command-usage"></a>Befehlsverwendung

### <a name="overview"></a>Übersicht
 Im Gegensatz zu Microsoft Office, einer Suite, die viele separate Produkte umfasst, enthält Visual Studio viele Produkte, die jeweils ihre Befehlssätze zur globalen Visual Studio-IDE beitragen. Die IDE verwaltet die Komplexität von Tausenden von Befehlen, indem sie die dem Benutzer zur Verfügung stehenden Funktionen basierend auf dem Kontext filtert.

 Wenn sich der Kontext eines Benutzers ändert , z. B. der Wechsel von einem Entwurfsfenster zu einem Codebearbeitungsfenster, verschwindet die Funktionalität, die nichts mit dem neuen Kontext zu tun hat. Gleichzeitig werden neue Funktionen zusammen mit zugehörigen dynamischen Informationen, wie Eigenschaften und Toolbox-Optionen, angezeigt. Der Benutzer sollte den Austausch des verfügbaren Befehlssatzes nicht bemerken. Wenn der Benutzer durch das Erscheinen oder Verschwinden von Befehlen abgelenkt oder verwirrt wird, muss der UI-Entwurf angepasst werden. Der aktuelle Kontext des Benutzers wird immer auf eine oder mehrere Arten angezeigt, z. B. in der IDE-Titelleiste, im Eigenschaftenfenster oder im Dialogfeld Eigenschaftenseiten.

 Befehlsleisten ermöglichen Flexibilität in der Benutzeroberfläche. Die einzigen Befehlsstrukturen, die der Visual Studio-Umgebung inhärent sind, sind das Hauptmenü und die Hauptbefehlsleiste, die sowohl angepasst als auch sogar ausgeblendet werden können. Andere Befehlsleisten werden basierend auf dem Status der Anwendung angezeigt und verschwinden. Toolfenster und Dokumenteditoren können auch eingebettete Symbolleisten in ihren Fensterkanten enthalten.

#### <a name="basic-guidelines"></a>Grundlegende Richtlinien

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Verwenden Sie nach Möglichkeit vorhandene freigegebene Befehle, Befehlsgruppen und Menüs.
 Da Befehle in der Regel basierend auf dem Kontext angezeigt werden, stellt die Verwendung vorhandener freigegebener Menüs und Befehlsgruppen sicher, dass die Befehlsstruktur zwischen Kontextänderungen relativ stabil bleibt. Die Wiederverwendung freigegebener Befehle und das Platzieren neuer Befehle in der Nähe verwandter freigegebener Befehle reduziert auch die IDE-Komplexität und schafft eine benutzerfreundlichere Umgebung. Wenn ein neuer Befehl definiert werden muss, versuchen Sie, ihn in einer vorhandenen freigegebenen Befehlsgruppe zu platzieren. Wenn eine neue Gruppe definiert werden muss, platzieren Sie sie in einem vorhandenen freigegebenen Menü in der Nähe einer verknüpften Befehlsgruppe, bevor Sie ein neues Menü der obersten Ebene erstellen.

##### <a name="do-not-create-icons-for-every-command"></a>Erstellen Sie nicht für jeden Befehl Symbole.
 Denken Sie sorgfältig nach, bevor Sie ein Befehlssymbol erstellen. Symbole sollten nur für Befehle erstellt werden, die:

- auf einer Standardsymbolleiste angezeigt werden.

- werden wahrscheinlich von Benutzern über das Dialogfeld **Anpassen...** von Benutzern zu einer Symbolleiste hinzugefügt.

- ein Symbol mit derselben Aktion in einem anderen Microsoft-Produkt verknüpft sind.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Beschränken des Hinzufügens von Tastenkombinationen
 Die überwiegende Mehrheit der Benutzer beschäftigt einen winzigen Bruchteil aller verfügbaren Verknüpfungen. Binden Sie Ihre Funktion im Zweifelsfall nicht an eine Tastenkombination. Arbeiten Sie mit Ihrem Benutzererfahrungsteam, bevor Sie neue Verknüpfungen hinzufügen.

##### <a name="give-commands-a-default-menu-placement"></a>Geben Sie Befehlen eine Standardmenüplatzierung.
 Beachten Sie, dass Ihre Befehle von anderen angepasst werden, und entwerfen Sie sie entsprechend. Es gibt keinen versteckten Befehl. Alle Visual Studio-Befehle werden im Dialogfeld **"Werkzeuge > Anpassen",** im Befehlsfenster, beim automatischen Vervollständigen, im Dialogfeld **Tools > Optionen > Tastatur-** und in der Entwicklungstools-Umgebung (DTE) angezeigt. Stellen Sie sicher, dass Sie Ihren Befehlen einen Namen und eine QuickInfo in Ihrer CTC-Datei geben, damit Benutzer sie leicht finden können.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Duplizieren Sie keine freigegebenen Befehle auf einer eingebetteten Symbolleiste.
 Es ist nützlich, Befehle in unmittelbarer Nähe zum Fokusbereich des Benutzers zu platzieren. Eine Möglichkeit hierfür besteht darin, eine eingebettete Symbolleiste am oberen Rand des Toolfensters oder Dokumenteditors zu erstellen. Die auf der Symbolleiste platzierten Befehle sollten spezifisch für den Inhaltsbereich innerhalb des Fensters sein. Duplizieren Sie keine freigegebenen Befehle auf diesen Symbolleisten. Platzieren Sie beispielsweise niemals ein "Speichern"-Symbol in einer eingebetteten Symbolleiste.

### <a name="content-and-command-visibility"></a>Content- und Befehlssichtbarkeit
 Befehle sind in den folgenden Bereichen vorhanden: **Environment**, **Hierarchy**und **Document**. Kennen Sie jeden Bereich, um Vertrauen in die Befehlsplatzierung zu haben.

 Befehle im **Umgebungsbereich** stellen den primären Kontext fest und werden von mehreren Kontexten gemeinsam genutzt. Sie verändern die Sichtbarkeit oder Anordnung von Dokumenten und Werkzeugfenstern. Zu den Befehlen im Umgebungsbereich gehören **New Project**, Connect **to Server**, Attach **Process**, **Cut**, **Copy**, **Paste**, **Find**, **Options**, **Customize**, **New Window**und **View Help**.

 Befehle im **Bereich Hierarchie** verwalten Hierarchien in Visual Studio, einschließlich **Project**, **Team**und **Data**. Sie beziehen sich auf den Subkontext eines Projekts, z. B. **Debuggen**, **Erstellen**, **Testen**, **Architektur**oder **Analysieren**. Zu den Befehlen im Bereich Hierarchie gehören **Hinzufügen**neuer Elemente , **Neue Abfrage**, **Projekteinstellungen**, **Neue Datenquelle**hinzufügen , **Leistungsassistent starten**und Neues **Diagramm**.

 Befehle im **Dokumentbereich** wirken auf den Inhalt eines Dokuments, z. B. Code, Entwurf oder eine Arbeitsaufgabenabfrage (WIQ). Sie wirken auch auf die Ansicht eines Werkzeugfensters oder sind anderweitig spezifisch für dieses Werkzeugfenster. Dokumentbereichsbefehle wirken auch auf die Dateiobjekte, die selbst hierarchiespezifisch sind, z. B. **Entfernen aus Project**. Zu den Befehlen im Dokumentbereich gehören **Refactor > Rename**, **Create Copy of Work Item**, Expand **All**, **Collapse All**und Create **User Task**.

### <a name="command-placement-decisions"></a>Entscheidungen zur Befehlsplatzierung
 Nachdem Sie sich entschieden haben, einen Befehl zu erstellen, müssen Sie die entsprechende Platzierung und ob eine Tastenkombination erstellt werden soll, ermitteln. Folgen Sie diesem Entscheidungspfad, um festzulegen, wo der Befehl platziert werden soll:

 ![Entscheidungsdiagramm zur Befehlspositionierung](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Entscheidungspfad für die Befehlsplatzierung in Visual Studio**

### <a name="command-placement-in-menus"></a>Befehlsplatzierung in Menüs

#### <a name="main-menu-bar"></a>Hauptmenüleiste
 Die Hauptmenüleiste sollte der Standardspeicherort für Befehle von kontextspezifischen Menüpaketen sein, die zur Benutzeroberfläche beitragen. Die Hauptmenüleiste unterscheidet sich von anderen Befehlsstrukturen dadurch, dass die Umgebung sie verwendet, um zu steuern, welche Befehle sichtbar sind. Alle anderen Befehlsleisten deaktivieren einfach Befehle, die ablgegenden Kontext haben, unabhängig davon, ob sie in einem Menü oder auf einer Symbolleiste platziert werden.

 Die Umgebung definiert eine Reihe von Befehlen, die in der Hauptmenüleiste integriert sind und in der gesamten IDE und in mehreren Aufgabendomänen üblich sind. Diese Befehle sind immer sichtbar, unabhängig davon, welche VSPackages in die Umgebung geladen werden. Obwohl VSPackages diesen Befehlssatz erweitern kann, liegt der Befehlssatz jedes Produkts und die Platzierung der Befehle in der Verantwortung jedes Teams.

 Die Struktur des Visual Studio-Hauptmenüs kann in die folgenden Menükategorien unterteilt werden:

##### <a name="core-menus"></a>Kernmenüs

- Datei

- Edit (Bearbeiten)

- Ansicht

- Tools

- Fenster

- Hilfe

##### <a name="project-specific-menus"></a>Projektspezifische Menüs

- Project

- Build

- Debug

##### <a name="context-specific-menus"></a>Kontextspezifische Menüs

- Team

- Daten

- Test

- Aufbau

- Analysieren

##### <a name="document-specific-menus"></a>Dokumentspezifische Menüs

- Format

- Tabelle

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Beachten Sie beim Entwerfen von Hauptmenüs die folgenden Regeln:

- Nicht mehr als 25 Elemente der obersten Ebene in einem bestimmten Kontext

- Menüs sollten niemals 600 Pixel in der Höhe überschreiten.

- Bewerten Sie ein Hauptmenü in mehreren Kontexten, z. B. in der Ultimate SKU und im Allgemeinen Profil.

- Flyout-Menüs sind akzeptabel.

- Flyout-Menüs sollten mindestens drei Unden mindestens sieben elemente enthalten.

- Flyout-Menüs sollten nur eine Ebene tief gehen - einige Visual Studio-Menüelemente verfügen über kaskadierende Untermenüs, aber dieses Muster wird nicht empfohlen.

- Verwenden Sie nicht mehr als sechs Trennzeichen. Gruppierungen sollten sich an die folgende Abbildung halten:

     ![Richtlinien für die Gruppierung des Hauptmenüs](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Obwohl es nicht erforderlich ist, jede Gruppierung in der Abbildung zu haben, ist das Hinzufügen zusätzlicher Gruppierungen eingeschränkt.

- Jede Gruppierung sollte zwei bis sieben Menüpunkte haben.

#### <a name="main-menu-ordering"></a>Hauptmenü-Bestellung
 Bevor Sie ein neues Element der obersten Ebene hinzufügen, sollten Sie den Befehl in einem vorhandenen Menü der obersten Ebene platzieren. Achten Sie beim Hinzufügen eines neuen Menüs der obersten Ebene darauf, es an der richtigen Position zu platzieren. Entscheiden Sie, ob das Menü projekt-, kontext- oder dokumentspezifisch ist. Halten Sie den Namen des Menüs der obersten Ebene prägnant und verwenden Sie nur ein Wort.

 Die Kernmenüs sollten den Rest der Befehle buchen. Datei, Bearbeiten und Ansicht sollten sich immer links befinden, und Tools, Fenster und Hilfe sollten immer rechts sein.

#### <a name="context-menus"></a>Kontextmenüs
 Das Platzieren zu viel Funktionalität in den Kontextmenüs führt zu einer schwer zu erlernenden Benutzeroberfläche. Alle wichtigen Funktionen sollten über die Hauptmenüleiste verfügbar sein. Die Platzierung von Befehlen sollte mit vorhandenen Befehlen abgestimmt werden, um doppelte Befehle zu vermeiden. Für Kontextmenüs definiert die Shell Standardmenügruppen, die eingeschlossen werden sollen, je nachdem, ob das Kontextmenü für die Projektmappe, einen Projektknoten oder ein Projektelement bestimmt ist.

 Beachten Sie beim Entwerfen von Kontextmenüs die gleichen Regeln wie für das Hauptmenü, und außerdem:

- Überschreiten Sie nicht 25 Menüpunkte der obersten Ebene.

- Flyout-Menüs sind akzeptabel, dürfen aber eine Ebene nicht tief überschreiten - verwenden Sie niemals kaskadierende Flyouts.

- Verwenden Sie nicht mehr als sechs Trennzeichen.

### <a name="command-placement-in-toolbars"></a>Befehlsplatzierung in Symbolleisten

#### <a name="general-toolbars"></a>Allgemeine Symbolleisten
 Befolgen Sie beim Entwerfen und Anordnen von Symbolleisten die folgenden Standards:

- Verwenden Sie nicht mehr als ein Verb pro Taste. Eine Schaltfläche = eine Aktion.

- Verwenden Sie Text neben dem Symbol nur, wenn er mit dem Etikett verstärkt werden muss.

- Verwenden Sie ein Kombinationsfeld ausschließlich für Eigenschaften, die in einer Sitzung mehrmals gewechselt werden. Andernfalls legen Sie die Eigenschaft an einer anderen Stelle frei.

- Die Breite eines Kombinationsfeldes sollte der Breite des längsten Elements innerhalb des Feldes + 30 % entsprechen. Wenn das längste Element beispielsweise 200 Pixel beträgt, sollte das Kombinationsfeld 260 Pixel breit sein.

- Beschränken Sie die Verwendung von Trennzeichen. Die Verwendung eines Trennzeichens neben einer Dropdownliste ist ein Antimuster, da die Form der Dropdown-Liste selbst als visuelles Trennzeichen fungiert.

- Symbolgruppen sollten drei bis sechs Symbole enthalten.

- Wenn Qualifizierer zu mehreren nützlichen Befehlen führen, verwenden Sie eine Geteiltschaltfläche, die die letzte Einstellung speichert:

     ![Unterteilte Schaltflächen in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Beispiel für eine geteilte Schaltfläche. Die sechs Befehle auf der linken Seite können stattdessen in eine einzelne Taste passen.**

#### <a name="product-specific-toolbars"></a>Produktspezifische Symbolleisten
 Jedes Produkt kann eine Standardsymbolleiste bereitstellen, die häufig verwendete und wichtige Befehle enthält, und die Standardsymbolleiste jedes Produkts sollte beim ersten Start von Visual Studio nach der Installation des Produkts angezeigt werden.

 Produkte sollten auch freigegebene Befehlsgruppen und Menüs nutzen, die von der IDE bereitgestellt werden. Jede freigegebene Befehlsgruppe wird in einem freigegebenen Menü platziert, das verwandte Befehle auf sinnvolle Weise für den Benutzer organisieren soll. Es ist wichtig, diese gemeinsame Befehlsstruktur zu nutzen, um die Komplexität zu reduzieren.

#### <a name="global-toolbars"></a>Globale Symbolleisten
 Globale Symbolleisten müssen direkt aus dem Kasten heraus in eine Reihe passen. Befolgen Sie beim Erstellen einer neuen globalen Symbolleiste die Richtlinien für diesen Symbolleistentyp.

 **Allgemeine Symbolleistenrichtlinien:**

- Jede Symbolleiste hat 24 Pixel in gemeinsamen Steuerelementen (Greifer, Überlauf).

- Jede Symbolleistenschaltfläche ist 22 Pixel breit, einschließlich Auffüllung. Wenn Sie das Symbol zu einer geteilten Schaltfläche machen, werden weitere 11 Pixel Breite hinzugefügt.

- Das Dupliieren von Befehlen über Symbolleisten hinweg ist zulässig.

  **Dokumentspezifische Symbolleisten** werden angezeigt, wenn ein bestimmter Dateityp aktiv ist, und verschwinden, wenn ein anderer Dateityp aktiv wird.

- Dokumentspezifische Symbolleisten dürfen nicht mehr als 12 Schaltflächen enthalten.

- Die Gesamtbreite der Symbolleiste darf 300 Pixel nicht überschreiten.

- Jeder Dateityp kann entweder über eine eingebettete Symbolleiste oder eine dokumentspezifische globale Symbolleiste verfügen, jedoch nicht über beides.

  **Kontextspezifische Symbolleisten** werden angezeigt, wenn ein bestimmter Kontext festgelegt ist und dazu neigen, über einen längeren Zeitraum aktiv zu bleiben.

- Die Schaltflächenbeschränkung für alle kontextspezifischen Symbolleisten beträgt 18.

- Wenn die meisten Benutzer die Befehle dieser Symbolleiste nicht konsistent verwenden, wenn der Kontext aktiv ist, verknüpfen Sie diese Symbolleiste nicht mit einem Kontext.

- Stellen Sie sicher, dass die Symbolleiste beim Beenden des Kontexts verschwindet. Keine dieser Symbolleisten sollte beim Start angezeigt werden.

  **Symbolleisten ohne Kontext** werden nie automatisch angezeigt. Diese werden nur angezeigt, wenn der Benutzer sie aktiviert. Halten Sie die maximale Breite unter 200 Pixel.

### <a name="general-organization-and-shell-defined-groups"></a>Allgemeine Organisations- und Shell-definierte Gruppen
 Verwenden Sie vorhandene freigegebene Befehle, Befehlsgruppen und Menüs. Wenn ein neuer Befehl definiert werden muss, versuchen Sie, ihn in einer vorhandenen freigegebenen Befehlsgruppe zu platzieren. Wenn eine neue Gruppe definiert werden muss, versuchen Sie, sie in einem vorhandenen freigegebenen Menü in der Nähe einer verknüpften Befehlsgruppe zu platzieren, bevor Sie ein neues Menü der obersten Ebene erstellen. Dadurch wird die Befehlskomplexität reduziert und gleichzeitig eine konsistente Befehlsplatzierung in der IDE sichergestellt.

 Das Menü **"Freigegebenes Format",** das in der Regel im Kontext von Dokumentfenstern im Designerstil angezeigt wird, wird in der folgenden Abbildung dargestellt:

 ![Visual Studio-Menü "Format" mit Beschriftungen](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Menügruppen in Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Reduzieren und Wiederverwenden von Befehlen
 Befehle werden in der Regel basierend auf dem Kontext angezeigt, um die Anzahl der Befehle zu reduzieren, die der Benutzer zu einem bestimmten Zeitpunkt sieht. Sie sollten jedoch auch vorhandene freigegebene Menüs und Befehlsgruppen wiederverwenden, um sicherzustellen, dass die Befehlsstruktur zwischen den Änderungen im Kontext relativ stabil bleibt.

 Das Erneutverwenden freigegebener Befehle und das Platzieren neuer Befehle in der Nähe verwandter freigegebener Befehle reduziert die IDE-Komplexität und schafft eine benutzerfreundlichere Umgebung.

## <a name="naming-commands"></a>Benennungsbefehle

### <a name="naming-conventions"></a>Namenskonventionen
 Die konsistente Befehlsbenennung ist von entscheidender Bedeutung, damit Benutzer Befehle finden und ausführen können, entweder mithilfe der Befehlszeile oder der Bindung an eine Tastenkombination. Befehlsnamen helfen dem Benutzer auch zu verstehen, welchen Zweck ein Befehl erfüllt, wenn er auf einer Symbolleiste oder in einem Kaskadierungs- oder Kontextmenü angezeigt wird.

#### <a name="when-naming-commands"></a>Beim Benennen von Befehlen:

- Erstellen Sie Text so, dass er leicht lokalisierbar ist. Weitere Informationen zum Lokalisieren von Text finden Sie unter [Bewährte Methoden zur Lokalisierung](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Seien Sie prägnant. Befehle sollten nicht mehr als drei Wörter verwenden.

- Verwenden Sie die Großschreibung des Titels: Der erste Buchstabe jedes Wortes sollte groß geschrieben werden. Weitere Informationen zur Textformatierung in Visual Studio finden Sie unter [Textformat .](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

- Berücksichtigen Sie, wo der Befehl platziert wird. Ist es in einem Top-Level-Menü oder ein Flyout? Wenn Sie z. B. Ausrichtungsbefehle in einem Flyout gruppieren, sollte der Befehl der obersten Ebene "Ausrichten" sein, und die Flyoutbefehle sollten "Links", "Rechts", "Mitte", "Justify" usw. sein. Es wäre redundant, die Flyout-Befehle "Links ausrichten" oder "Rechts ausrichten" zu benennen.

     ![Visual Studio-Menü "Format"](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Verwenden von Symbolen mit Befehlen
 Sparen Sie bei der Verwendung von Symbolpaarung mit Befehlen. Obwohl das Zuordnen eines eindeutigen Bildes zu einem Befehl die Fähigkeit des Benutzers beschleunigt, diesen Befehl zu identifizieren, treten visuelle Unordnung und Ineffizienz bei der Bildübernutzung auf. Die folgenden Regeln helfen ihnen bei der Entscheidung, ob ein Befehlssymbol erstellt werden soll.

#### <a name="use-an-icon-with-a-command-only-if"></a>Verwenden Sie ein Symbol mit einem Befehl nur, wenn:

- Dem gleichen Befehl ist ein Symbol in einem anderen prominenten Microsoft-Produkt zugeordnet, z. B. in einer der Microsoft Office-Anwendungen.

- Der Befehl wird in einer Standardsymbolleiste platziert.

- Der Befehl ist ein Spezialbefehl, den Benutzer wahrscheinlich mithilfe des Dialogfelds **"Anpassen..."** zu einer Symbolleiste hinzufügen.

## <a name="access-and-shortcut-keys"></a>Zugriffs- und Tastenkombinationen

### <a name="overview"></a>Übersicht
 Es gibt zwei Arten von Tastaturtastenzuweisungen:

- **Zugriffstasten** (auch als Beschleuniger bezeichnet) ermöglichen den Tastaturzugriff über die Menüs für die Befehlssuche und auf jede Beschriftung in der Dialog-Benutzeroberfläche. Zugriffsschlüssel dienen meist der Barrierefreiheit, sind allen Menüs und den meisten Dialogfeldsteuerelementen zugewiesen, sollen nicht gespeichert werden, wirken sich nur auf das aktuelle Fenster aus und sind lokalisiert.

- **Tastenkombinationen** verwenden meist Control (Strg) und Funktion (Fn) Tastensequenzen. Sie sind mehr für fortgeschrittene Anwender konzipiert und helfen bei der Produktivität. Sie werden nur den am häufigsten verwendeten Befehlen zugewiesen und ermöglichen einen schnellen Zugriff unter Umgehung des Hauptmenüs. Shortcut-Schlüssel sollen gespeichert werden und müssen daher entsprechend dem Profilschema zugewiesen werden. Shortcut-Schlüsselschemata können von Profil zu Profil variieren. Ein Benutzer kann Tastenkombinationen über **Tools > Optionen > Tastatur**anpassen.

### <a name="assigning-access-keys"></a>Zuweisen von Zugriffsschlüsseln
 Zugriffsschlüssel bestehen aus Alt plus alphanumerischen Schlüsseln. Weisen Sie jedem Menüelement ausnahmslos einen Zugriffsschlüssel zu. Befolgen Sie Windows und allgemeine Konventionen zum Zuweisen von Zugriffsschlüsseln. Der Zugriffsschlüssel für **Datei > Neu** sollte beispielsweise immer **Alt, F, N**sein.

 Verwenden Sie keine Buchstaben mit einer Pixelbreite wie "i" (in Groß- oder Kleinbuchstaben) oder kleinbuchstaben "l" und vermeiden Sie die Verwendung von Zeichen mit untergeordneten Werten (g, j, p, q und y), da diese schwer zu unterscheiden sind.

 Vermeiden Sie es, wenn möglich, doppelte Schlüssel zu verwenden. In Fällen, in denen Eine Duplizierung unvermeidbar ist, behandelt das Menüsystem Konflikte, indem es alle Befehle durchläuft, die die Taste verwenden. Beispielsweise würde für einen hypothetischen Befehl "Number" unter dem Menü Datei, der die Zugriffstaste "N" dupliziert, **Alt, F, N** eine neue Datei erstellen und **Alt, F, N, N** den Befehl "Number" ausführen.

### <a name="assigning-shortcut-keys"></a>Zuweisen von Tastenkombinationen
 Vermeiden Sie das Zuweisen neuer Tastenkombinationen, da sie nicht für jeden Befehl erforderlich sind, und besteuern Sie das System (und den Benutzerspeicher), wenn sie überstrapaziert werden. Daten aus dem Programm zur Verbesserung der Benutzerfreundlichkeit (CIP) weisen darauf hin, dass Visual Studio-Benutzer nur eine kleine Teilmenge der integrierten Verknüpfungen verwenden.

 Befolgen Sie beim Definieren von Verknüpfungen die folgenden Regeln:

- **Verwenden Sie die Tastenfolgen Control (Strg) und Funktion (Fn).**

- **Bewahren Sie häufig verwendete Verknüpfungen auf.** Verwalten Sie die beliebtesten Verknüpfungen.

- **Machen Sie Editor-Verknüpfungen einfach einzugeben.** Binden Sie einfach zu typisierende Verknüpfungen an Befehle, die Entwickler beim Schreiben von Code am meisten benötigen. Beispielsweise muss **Edit.InvokeSmartTag** über eine kurze Tastenkombination wie Strg+/ und nicht über Alt+Umschalt+F10 verfügen.

- **Streben Sie nach konsistenten Themenverknüpfungen.**

- **Befolgen Sie die Windows-Richtlinien, um zu bestimmen, welche Modifikatorschlüssel verwendet werden sollen.** Verwenden Sie Strg-Tastenkombinationen für Befehle mit großen Effekten, z. B. Befehle, die für ein gesamtes Dokument gelten. Verwenden Sie Umschalttastenkombinationen für Befehle, die die Aktionen der Standard-Tastenkombination erweitern oder ergänzen. Verwenden Sie keine Strg+Alt-Kombinationen.

- **Entfernen Sie fremde Verknüpfungen.** Wenn Sie über ein älteres Feature verfügen, sollten Sie Verknüpfungen entfernen, die mit extremer Infrequenz (weniger als 10-mal aus den CEIP-Daten) oder einer moderaten Infrequenz (weniger als 100-mal aus den CEIP-Daten) verwendet werden, wenn ein Zugriffsschlüssel schnellen Zugriff auf denselben Befehl bietet. Beispiel: Alt, H, C öffnet Hilfe/Inhalt.

  Es gibt keine einfache Möglichkeit, die Verfügbarkeit von Verknüpfungen zu überprüfen. Wenn Sie eine Verknüpfung hinzufügen möchten, führen Sie die folgenden Schritte aus:

1. Überprüfen Sie die Liste der [Visual Studio 2013-Verknüpfungen,](http://visualstudioshortcuts.com/2013/) um festzustellen, ob ähnliche Befehle vorhanden sind, mit denen Sie gruppieren können.

2. Wechseln Sie zu **Tools > Optionen > Umgebung > Tastatur,** und testen Sie ihre Verknüpfung. Überprüfen Sie jedes Unterrufungsschema der Tastatur unter "Anwenden des folgenden zusätzlichen Tastaturzuordnungsschemas". Aktivieren Sie die Allgemeinen, C-, VB- und C++-Profile, da diese eindeutige Verknüpfungen gemeinsam nutzen. Ihre Verknüpfung ist verfügbar, wenn sie an keinem dieser Orte zugeordnet ist.
