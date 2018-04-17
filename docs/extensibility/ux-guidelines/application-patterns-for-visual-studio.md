---
title: Anwendungsmuster für Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a793651660c456213c0e91c0d6c6474cccf3f7d8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="application-patterns-for-visual-studio"></a>Anwendungsmuster für Visual Studio
##  <a name="BKMK_WindowInteractions"></a> Fenster Interaktionen  
  
### <a name="overview"></a>Übersicht  
In Visual Studio verwendet die beiden im Hauptfenster-Typen sind Dokument-Editoren und Toolfenster. Seltene, aber möglich, sind große nicht modale Dialogfelder. Obwohl es sich alle in der Shell nicht modalen handelt, sind ihre Muster grundlegend. Dieser Abschnitt behandelt den Unterschied zwischen Dokumentfenster und Toolfenster nicht modale Dialogfelder. Modales Dialogfeld Muster finden Sie [Dialoge](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Vergleichen von Verwendungsmustern Fenster  
**Dokumentieren von Windows** werden fast immer angezeigt, innerhalb des Dokuments ebenfalls. Dies ermöglicht dem Dokument-Editor eine "center Phase" ergänzende Toolfenster um anordnen.  
  
Ein **Toolfenster** wird am häufigsten als separate, kleinere Fenster für den Rand der IDE reduziert angezeigt. Dies kann sichtbar, ausgeblendet oder automatisch ausgeblendet sein. Allerdings manchmal Toolfenstern Clientanzahl innerhalb des Dokuments, auch durch Deaktivieren der **Fenster/andocken** Eigenschaft im Fenster. Dies führt zu mehr Immobilien, aber auch eine gemeinsame entwurfsentscheidung: beim Versuch, die in Visual Studio integrieren, müssen Sie entscheiden, ob die Funktion eines Toolfensters oder einem Dokumentfenster angezeigt werden soll.  
  
**Nicht modale Dialogfelder** sind in Visual Studio abgeraten. Die meisten nicht modale Dialogfelder sind, per Definition Gleitkomma-Toolfenster und auf diese Weise implementiert werden sollte. Nicht modale Dialogfelder dürfen in Fällen, in denen die Größe von einem normalen Toolfenster auf der Seite der Shell angedockt zu eingeschränkt erweisen würde. Sie dürfen auch in Fällen, in denen der Benutzer wahrscheinlich so verschieben Sie das Dialogfeld zu einem sekundären Monitor sein.  
  
Denken Sie an, zu dem Container müssen Sie sorgfältig. Häufige Muster Aspekte bei der Verwendung Benutzeroberflächendesign sind in der folgenden Tabelle.  
  
||Dokumentfenster|Toolfenster|Nicht modalem Dialogfeld|  
|-|---------------------|-----------------|---------------------|  
| **Position** | Immer auch innerhalb des Dokuments positioniert und ist nicht an den Rändern der IDE andocken. Sie können "abgerufen werden, deaktiviert", damit es separat von der main-Shell: verschiebt. | Im Allgemeinen als Registerkarte an den Rändern der IDE angedockt jedoch können benutzerdefinierte in Gleitkommazahlen werden, werden automatisch ausgeblendete (unpinned) oder auch innerhalb des Dokuments angedockt.|Große unverankerte Fenster "getrennt von der IDE. |  
| **Commit-Modell** | *Verzögerter commit*<br /><br /> Um die Daten in einem Dokument speichern möchten, muss der Benutzer ausgeben der **Datei &gt; speichern**, **speichern unter**, oder **alle speichern** Befehl. Ein Dokumentfenster wurde das Konzept der Daten darin wird "verunreinigt" klicken Sie dann auf einen der speichern committed Befehle. Bei einem Dokumentfenster zu schließen, werden alle Inhalte entweder auf einem Datenträger gespeichert oder verloren geht. | *Sofortige commit*<br /><br /> Es ist kein speichern Modell. Inspektor-Toolfenster, die bei der Bearbeitung einer Datei, die Datei muss im aktiven Editor oder Designer geöffnet sein und der Editor bzw. Designer besitzt speichern. | *Verzögerte oder sofortige commit*<br /><br /> In den meisten Fällen ein großes nicht modales Dialogfeld erfordert eine Aktion aus, um Änderungen zu übernehmen und kann für einen Vorgang "Abbrechen", der alle Änderungen, die innerhalb der Dialogfeld-Sitzung ein Rollback ausgeführt.  Dies unterscheidet ein nicht modales Dialogfeld aus einem Toolfenster, Toolfenster immer ein Modell der sofortige Commit enthalten. |  
| **Sichtbarkeit** | *(Datei) öffnen oder erstellen und schließen*<br /><br /> Öffnen ein Dokumentfenster erfolgt entweder über ein vorhandenes Dokument öffnen oder mithilfe einer Vorlage zum Erstellen eines neuen Dokuments. Es gibt keine "Open \<bestimmten Editor >" Befehl. | *Anzeigen und ausblenden*<br /><br /> Einzelinstanz-Toolfenster können ausgeblendet oder angezeigt werden. Inhalt und Status des Toolfensters persistent zu speichern, ob in der Sicht oder ausgeblendet. Toolfenster mit mehreren Instanzen können geschlossen ausgeblendet als auch sein. Wenn ein Toolfenster mit mehreren Instanzen geschlossen wird, wird Inhalt und Status innerhalb des Toolfensters verworfen. | *Von einem Befehl gestartet*<br /><br /> Dialogfelder werden von einem Befehl aufgabenbasierte gestartet. |  
| **Instanzen** | *Mit mehreren Instanzen*<br /><br /> Einige Editoren können am selben Zeit und Bearbeitung von anderen Dateien, geöffnet sein, während einige Editoren auch die gleiche Datei im Editor für mehrere geöffnet sein können (mithilfe der **Fenster &gt; neues Fenster** Befehl).<br /><br /> Ein einzigen Editor möglicherweise eine oder mehrere Dateien gleichzeitig (Projekt-Designer) bearbeiten. | *Einzelne oder mehrere instance*<br /><br /> Inhalt ändern, um widerzuspiegeln Kontext (wie in den Eigenschaftenbrowser) oder den Fokus/Kontext einen push an andere Windows (Aufgabenliste, Projektmappen-Explorer).<br /><br /> Sowohl mit mehreren Instanzen als auch Einzelinstanz-Toolfenster darf das aktive Fenster zugeordnet sein, es sei denn, es ist kein zwingender Grund nicht zu. | *Einfache Instanz* |  
| **Beispiele** | **Text-Editoren**, wie im Code-Editor<br /><br /> **Entwurfsoberflächen**wie ein Formular-Designer oder eine Fläche, die Modellierung<br /><br /> **Steuern des Layouts Dialoge ähnelt**, wie Sie den Manifest-Designer | Die **Projektmappen-Explorer** bietet eine Lösung und innerhalb der Projektmappe enthaltenen Projekte<br /><br /> Die **Server-Explorer** wird eine hierarchische Ansicht von Servern und Verbindungen, die der Benutzer entscheidet, in das Fenster zu öffnen. Öffnen ein Objekt aus der Datenbank, wie eine Abfrage wird ein Dokumentfenster geöffnet und ermöglicht dem Benutzer, die Abfrage zu bearbeiten.<br /><br /> Die **Eigenschaftenbrowser** zeigt die Eigenschaften für das Objekt entweder in einem Dokumentfenster oder anderen Toolfenster ausgewählt. Die Eigenschaften werden in einer hierarchischen Rasteransicht oder in komplexen Dialogfeld Like-Steuerelementen angezeigt und ermöglicht dem Benutzer die Werte für diese Eigenschaften festzulegen. | |  
  
##  <a name="BKMK_ToolWindows"></a> Toolfenster  
  
### <a name="overview"></a>Übersicht  
Toolfenster unterstützen des Benutzers arbeiten, die in den Dokumentfenstern geschieht. Sie können verwendet werden, um eine Hierarchie anzuzeigen, die eine grundlegende Stammobjekt darstellt, die Visual Studio bietet, und bearbeiten können.  
  
Wenn Sie ein neue Toolfenster in der IDE nachdenken, sollten Autoren:  
  
-   Verwenden Sie die Aufgabe geeignete vorhandene Toolfenster und neue Verträge mit ähnlicher Wirkungsweise nicht erstellt werden. Neue Toolfenster sollten erst erstellt werden, wenn sie bieten eine deutlich unterschiedliche "-Tool" oder Funktionen, die in einem ähnlichen Fenster oder aktivieren ein vorhandenes Fenster an ein tabellenpivotierung Hub kann nicht integriert werden.  
  
-   Verwenden Sie eine standard-Befehlsleiste, ggf. am oberen Rand des Toolfensters.  
  
-   Konsistent mit Mustern in andere Toolfenster Steuerelement Präsentations- und Tastatur Navigation bereits vorhanden sein.  
  
-   Mit der Control-Darstellung in andere Toolfenster konsistent sein.  
  
-   Stellen Sie dokumentspezifische Toolfenster automatisch sichtbar nach Möglichkeit, damit sie angezeigt werden, wenn das übergeordnete Dokument aktiviert ist.  
  
-   Stellen Sie sicher, dass ihre Inhalte Fenster über die Tastatur (Unterstützung Pfeiltasten) navigierbar ist.  
  
#### <a name="tool-window-states"></a>Status für Toolfenster  
Visual Studio-Toolfenster haben unterschiedliche Zustände, von die einige Benutzer (z. B. die Funktion automatisch im Hintergrund) aktiviert sind. Andere Zustände, wie z. B. automatisch sichtbar, ermöglichen Sie Toolfenster im richtigen Kontext angezeigt und auszublenden, wenn Sie nicht benötigt. Es gibt fünf Status für Toolfenster insgesamt.  
  
-   **In der Dockingstation/angeheftet** Toolfenster können an jeder der vier Seiten des Dokumentbereichs angehängt werden. Das Ortsmarkensymbol sieht in der Titelleiste des Toolfensters. Das Toolfenster kann horizontal oder vertikal angedockt werden, am Rand der Shell und andere Toolfenster, und Sie können auch Registerkarten verknüpft werden.  
  
-   **Automatisch ausgeblendete** Toolfenster gelöst werden. Das Fenster kann ausgeblendet, lassen eine Registerkarte (mit den Namen im Toolfenster und dessen Symbol ") am Rand des Dokumentbereichs schieben. Das Toolfenster wird Wenn ein Benutzer über die Registerkarte bewegt wird.  
  
-   **Automatisch sichtbar** Toolfenster automatisch angezeigt, wenn eine andere Teil der Benutzeroberfläche, z. B. einem Editor gestartet oder den Fokus erhält.  
  
-   **Gleitkommawert** Toolfenster außerhalb der IDE zeigen. Dies ist hilfreich für Konfigurationen mit mehreren Monitoren.  
  
-   **Dokumentfenster im Registerformat** Toolfenster können auch innerhalb des Dokuments angedockt werden. Dies ist hilfreich für große Toolfenster, z. B. Objektkatalog, die weitere Immobilien als Andocken an den Rändern des Frames zulässt.  
  
![In Visual Studio Zuständen des Toolfensters](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702 01_ToolWindowStates")<br />Status für Toolfenster in Visual Studio
  
#### <a name="single-instance-and-multi-instance"></a>Einzelinstanz- und mit mehreren Instanzen  
Toolfenster sind in einer Instanz oder mit mehreren Instanzen. Einige Einzelinstanz-Toolfenster ggf. das aktive Fenster, zugeordnet, während nicht möglicherweise Toolfenster mit mehreren Instanzen. Toolfenster mit mehreren Instanzen reagieren auf die **Fenster &gt; neues Fenster** Befehl durch Erstellen einer neuen Instanz des Fensters. Die folgende Abbildung zeigt ein Toolfenster, die den neuen Fenster-Befehl aktivieren, wenn eine Instanz des Fensters aktiv ist:  
  
![Das Toolfenster "Aktivieren der Befehl"Neues Fenster", wenn eine Instanz des Fensters ist aktiv](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702 02_ToolWindowEnablingCommand")<br />Toolfenster, die der Befehl "Neues Fenster" aktivieren, wenn eine Instanz des Fensters aktiv ist.  
  
Einzelinstanz-Toolfenster können ausgeblendet oder angezeigt werden, während mit mehreren Instanzen Toolfenster geschlossen ausgeblendet als auch können werden. Alle Toolfenster können angedockt, Registerkarte verknüpft, Gleitkomma oder als ein Multiple Document Interface (MDI) untergeordnetes Fenster (vergleichbar mit einem Dokumentfenster) festgelegt werden. Alle Toolfenster reagieren soll auf die entsprechenden Fenster Management-Befehle im Menü "Fenster":  
  
![Management-Befehle in der Visual Studio-Fenster im Menü "Fenster"](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702 03_WindowManagementControls")<br />Management-Befehle in der Visual Studio-Fenster im Menü "Fenster"
  
#### <a name="document-specific-tool-windows"></a>Dokumentspezifische Toolfenster  
Einige Toolfenster dienen als basierend auf einem angegebenen Typ des Dokuments ändern. Diese Fenster aktualisiert kontinuierlich und um Funktionalität, die für das aktive Fenster in der IDE zu entsprechen.  
  
Beispiele für Toolfenster, deren Inhalt entsprechend der ausgewählten Editor zu ändern, sind die Toolbox und die Dokumentgliederung an. Diese Fenster zeigen ein Wasserzeichen enthalten sein, wenn Sie ein Editor den Fokus besitzt, die kein Kontext zum Fenster bereitstellt.  
  
#### <a name="navigable-list-tool-windows"></a>Navigierbar Liste Toolfenster  
Einige Toolfenster zeigt eine Liste von navigierbaren Elementen, denen der Benutzer interagieren kann. Bei dieser Art von Fenster sollte es immer sein Feedback für das aktuelle Element in der Liste, auch wenn das Fenster nicht aktiv ist. Die Liste welche Reaktionen auf die **Gehe zu nächster Position** und **GoToPrevLocation** Befehle durch das aktuell ausgewählte Element in das Fenster auch ändern  
  
Beispiele für Toolfenster navigierbar Liste sind im Projektmappen-Explorer und das Fenster Suchergebnisse.  
  
### <a name="tool-window-types"></a>Fenstertypen Tool  
  
#### <a name="common-tool-windows-and-their-functions"></a>Allgemeine Toolfenster und ihre Funktionen

**Hierarchische Toolfenster**
| Toolfenster | Funktion | 
| --- | --- | 
| Projektmappen-Explorer | Eine hierarchische Struktur, die eine Liste der enthaltenen Dokumente in Projekten, sonstige Dateien und Projektmappenelemente anzeigt. Die Anzeige der Elemente innerhalb von Projekten wird durch das Paket definiert, die vom Projekttyp (z. B. verweisbasierten, Directory-basierte oder im gemischten Modus Typen) besitzt. | 
| Klassenansicht | Eine hierarchische Struktur der Klassen und verschiedenen Elementen in den Arbeitsseiten von Dokumenten, unabhängig von den Dateien selbst. | 
| Server-Explorer | Eine hierarchische Struktur, in dem alle Server und-datenverbindungen in der Projektmappe angezeigt. | 
| Dokumentgliederung | Die hierarchische Struktur des aktiven Dokuments. | 

**Raster-Toolfenster**
| Toolfenster | Funktion | 
| --- | --- | 
| Eigenschaften | Ein Raster, in dem eine Liste von Eigenschaften für das ausgewählte Objekt zusammen mit Wert Bildlaufbereich so bearbeiten Sie die Eigenschaften angezeigt. | 
| Aufgabenliste | Ein Raster mit den dem Benutzer, Erstellen/Bearbeiten/Löschen von Aufgaben und Kommentaren ermöglicht. | 

**Inhalt Toolfenster**
| Toolfenster | Funktion | 
| --- | --- | 
| Hilfe | Ein Fenster, das Benutzern Zugriff auf die verschiedenen Methoden zum Abrufen von Hilfe, von "Wie kann ich?" ermöglicht. Videos auf MSDN-Foren. | 
| Dynamische Hilfe | Ein Toolfenster mit Links zu Themen, die für die aktuelle Auswahl gelten können. | 
| Objektkatalog | Eine zweispaltige Frameset mit einer Liste von hierarchischen Objekt Komponenten im linken Bereich, und des Objekts Eigenschaften und Methoden in der rechten Spalte. | 

**Dialogfeld-Toolfenster**
| Toolfenster | Funktion | 
| --- | --- | 
| Find | Ein Dialogfeld, in dem der Benutzer zu suchen oder suchen und Ersetzen in verschiedene Dateien innerhalb der Projektmappe. |
| Erweiterte Suche | Ein Dialogfeld, in dem der Benutzer zu suchen oder suchen und Ersetzen in verschiedene Dateien innerhalb der Projektmappe. | 

**Andere Toolfenster**
| Toolfenster | Funktion | 
| --- | --- | 
| Werkzeugkasten | Das Toolfenster verwendet, um Elemente zu speichern, die auf der Entwurfsoberflächen Bereitstellen einer konsistenten Ziehquelle für alle Designer gelöscht werden. |
| Startseite | Der Benutzer im Portal zu Visual Studio mit Zugriff auf Datenfeeds von Informationen für Entwickler, Visual Studio-Hilfe und zuletzt geöffnete Projekte. Benutzer können auch benutzerdefinierte Startseiten erstellen, durch Kopieren der Datei "StartPage.xaml" aus der "Common7\IDE\StartPages\" Verzeichnis für Programmdateien in den Ordner StartPages in Visual Studio Visual Studio dokumentiert, Directory, und klicken Sie dann entweder Bearbeiten des XAML-Codes von Hand oder Sie sie in Visual Studio oder einem anderen Codeeditor öffnen. | 

**Debugger-Toolfenster**
| Toolfenster | Funktion | 
| --- | --- |
| Auto ||  
| Direkt ||  
| Ausgabe | Wenn Sie Text Ereignisse oder Status deklariert haben, kann das Fenster "Ausgabe" verwendet werden. |  
| Arbeitsspeicher ||  
| Haltepunkte ||  
| Running ||  
| Dokumente ||  
| Aufrufliste ||  
| Locals ||  
| Überwachungen ||  
| Disassemblierung ||  
| Register ||  
| Threads ||  
  
##  <a name="BKMK_DocumentEditorConventions"></a> Dokument-Editor-Konventionen  
  
### <a name="document-interactions"></a>Dokument-Interaktionen  
"Document gut" ist die größte Fläche in der IDE und, in denen der Benutzer in der Regel ihre Aufmerksamkeit liegt der Schwerpunkt um ihre Aufgaben von ergänzenden Toolfenster unterstützt werden. Dokument-Editoren stellen die grundlegenden Arbeitseinheiten, die der Benutzer öffnet und speichert in Visual Studio dar. Behalten sie eine hohe Auswahl mit Projektmappen-Explorer oder anderen Fenstern aktiven Hierarchie verknüpft sind. Der Benutzer sollte sein können, zeigen Sie auf eines der diese Hierarchie-Fenster, und wissen, wo das Dokument enthalten ist und seine Beziehung auf die Projektmappe, das Projekt oder einer anderen Stammobjekt, die von einem Visual Studio-Paket bereitgestellt.  
  
Dokument bearbeiten, ist eine konsistente benutzerumgebung erforderlich. Damit wird den Benutzer für den Task zur hand anstatt auf fensterverwaltung und suchen die Befehle zu konzentrieren, wählen Sie eine Dokument-Ansicht-Strategie, die am besten der Benutzeraufgaben für diesen Dokumenttyp bearbeiten.  
  
#### <a name="common-interactions-for-the-document-well"></a>Allgemeine Aktivitäten für Dokumentursprung  
  
-   Verwalten Sie eine konsistente Interaktionsmodell im allgemeinen **neue Datei** und **Dateiöffnungsmodus** auftritt.  
  
-   Aktualisieren Sie verwandten Funktionen in verwandten Fenstern und Menüs, wenn im Dokumentfenster geöffnet wird.  
  
-   Befehle im Menü werden entsprechend in allgemeine Menüs wie integriert **bearbeiten**, **Format**, und **Ansicht** Menüs. Wenn eine beträchtliche Menge an spezielle Befehle verfügbar sind, kann ein neues Menü erstellt werden. Diese neue Menü sollte angezeigt werden, nur, wenn das Dokument den Fokus hat.  
  
-   Eine eingebettete Symbolleiste kann am oberen Rand der Editor platziert werden. Dies ist vorzuziehen, sodass Sie eine separate Symbolleiste, die außerhalb des Editors wird angezeigt.  
  
-   Stets eine Auswahl im Projektmappen-Explorer oder ähnliche aktive Fenster "Aufrufhierarchie".  
  
-   Durch Doppelklicken auf ein Dokument im Projektmappen-Explorer sollten dieselbe Aktion wie ausführen **öffnen**.  
  
-   Wenn mehr als einer der Redakteure auf einen Dokumenttyp verwendet werden kann, sollte der Benutzer kann außer Kraft gesetzt oder zurückgesetzt die Standardaktion für ein bestimmtes Dokument mit werden die **Öffnen mit** (Dialogfeld), indem Sie mit der rechten Maustaste auf die Datei und auswählen **öffnen Mit** aus dem Kontextmenü.  
  
-   Erstellen Sie einen Assistenten in einem Dokument nicht gut.  
  
### <a name="user-expectations-for-specific-document-types"></a>Erwartungen der Benutzer für bestimmte Dokumenttypen  
Es gibt verschiedene grundlegende Typen von Dokument-Editoren, und jede verfügt über einen Satz von Aktivitäten, die konsistent mit anderen desselben Typs sind.  
  
-   **Textbasierten Editor:** Codeeditor, Protokolldateien  
  
-   **Entwurfsoberfläche:** WPF-Forms-Designer, Windows Forms  
  
-   **Dialogfeld-Stil-Editor:** Manifest-Designer-Projekteigenschaften  
  
-   **Modell-Designer:** Workflow-Designer, Codemap, Architekturdiagramm, Progression  
  
Es gibt auch mehrere nicht-Editor-Typen, die das Dokument verwenden. Während sie Dokumente selbst nicht bearbeiten, müssen sie Standardinteraktionen für Dokumentfenster folgen.  
  
-   **Berichte:** IntelliTrace zu melden, Hyper-V-Bericht Profiler-Berichtsansicht  
  
-   **Dashboard:** Diagnose-Hub  
  
#### <a name="text-based-editors"></a>Textbasierte-Editoren  
  
-   Das Dokument ist Teil der Vorschau Registerkartenmodell, mit dem für die Vorschau des Dokuments, ohne es zu öffnen.  
  
-   Die Struktur des Dokuments kann innerhalb eines Toolfensters Companion z. B. eine dokumentgliederung dargestellt werden.  
  
-   IntelliSense (falls zutreffend) verhält sich konsistent mit anderen Codeeditoren.  
  
-   Popups oder unterstützende UI führen Sie ähnliche Formate und Muster für vorhandene ähnlichen Benutzeroberfläche, z. B. CodeLens ein.  
  
-   Meldungen zu Dokumentstatus werden in einem Infoleiste-Steuerelement am oberen Rand des Dokuments oder in der Statusleiste angezeigt.  
  
-   Der Benutzer muss in der Lage, Anpassen der Darstellung von Schriftarten und Farben, die mit einem **Tools > Optionen** Seite der freigegebenen Seite für Schriftarten und Farben oder einen bestimmten auf den Editor.  
  
#### <a name="design-surfaces"></a>Entwurfsoberflächen  
  
-   Ein leerer Designer sollte ein Wasserzeichen auf der Oberfläche, der angibt, zu den ersten Schritten erhalten haben.  
  
-   Ansicht wechseln Mechanismen führen Sie die vorhandenen Muster wie Doppelklicken Sie in einem Code-Editor oder Registerkarten im Dokumentfenster ermöglicht die Interaktion mit beider Bereiche zu öffnen.  
  
-   Hinzufügen von Elementen, die der Entwurfsoberfläche sollte über die Toolbox durchgeführt werden, es sei denn, ein sehr spezifischen Toolfenster erforderlich ist.  
  
-   Elemente auf der Entwurfsoberfläche werden ein Auswahlmodell konsistent folgen.  
  
-   Eingebettete Symbolleisten enthalten dokumentspezifische Befehle nur, die nicht häufig Befehle wie z. B. **speichern**.  
  
#### <a name="dialog-style-editors"></a>Dialogfeld-Stil-Editoren  
  
-   Das Steuerelementlayout sollten normalen Dialogfensters Layoutkonventionen folgen.  
  
-   Registerkarten innerhalb des Editors sollte nicht die Darstellung der Registerkarten "Dokument" entsprechen, sollten sie einen der beiden zulässigen inneren Registerkarte Stile übereinstimmen.  
  
-   Benutzer müssen mit den Steuerelementen, die über Tastatur interagieren können; entweder den Editor aktivieren und Tabulator-über Steuerelemente oder standard Tastenkürzel verwenden.  
  
-   Mithilfe des Designers sollte den allgemeinen Modell speichern. Keine allgemeinen speichern "oder" Commit-Schaltflächen sollten auf der Oberfläche platziert werden, auch andere Schaltflächen angemessen sein können.  
  
#### <a name="model-designers"></a>Modell-Designer  
  
-   Ein leerer Designer sollte ein Wasserzeichen auf der Oberfläche, der angibt, zu den ersten Schritten erhalten haben.  
  
-   Hinzufügen von Elementen, die der Entwurfsoberfläche sollte über die Toolbox erfolgen.  
  
-   Elemente auf der Entwurfsoberfläche werden ein Auswahlmodell konsistent folgen.  
  
-   Eingebettete Symbolleisten enthalten dokumentspezifische Befehle nur, die nicht häufig Befehle wie z. B. **speichern**.  
  
-   Auf der Oberfläche Hinweisende oder ein Wasserzeichen möglicherweise eine Legende angezeigt.  
  
-   Der Benutzer muss in der Lage, die Darstellung der mithilfe von Schriftarten/Farben anpassen, eine **Tools > Optionen** Seite der freigegebenen Seite für Schriftarten und Farben oder einen bestimmten auf den Editor.  
  
#### <a name="reports"></a>Berichte  
  
-   Berichte werden in der Regel Informationen nur und nicht Teil des Modells speichern. Sie enthalten jedoch möglicherweise Interaktion wie beispielsweise Links zu anderen relevanten Informationen oder die Abschnitte, die erweitert und reduziert werden.  
  
-   Die meisten Befehle auf der Oberfläche sollte Hyperlinks, die keine Schaltflächen.  
  
-   Layout sollten enthalten einen Header, und befolgen Sie die Standardbericht Layout-Richtlinien.  
  
#### <a name="dashboards"></a>Dashboards  
  
-   Dashboards müssen ein Interaktionsmodell selbst allerdings dienen dazu, eine Vielzahl von anderen Tools zu bieten.  
  
-   Sie das Modell speichern nicht teilnehmen.  
  
-   Benutzer müssen mit den Steuerelementen, die über Tastatur, entweder durch Aktivieren des Editors und mit der Tabulatortaste Steuerelemente oder mithilfe von standard Mnemonik interagieren können.  
  
##  <a name="BKMK_Dialogs"></a> Dialogfelder  
  
### <a name="introduction"></a>Einführung  
Dialogfelder in Visual Studio unterstützen sollte in der Regel eine einzelne Arbeitseinheit des Benutzers und anschließend verworfen werden.  
  
Wenn sich herausgestellt hat, dass Sie ein Dialogfeld benötigen, haben Sie drei Möglichkeiten zur Verfügung, in bevorzugter Reihenfolge:  
  
1.  Integrieren Sie die Funktionen in eine freigegebene Dialogfelder in Visual Studio.  
  
2.  Erstellen Sie eigene Dialogfeld unter Verwendung eines Musters in einem vorhandenen ähnliche Dialogfeld gefunden.  
  
3.  Erstellen Sie ein neuer Dialog, folgende Interaktion und Layoutrichtlinien.  
  
Dieser Abschnitt beschreibt, wie Sie das richtige Dialogfeld Muster in Visual Studio-Workflows und die allgemeinen Konventionen für das Dialogfeld Design auswählen.  
  
### <a name="themes"></a>Designs  
Dialogfelder in Visual Studio führen Sie einen der zwei grundlegende Formate:  
  
#### <a name="standard-unthemed"></a>Standard (Unthemed)  
Die meisten Dialogfelder werden standard-Dienstprogramm-Dialogfelder und Unthemed sein. Verwenden Sie nicht Re-Vorlage für allgemeine Steuerelemente oder zum Erstellen von gestalteten "modernen" Schaltflächen oder Steuerelementen. Steuerelemente und führen Sie Chrome-Darstellung [Windows Desktop Interaktion Standardrichtlinien für die Dialogfelder](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx).  
  
#### <a name="themed"></a>Designs  
Specialty "Signatur" Dialoge möglicherweise Designs. Designs Dialoge haben eine eigene Darstellung, die auch einige spezielle interaktionsmustern, die den Stil zugeordnet hat. Design Ihrer Dialogfeld nur, wenn sie die folgenden Anforderungen erfüllt:  
  
-   Das Dialogfeld "ist eine allgemeine Erfahrung, die angezeigt und häufig oder von mehreren Benutzern verwendet werden (z. B. die **neues Projekt** Dialogfeld.  
  
-   Das Dialogfeld enthält deutliche Brand Produktelemente (z. B. die **Kontoeinstellungen** Dialogfeld).  
  
-   Das Dialogfeld wird angezeigt, als ein wesentlicher Bestandteil einer größeren fließrichtung, der andere Designs Dialoge enthält (z. B. die **verbundenen Dienst hinzufügen** Dialogfeld).  
  
-   Das Dialogfeld "ist ein wichtiger Teil eine Erfahrung, die in Höherstufen oder Unterscheidung einer Produktversion eine strategische Rolle spielt.  
  
Beim Erstellen eines Designs Dialogfelds verwenden Sie die entsprechende Umgebungsfarben, und befolgen Sie die richtige Layout und Nachrichteninteraktionsmustern zusammensetzen. (Siehe [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)  
  
### <a name="dialog-design"></a>Dialogfeld-Entwurf  
Sorgfältig entworfene Dialoge berücksichtigen Sie die folgenden Elemente:  
  
-   Die Benutzeraufgabe, die unterstützt werden  
  
-   Das Dialogfeld Textart, Sprache und Terminologie  
  
-   Auswahl des Steuerelements und UI-Konventionen  
  
-   Das visuelle Layout-Spezifikation und Steuerung Ausrichtung  
  
-   Tastaturzugriff  
  
#### <a name="content-organization"></a>Organisation von Inhalten  
Betrachten Sie die Unterschiede zwischen diesen grundlegenden Typen von Dialogfeldern:  
  
-   [Einfache Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) Steuerelemente in einem einzelnen modale Fenster darstellen. Die Präsentation kann Variationen des komplexen Steuerelementmuster, z. B. einer Feldauswahl oder eine Symbolleiste enthalten.  
  
-   [Dialogfelder in den Ebenen](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) werden verwendet, um die optimale Nutzung von Bildschirmfläche zu stellen, wenn ein einzelnes Stück UI mehrere Gruppen von Steuerelementen umfasst. Im Dialogfeld Gruppierungen sind "über Registerkarten-Steuerelemente, Steuerelemente für die Seitennavigation oder Schaltflächen in den Ebenen", damit der Benutzer die Gruppierung auf einem bestimmten Moment sehen kann.  
  
-   [Assistenten](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) eignen sich für das Umleiten von des Benutzers über eine logische Sequenz von Schritten, die auf den Abschluss einer Aufgabe. In sequenziellen Bereiche, in einigen Fällen Einführung in anderen Workflows ("Verzweigung") eine Auswahl in der vorherigen Seite abhängig sind eine Reihe von Optionen angeboten.  
  
####  <a name="BKMK_SimpleDialogs"></a> Einfache Dialogfelder  
Ein einfaches Dialogfeld ist eine Präsentation von Steuerelementen in einem einzelnen modale Fenster. In dieser Präsentation kann Variationen des komplexen Steuerelementmuster, z. B. einer Feldauswahl enthalten. Führen Sie für einfache Dialoge das Standardlayout allgemeine als auch bestimmten Layout für komplexe Steuerelement Gruppierungen erforderlich sind.
  
![> erstellen Schlüssel mit starkem Namen wird ein Beispiel für ein einfaches Dialogfeld in Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704 Artikelnr 01_CreateStrongNameKey")<br />Erstellen Schlüssel mit starkem Namen wird ein Beispiel für ein einfaches Dialogfeld in Visual Studio.
  
####  <a name="BKMK_LayeredDialogs"></a> Mehrschicht-Dialogfelder  
Überlappende Dialoge enthalten Registerkarten, Dashboards und eingebettete Strukturen. Sie werden verwendet, um die Immobilien zu maximieren, wenn es mehrere Gruppen von Steuerelementen, die in ein einzelnes Stück UI angeboten werden. Die Gruppierungen sind überlagernd, damit der Benutzer die Gruppierung auf einem beliebigen Zeitpunkt sehen kann.  
  
Im einfachsten Fall ist der Mechanismus für den Wechsel zwischen Gruppierungen ein Registerkarten-Steuerelement. Stehen verschiedene Alternativen zur Verfügung. Festlegen der Priorität und Ebenen für das am besten geeignete Format auswählen angezeigt.  
  
Die **Tools &gt; Optionen** Dialog ist ein Beispiel für ein Dialogfeld mit Ebenen mit einer eingebetteten Struktur:  
  
![Extras > Optionen ist ein Beispiel für ein Dialogfeld mit Ebenen in Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704 Artikelnr 02_ToolsOptions")<br />Extras > Optionen ist ein Beispiel für ein Dialogfeld mit Ebenen in Visual Studio.
  
####  <a name="BKMK_Wizards"></a> Assistenten  
Assistenten eignen sich für das Umleiten von des Benutzers über eine logische Sequenz von Schritten bei der Durchführung einer Aufgabe. Eine Reihe von Optionen werden in sequenziellen Bereiche angeboten, und der Benutzer muss bei jedem Schritt vor dem Fortfahren auf die nächste folgen. Sobald genügend Standardwerte verfügbar sind, werden die **Fertig stellen** Schaltfläche ist aktiviert.  
  
 Modale-Assistenten für Aufgaben verwendet werden, die:  
  
-   Enthalten Sie Verzweigungen, wobei unterschiedliche Pfade je nach Benutzerauswahl angeboten werden  
  
-   Enthalten Sie Abhängigkeiten zwischen den Schritten, die in nachfolgende Schritten auf Benutzereingaben aus der vorherigen Auftragsschritte abhängen  
  
-   Sind ausreichend komplex, dass die Benutzeroberfläche verwendet werden soll, um die Installationsoptionen sowie die möglichen Ergebnisse in jedem Schritt wird erläutert  
  
-   Sind transaktional, erfordern eine Reihe von Schritten in seiner Gesamtheit abgeschlossen werden, bevor ein Commit für Änderungen ausgeführt wird  
  
### <a name="common-conventions"></a>Allgemeine Konventionen  
Um eine optimale Entwurf und-Funktionen mit der Dialogfelder zu erreichen, folgen Sie diesen Konventionen Größe des Dialogfelds, Position, Standards, Steuerelementkonfiguration und Ausrichtung, Benutzeroberfläche Text, Titelleisten, Schaltflächen und Zugriffstasten.  
  
Layout-spezifische Richtlinien finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Größe  
Dialoge sollte in einer mindestauflösung von 1024 x 768 Bildschirm passen, und Größe des ersten Dialogfelds darf 900 x 700 Pixel nicht überschreiten. Dialoge können in der Größe veränderbar sein, aber es ist keine Voraussetzung.  
  
Es gibt zwei Empfehlungen für die in der Größe veränderbaren Dialogfelder:  
  
1.  Eine Mindestgröße für den Dialog definiert ist, die für das Steuerelement zu optimieren, wird ohne Clipping festlegen und anpassen, um sinnvolle Lokalisierung Wachstum.  
  
2.  Dass die Benutzer skaliert Größe Sitzung erhalten bleibt. Z. B. wenn der Benutzer ein Dialogfeld zu 150 % skaliert werden, werden dann einer nachfolgenden Start des Dialogs 150 % angezeigt.  
  
#### <a name="position"></a>Position  
Dialoge müssen in der IDE beim ersten Start zentriert angezeigt werden. Die letzte Position von Dialogen nicht veränderbare Größen muss nicht beibehalten werden, damit sie auf nachfolgende Aufrufe zentriert angezeigt werden. 

Für in der Größe veränderbaren Dialoge sollte die Größe auf nachfolgende Aufrufe beibehalten werden. Für modale Dialogfelder geändert werden kann muss die Position nicht beibehalten werden. Anzeigen in der IDE zentriert wird verhindert, dass das Dialogfeld "in einen unvorhersehbaren oder unbrauchbar Position angezeigt wird, wenn Anzeigekonfiguration des Benutzers geändert wurde. 

Für nicht modale Dialogfelder, die neu angeordnet werden können, sollten Position des Benutzers auf nachfolgende gestartet wird, verwaltet werden, wie das Dialogfeld häufig als wesentlicher Bestandteil eines größeren Workflows verwendet werden kann.  
  
Bei Dialogen andere Dialogfelder erzeugen müssen, sollte das oberste Dialogfeld kaskadiert werden rechts und nach unten aus dem übergeordneten Element so, dass die It für den Benutzer ersichtlich, an die Stelle der Sie navigiert haben.  
  
#### <a name="modality"></a>Modalität  
Modal wird bedeutet, dass Benutzer aufgefordert werden, abgeschlossen oder das Dialogfeld abbrechen, bevor Sie fortfahren. Da modale Dialogfelder den Benutzer von der Interaktion mit anderen Teilen der Umgebung zu sperren, sollten Sie durch Ihre Funktion Aufgabenverlauf so selten wie möglich verwenden werden. Wenn ein modaler Vorgang erforderlich ist, hat Visual Studio eine Anzahl der freigegebenen Dialoge, denen Sie Features in integrieren können. Wenn Sie ein neues Dialogfeld erstellen müssen, führen Sie die das Interaktionsmuster einen vorhandenen Dialog mit ähnlicher Wirkungsweise.  
  
Wenn der Benutzer zwei Aktivitäten gleichzeitig ausführen müssen, wie z. B. **suchen** und **ersetzen** beim Schreiben von neuem Code aus, das Dialogfeld muss nicht modalen, damit Benutzer problemlos zwischen ihnen wechseln kann. Visual Studio verwendet die Toolfenster in der Regel für diese Art von verknüpften Task-Editor-Unterstützung.  
  
#### <a name="control-configuration"></a>Konfiguration des cachesteuerelements  
Mit vorhandenen steuerelementkonfigurationen, die in Visual Studio dasselbe Ziel erreichen konsistent sein.  
  
#### <a name="title-bars"></a>Titelleisten  
  
-   Der Text in der Titelleiste muss den Namen des Befehls widerspiegeln, die es gestartet.  
  
-   Symbol "keine" sollte im Dialogfeld Titelleisten verwendet werden. Verwenden Sie in Fällen, in denen das System eine erfordert das Visual Studio-Logo.  
  
-   Dialoge sollten keine minimieren oder maximieren Schaltflächen.  
  
-   Hilfe-Schaltflächen in der Titelleiste sind veraltet. Fügen Sie sie nicht Sie neue Dialogfelder. Wenn sie vorhanden sind, sollten sie ein Hilfethema starten, die grundsätzlich relevant für die Aufgabe ist.  
  
 ![Spezifikationen der Richtlinie für Titelleisten in Visual Studio-Dialogfeldern](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704 Artikelnr 03_TitleBarSpecs")<br />Spezifikationen der Richtlinie für Titelleisten in Visual Studio-Dialogfelder
  
#### <a name="control-buttons"></a>Steuerelementschaltflächen  
Im allgemeinen **OK**, **"Abbrechen"**, und **Hilfe** Schaltflächen in der unteren rechten Ecke des Dialogfelds horizontal angeordnet werden soll. Der alternative vertikale Stapel ist zulässig, wenn ein Dialogfeld mehrere andere Schaltflächen im unteren Bereich des Dialogfelds verfügt, die visual Verwechslungen mit den Steuerelementschaltflächen darstellen würde.  
  
![Akzeptable Konfigurationen für Steuerelementschaltflächen in Visual Studio-Dialogfeldern](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704 Artikelnr 04_ControlButtonConfig")<br />Akzeptable Konfigurationen für Steuerelementschaltflächen in Visual Studio-Dialogfelder
  
Das Dialogfeld "muss eine Standardschaltfläche für das Steuerelement enthalten. Um zu bestimmen, den bewährte Befehl als Standard verwenden, wählen Sie aus den folgenden Optionen (entsprechend der Rangfolge aufgelistet):  
  
-   Wählen Sie den sichersten und sicherste-Befehl als Standard. Dies bedeutet, dass des Vermeidung von Datenverlusten und verhindern von unbeabsichtigten Systemzugriff am wahrscheinlichsten-Befehls.  
  
-   Wenn Datenverlust und Sicherheit nicht Faktoren sind, wählen Sie dann den Standardbefehl basierend auf halber an. Einschließlich des wahrscheinlichsten Befehls als Standard wird durch den Workflow des Benutzers, wenn das Dialogfeld "häufige oder sich wiederholende Aufgaben unterstützt verbessert.  
  
Vermeiden Sie die Auswahl einer dauerhaft destruktiven Aktion für den Standardbefehl. Wenn ein Befehl vorhanden ist, wählen Sie einen sichereren Befehl als Standard stattdessen.  
  
#### <a name="access-keys"></a>Zugriffstasten  
Verwenden Sie keine Zugriffstasten für **OK**, **"Abbrechen"**, oder **Hilfe** Schaltflächen. Standardmäßig werden diese Schaltflächen Tastenkombinationen zugeordnet:  
  
| Schaltflächenname | Tastenkombination |  
| --- | --- |  
| OK | EINGABETASTE |  
| Abbrechen | Esc |  
| Hilfe | F1 |  
  
#### <a name="imagery"></a>Bilder  
Verwenden Sie Bilder sparsam in Dialogfeldern. Verwenden Sie keine große Symbole in Dialogfeldern lediglich zum Speicherplatz zu verwenden. Verwenden Sie Bilder aus, nur dann, wenn sie ein wichtiger Bestandteil die Nachricht an den Benutzer wie Warnsymbole oder Status Animationen vermittelt werden.  
  
###  <a name="BKMK_PrioritizingAndLayering"></a> Priorisieren und Ebenen  
  
#### <a name="prioritizing-your-ui"></a>Priorisieren die Benutzeroberfläche  
Es möglicherweise erforderlich, weisen Sie bestimmte Elemente der Benutzeroberfläche der Forefront und platzieren Sie erweiterte Verhalten und die Optionen (einschließlich kryptische Befehle) in Dialogfeldern. Plazieren Sie häufig verwendete Funktionen der Forefront durch Platz dafür vornehmen und es sichtbar gemacht wird standardmäßig in der Benutzeroberfläche mit einer textbezeichnung Wenn das Dialogfeld angezeigt wird.  
  
#### <a name="layering-your-ui"></a>Überlagern die Benutzeroberfläche  
Wenn sich herausgestellt hat, dass ein Dialog erforderlich ist, aber hinausgeht, dass die zugehörige Funktionalität, die Sie für dem Benutzer bereitstellen möchten wie in einem einfachen Dialogfeld angezeigt werden können, müssen Sie Ihre Benutzeroberfläche Ebene. Am häufigsten verwendeten Strukturlayout-Methoden, die Visual Studio verwendet werden Registerkarten und Fluren oder Dashboards an. In einigen Fällen möglicherweise entsprechenden Bereiche, die erweitert und reduziert werden können. Adaptive Benutzeroberfläche ist in Visual Studio im Allgemeinen nicht empfohlen.  
  
Es gibt vor- und Nachteile der verschiedenen Methoden überlagern Benutzeroberfläche über die Registerkarte "-Like-Steuerelemente. Überprüfen Sie die Liste unten, um sicherzustellen, dass Sie eine Technik Ebenen auswählen, die für Ihre Situation geeignet ist.  
  
##### <a name="tabbing"></a>Wechseln mit der Tabulatortaste  
  
| Mechanismus wechseln | Vorteile und die richtige Verwendung | Nachteile und nicht ordnungsgemäße Verwendung |  
| --- | --- | --- |  
| Registersteuerelement | Dialogfelder in Verwandte Gruppen logisch zu gruppieren<br /><br />Für weniger als fünf (oder die Anzahl der Registerkarten, die in einer Zeile entsprechen, über das Dialogfeld ") hilfreich Seiten von verwandten Steuerelementen im Dialogfeld"<br /><br />Registerkartenbezeichnungen müssen kurz sein: ein oder zwei Wörter, die schnell den Inhalt<br /><br />Eine allgemeine System Dialogfeld Stil<br /><br />Beispiel: **-Datei-Explorer &gt; Elementeigenschaften** | Beschreibende kurze Bezeichnungen vornehmen kann schwierig sein<br /><br />In der Regel Skalierung keine nach fünf Registerkarten in einem Dialogfeld<br /><br />Ungeeignete haben zu viele Registerkarten für eine Zeile (verwenden Sie eine alternative Strukturlayout Technik)<br /><br />Nicht erweiterbare |  
| Seitenleistennavigation | Einfache switching Gerät, das weitere Kategorien als Registerkarten aufnehmen kann<br /><br />Flache Liste der Kategorien (ohne Hierarchie)<br /><br />Erweiterbare<br /><br />Beispiel: **anpassen... &gt; Hinzufügen (Befehl)** | Nicht für eine gute Verwendung für horizontalen Bereich, wenn weniger als drei Gruppen vorhanden sind<br /><br />Task möglicherweise besser geeignet, um eine Dropdownliste |  
| Struktursteuerelement | Ermöglicht unbegrenzte Kategorien<br /><br />Ermöglicht die Gruppierung und/oder die Hierarchie der Kategorien<br /><br />Erweiterbare<br /><br />Beispiel: **Tools &gt; Optionen** | Stark geschachtelte Hierarchien, so kann eine übermäßige horizontalen Bildlauf<br /><br />Visual Studio verfügt über eine Overabundance von Strukturansichten |  
| Assistent | Unterstützt Sie bei Abschluss der Aufgabe von spaltenänderungsattributen des Benutzers über aufgabenbasierte, aufeinander folgende Schritte aus: der Assistent stellt eine übergeordnete Aufgabe und die einzelnen Bereiche darstellen, Unteraufgaben erforderlich, um die gesamte Aufgabe<br /><br />Ist nützlich, wenn die Aufgabe über Ui, mehrere als wenn der Benutzer andernfalls müssten verwenden Sie mehrere Editoren und Toolfenstern zum Abschließen der Aufgabe<br /><br />Ist nützlich, wenn der Task Verzweigung erfordert<br /><br />Ist nützlich, wenn die Aufgabe Abhängigkeiten zwischen den Schritten enthält<br /><br />Ist nützlich, wenn mehrere ähnliche Aufgaben mit einer Entscheidung Verzweigung in einem Dialogfeld zum Reduzieren der Anzahl der verschiedenen ähnliche Dialogfelder angezeigt werden kann | Ungeeignet für jede Aufgabe, die einen sequenziellen Workflow keine erforderlich<br /><br />Benutzer können überschwemmt und von einem Assistenten mit zu viele Schritte verwechselt werden.<br /><br />Assistenten haben grundsätzlich Bildschirmfläche beschränkt. |  
  
##### <a name="hallways-or-dashboards"></a>Fluren oder dashboards  
Fluren und Dashboards sind Dialogfelder oder Bereiche, die als starten verweist auf den anderen Dialogfeldern und Fenstern dienen. Sorgfältig entworfene "Gang" Flächen sofort nur die am häufigsten verwendeten Optionen, Befehle und Einstellungen, sodass der Benutzer leicht allgemeiner Aufgaben. Wie eine reale Gang Doorways für den Zugriff auf die Räume nutzen bietet, gesammelt hier die Benutzeroberfläche weniger häufig in separaten "Räume" (häufig mit anderen Dialogfeldern) Verwandte Funktionen, die von der wichtigsten Gang zugegriffen werden kann.  
  
Alternativ können Sie eine Benutzeroberfläche, die alle verfügbaren Funktionen in einer einzelnen Auflistung bietet, anstatt die weniger übliche-Funktionalität in voneinander entfernten Standorten aus Umgestaltung einfach ein Dashboard ist.  
  
![Hallway-Konzept zum Verfügbarmachen von weitere Benutzeroberfläche in Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704 Artikelnr 08_Hallway")<br />Hallway-Konzept zum Verfügbarmachen von weitere Benutzeroberfläche in Outlook
  
##### <a name="adaptive-ui"></a>Adaptive UI  
Ein- oder Ausblenden der Benutzeroberfläche basierend auf Nutzung oder eine Self-gemeldeten benutzererfahrung ist eine weitere Möglichkeit zur Darstellung der benötigten Benutzeroberfläche und gleichzeitig andere Teile von. Dies wird in Visual Studio, nicht empfohlen, die Algorithmen für die Entscheidung, wann ein- oder Ausblenden der Benutzeroberfläche können kompliziert sein, und die Regeln werden immer in der falschen für einige Satz von Fällen.  
  
##  <a name="BKMK_Projects"></a> Projekte  
  
### <a name="projects-in-the-solution-explorer"></a>Projekte im Projektmappen-Explorer  
Die meisten Projekte werden als verweisbasierten, Directory-basierte oder gemischten klassifiziert. Alle drei Typen von Projekten werden im Projektmappen-Explorer gleichzeitig unterstützt. Der Stamm der benutzererfahrung bei der Arbeit mit Projekten findet in diesem Fenster an. Obwohl verschiedene Projektknoten Verweis, Verzeichnis oder im gemischten Modus Typ Projekte sind, besteht ein allgemeines Interaktionsmuster, das als Ausgangspunkt angewendet werden soll, bevor in Mustern für projektspezifische Benutzer gehen auseinander.  
  
Es sollte immer Projekte:  
  
-   Unterstützen Sie die Möglichkeit zum Hinzufügen von Projektordner zum Organisieren von Inhalt von Projekten  
  
-   Beibehalten eines konsistenten Modells zum projektdauerhaftigkeit  
  
Projekte sollten auch konsistent interaktionsmodelle für verwalten:  
  
-   Entfernen von Projektelementen  
  
-   Speichern von Dokumenten  
  
-   Projekt Eigenschaft bearbeiten  
  
-   Bearbeiten das Projekt in eine alternative Ansicht  
  
-   Drag & Drop-Vorgänge  
  
### <a name="drag-and-drop-interaction-model"></a>Drag & Drop-Interaktionsmodell  
Projekte klassifizieren selbst als verweisbasierten (nur Verweise auf Projektelemente im Speicher beibehalten werden können), in der Regel Directory-basierte (können nur Projektelemente physisch persistent gespeichert innerhalb der Hierarchie eines Projekts), oder gemischt (können Verweise beibehalten werden. oder physischen Elemente). Die IDE hat alle drei Typen von Projekten gleichzeitig innerhalb der **Projektmappen-Explorer**.  
  
Aus Sicht der Drag & Drop die folgenden Merkmale treffen sollten, für jeden Typ von Projekt innerhalb der **Projektmappen-Explorer**:  
  
-   **Referenz-basiertes Projekt:** wichtig ist, dass das Projekt um einen Verweis auf ein Element im Speicher gezogen wird. Wenn Sie ein Referenz-basiertes Projekt als Quelle für einen Verschiebevorgang fungiert, sollte es nur den Verweis auf das Element aus dem Projekt entfernen. Das Element sollten nicht tatsächlich von der Festplatte gelöscht werden. Wenn Sie ein Referenz-basiertes Projekt als Ziel für einen Vorgang verschieben (oder kopieren) fungiert, sollten sie einen Verweis auf die ursprüngliche Quellelement hinzufügen, ohne dass eine private Kopie des Elements.  
  
-   **Directory-basiertes Projekt:** aus Sicht des einen Drag-and-Drop wird das Projekt ziehen, um physischen Elements statt einen Verweis. Wenn ein Verzeichnis-basiertes Projekt als Quelle für einen Verschiebevorgang fungiert, sollte es am Ende löschen die physischen Elements von der Festplatte als auch aus dem Projekt entfernen. Wenn ein Verzeichnis-basiertes Projekt als Ziel für einen Vorgang verschieben (oder kopieren) fungiert, sollte eine Kopie des Quellelements in seiner Zielspeicherort erleichtern.  
  
-   **Gemischte Zielprojekt:** aus einer Drag & Drop-Sicht, das Verhalten dieser Art von Projekt ist aufgrund der Natur des Elements gezogen wird, entweder (einen Verweis auf ein Element im Speicher) oder das Element selbst. Das richtige Verhalten für Verweise und physischen Elemente werden oben beschrieben.  
  
Wenn gab es nur eine Art des Projekts in der **Projektmappen-Explorer**, Drag & Drop-Vorgänge einfach sein würde. Da jede Projektsystem die Möglichkeit, eigene Drag-and-Drop-Verhalten definiert hat, sollten bestimmte Richtlinien (basierend auf dem Windows-Explorer Drag-and-Drop-Verhalten) befolgt werden, um eine vorhersagbare benutzererfahrung zu gewährleisten:  
  
-   Eine unveränderte Vorgang ziehen, der **Projektmappen-Explorer** (Wenn weder STRG und UMSCHALTTASTE gedrückt gehalten werden) sollten in einem Verschiebevorgang führen.  
  
-   UMSCHALT-Ziehvorgang sollte auch ein Verschiebevorgang ergeben.  
  
-   STRG-Ziehvorgang sollten dazu führen, dass ein Vorgang zum Kopieren.  
  
-   Verweisbasierten und gemischten Projektsystemen unterstützen das Konzept der Hinzufügen einer Verknüpfung (oder Verweis) auf das Quellelement. Wenn diese Projekte sind das Ziel eines Drag-and-Drop-Vorgangs (Wenn **STRG + UMSCHALT** gedrückt gehalten wird), sie sollten dazu führen, einen Verweis auf das Element zum Projekt hinzugefügt wird  
  
Nicht alle Drag-and-Drop-Vorgänge sind für Kombinationen von Verweis, Verzeichnis und gemischten Projekte aussagefähiger. Insbesondere ist es schwierig, die vorgeben, einem Verschiebevorgang zwischen einem Directory basierende Quellprojekt und verweisbasierten Zielprojekt zu ermöglichen, da das Quellprojekt Directory basierende das Quellelement nach Abschluss des Verschiebens gelöscht hat. Das Zielprojekt verweisbasierten würde dann mit einem Verweis auf ein gelöschtes Element annehmen.  
  
Es ist ebenfalls irreführend, die vorgeben, ein Kopiervorgangs zwischen diesen Typen von Projekten zu ermöglichen, da das Zielprojekt verweisbasierten keine unabhängige Kopie des Quellelements herstellen soll. Auf ähnliche Weise sollten STRG + UMSCHALT ziehen, um ein Verzeichnis basierende Zielprojekt nicht zulässig, weil ein Verzeichnis-basiertes Projekt Verweise beibehalten werden kann. In Fällen, in denen die Drag-and-Drop-Vorgang nicht unterstützt wird, sollte die IDE unterbinden, die Dropdownliste und anzeigen dem Benutzer nicht ablegen-Cursor (im Zeiger in der folgenden Tabelle gezeigt).  
  
Um Drag & Drop-Verhalten ordnungsgemäß zu implementieren, muss das Quellprojekt des Ziehvorgangs sind ihrem Wesen in das Zielprojekt kommunizieren können. (Beispielsweise ist es Verweis oder Directory-basierte?) Diese Informationen wird durch das Zwischenablageformat angegeben, die von der Quelle bereitgestellt werden. Als Quelle eines Drag & (oder Kopieren der Zwischenablagevorgang) sollte ein Projekt bieten entweder `CF_VSREFPROJECTITEMS` oder `CF_VSSTGPROJECTITEMS` , je nachdem, ob das Projekt Verweis oder Directory-basierten. Beide Formate haben den gleichen Dateninhalt, also ähnelt der Windows `CF_HDROP` formatieren mit dem Unterschied, dass Listen von Zeichenfolgen, anstatt Sie Dateinamen, Double - sind`NULL` beendet Sie die Liste der `Projref` Zeichenfolgen (wie vom zurückgegeben`IVsSolution::GetProjrefOfItem`oder `::GetProjrefOfProject` je nach Bedarf).  
  
Als Ziel einer Drop (oder Einfügevorgangs Zwischenablage), sollte ein Projekt akzeptieren sowohl `CF_VSREFPROJECTITEMS` und `CF_VSSTGPROJECTITEMS`, obwohl die genaue Behandlung des Drag & Drop-Vorgangs je nach Art des Projekts Ziel und das Quellprojekt variiert. Das Quellprojekt deklariert sind ihrem Wesen nach, ob er bietet `CF_VSREFPROJECTITEMS` oder `CF_VSSTGPROJECTITEMS`. Das Ziel der Dropdownliste einen eigenen Art versteht und daher verfügt über genügend Informationen, um im Vergleich zu Entscheidungen zu treffen, ob ein verschieben, kopieren oder Link ausgeführt werden soll. Der Benutzer werden auch geändert, welche Drag & Drop-Vorgang durch Drücken der STRG, UMSCHALTTASTE oder sowohl STRG und Umschalttaste ausgeführt werden soll. Es ist wichtig für das Ablageziel um ordnungsgemäß anzugeben, welcher Vorgang im Voraus darüber erfolgen soll die `DragEnter` und `DragOver` Methoden. Die **Projektmappen-Explorer** automatisch weiß, ob das Quellprojekt und das Zielprojekt desselben Projekts sind.  
  
Projektelemente über Instanzen von Visual Studio (z. B. von einer Instanz von devenv.exe zu einem anderen) ziehen wird ausdrücklich nicht unterstützt. Die **Projektmappen-Explorer** auch direkt wird deaktiviert.  
  
Der Benutzer sollte immer sein können, um zu bestimmen, die Auswirkungen eines Drag-and-Drop-Vorgangs durch Auswählen eines Elements, ziehen es an den Zielspeicherort und beobachten, welche der folgenden Mauszeiger angezeigt wird, bevor das Element gelöscht wird:  
  
| Mauszeiger | Befehl | Beschreibung |  
| :---: | --- | --- |  
| ![Symbol "keine Ablage" für Maus](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706 01_MouseNoDrop") | Keine Ablage | Element kann nicht am angegebenen Speicherort abgelegt werden. |  
| ![Symbol "Maus"Kopieren""](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706 02_MouseCopy") | Kopieren | Element wird an den Zielspeicherort kopiert werden. |  
| ![Maus "Symbol"verschieben""](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706 03_MouseMove") | Verschieben | Elemente werden an den Zielspeicherort verschoben werden. |  
| ![Symbol für "Verweis hinzufügen" Maus](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706 04_MouseAddRef") | Verweis hinzufügen | Ein Verweis auf das ausgewählte Element wird an den Zielspeicherort hinzugefügt werden. |

#### <a name="reference-based-projects"></a>verweisbasierten Projekten  
 In der folgenden Tabelle werden die Drag & Drop (sowie Ausschneiden/Kopieren/Einfügen) Vorgänge, die ausgeführt werden, sollten basierend auf der Art des Elements und der Modifizierer Quellschlüssel gedrückt für Ziel verwiesen-basierte Projekte zusammengefasst:  
  
| Modifizierer | Kategorie | Das Quellelement: Referenzlink / | Das Quellelement: physischen Element bzw. die Datei-Systems (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Kein Modifizierer | Aktion | Verschieben | Link |  
| Kein Modifizierer | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Verweis auf das ursprüngliche Element hinzugefügt |  
| Kein Modifizierer | Quelle | Löscht Verweis zum ursprünglichen Element | Behält die ursprünglichen Element |  
| Kein Modifizierer | Ergebnis | `DROPEFFECT_MOVE` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_LINK` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |  
| Umschalt + Ziehen | Aktion | Verschieben | Keine Ablage |  
| Umschalt + Ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Keine Ablage |  
| Umschalt + Ziehen | Quelle | Löscht Verweis zum ursprünglichen Element | Keine Ablage |  
| Umschalt + Ziehen | Ergebnis | `DROPEFFECT_MOVE` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | Keine Ablage |  
| STRG + Ziehen | Aktion | Kopieren | Keine Ablage |  
| STRG + Ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Keine Ablage |  
| STRG + Ziehen | Quelle | Verweis auf das ursprüngliche Element behält | Keine Ablage |  
| STRG + Ziehen | Ergebnis | `DROPEFFECT_COPY` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | Keine Ablage |  
| STRG + UMSCHALT + ziehen | Aktion | Link | Link |  
| STRG + UMSCHALT + ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Verweis auf das ursprüngliche Element hinzugefügt |  
| STRG + UMSCHALT + ziehen | Quelle | Verweis auf das ursprüngliche Element behält | Behält die ursprünglichen Element |  
| STRG + UMSCHALT + ziehen | Ergebnis | `DROPEFFECT_LINK` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_LINK` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |  
| STRG + UMSCHALT + ziehen | Hinweis | Identisch mit Drag & Drop-Verhalten für Verknüpfungen im Windows-Explorer. ||  
| Ausschneiden und einfügen | Aktion | Verschieben | Link |  
| Ausschneiden und einfügen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Verweis auf das ursprüngliche Element hinzugefügt |  
| Ausschneiden und einfügen | Quelle | Verweis auf das ursprüngliche Element behält|Behält die ursprünglichen Element |  
| Ausschneiden und einfügen | Ergebnis | Element bleibt im ursprünglichen Speicherort im Speicher | Element bleibt im ursprünglichen Speicherort im Speicher |  
| Kopieren und einfügen | Aktion | Kopieren | Link |  
| Kopieren und einfügen | Quelle | Verweis auf das ursprüngliche Element hinzugefügt | Verweis auf das ursprüngliche Element hinzugefügt |  
| Kopieren und einfügen | Ergebnis | Verweis auf das ursprüngliche Element behält | Behält die ursprünglichen Element |  
| Kopieren und einfügen | Aktion | Element bleibt im ursprünglichen Speicherort im Speicher | Element bleibt im ursprünglichen Speicherort im Speicher |  
  
#### <a name="directory-based-projects"></a>Directory-basierte Projekte  
In der folgenden Tabelle werden die Drag & Drop (sowie Ausschneiden/Kopieren/Einfügen) Vorgänge, die ausgeführt werden, sollten basierend auf der Art des Elements und der Modifizierer Quellschlüssel gedrückt für Target Directory-basierte Projekte zusammengefasst:  
  
| Modifizierer | Kategorie | Das Quellelement: Referenzlink / | Das Quellelement: physischen Element bzw. die Datei-Systems (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Kein Modifizierer | Aktion | Verschieben | Verschieben |  
| Kein Modifizierer | Ziel | Kopien Element aus, um den Zielspeicherort an | Kopien Element aus, um den Zielspeicherort an |  
| Kein Modifizierer | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Verweis zum ursprünglichen Element | | Kein Modifizierer | Ergebnis | `DROPEFFECT_MOVE` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_MOVE` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |  
| Umschalt + Ziehen | Aktion | Verschieben | Verschieben |  
| Umschalt + Ziehen | Ziel | Kopien Element aus, um den Zielspeicherort an | Kopien Element aus, um den Zielspeicherort an |  
| Umschalt + Ziehen | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Element aus der ursprünglichen Speicherort |
| Umschalt + Ziehen | Ergebnis | `DROPEFFECT_MOVE` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_MOVE` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |  
| STRG + Ziehen | Aktion | Kopieren | Kopieren |  
| STRG + Ziehen | Ziel | Kopien Element aus, um den Zielspeicherort an | Kopien Element aus, um den Zielspeicherort an |  
| STRG + Ziehen | Quelle | Verweis auf das ursprüngliche Element behält | Verweis auf das ursprüngliche Element behält |  
| STRG + Ziehen | Ergebnis | `DROPEFFECT_COPY` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_COPY` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |  
| STRG + UMSCHALT + ziehen | | Keine Ablage | Keine Ablage |  
| Ausschneiden und einfügen | Aktion | Verschieben | Verschieben |  
| Ausschneiden und einfügen | Ziel | Kopien Element aus, um den Zielspeicherort an | Kopien Element aus, um den Zielspeicherort an |  
| Ausschneiden und einfügen | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Element aus der ursprünglichen Speicherort |  
| Ausschneiden und einfügen | Ergebnis | Element bleibt im ursprünglichen Speicherort im Speicher | Element ist vom ursprünglichen Speicherort gelöscht. |  
| Kopieren und einfügen | Aktion | Kopieren | Kopieren |  
| Kopieren und einfügen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Kopien Element aus, um den Zielspeicherort an |  
| Kopieren und einfügen | Quelle | Behält die ursprünglichen Element | Behält die ursprünglichen Element |  
| Kopieren und einfügen | Ergebnis | Element bleibt im ursprünglichen Speicherort im Speicher | Stehende Element bleibt im ursprünglichen Speicherort ins Speicher |
  
#### <a name="mixed-target-projects"></a>Gemischte Ziel-Projekte  
Die folgende Tabelle fasst die Drag & Drop (sowie Ausschneiden/Kopieren/Einfügen) Vorgänge, die ausgeführt werden, sollten basierend auf der Art des Elements und der Modifizierer Quellschlüssel für gemischte Ziel Projekte gedrückt:  
  
| Modifizierer | Kategorie | Das Quellelement: Referenzlink / | Das Quellelement: physischen Element bzw. die Datei-Systems (`CF_HDROP`) |  
| --- | --- | --- | --- |
| Kein Modifizierer | Aktion | Verschieben | Verschieben |
| Kein Modifizierer | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Kopien Element aus, um den Zielspeicherort an |
| Kein Modifizierer | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Verweis zum ursprünglichen Element |
| Kein Modifizierer | Ergebnis | `DROPEFFECT_ MOVE` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_ MOVE` wird als Aktion zurückgegeben `::Drop` und Element aus der ursprünglichen Speicherort im Speicher gelöscht wird |
| Umschalt + Ziehen | Aktion | Verschieben | Verschieben |
| Umschalt + Ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Kopien Element aus, um den Zielspeicherort an |
| Umschalt + Ziehen | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Element aus der ursprünglichen Speicherort | 
| Umschalt + Ziehen | Ergebnis | `DROPEFFECT_ MOVE` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_ MOVE` wird als Aktion zurückgegeben `::Drop` und Element aus der ursprünglichen Speicherort im Speicher gelöscht wird |
| STRG + Ziehen | Aktion | Kopieren | Kopieren |
| STRG + Ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Kopien Element aus, um den Zielspeicherort an |
| STRG + Ziehen | Quelle | Verweis auf das ursprüngliche Element behält | Behält die ursprünglichen Element |
| STRG + Ziehen | Ergebnis | `DROPEFFECT_ COPY` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_ COPY` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |
| STRG + UMSCHALT + ziehen | Aktion | Link | Link |
| STRG + UMSCHALT + ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Fügt der Verweis auf die ursprüngliche Quellelement |
| STRG + UMSCHALT + ziehen | Quelle | Verweis auf das ursprüngliche Element behält | Behält die ursprünglichen Element |
| STRG + UMSCHALT + ziehen | Ergebnis | `DROPEFFECT_ LINK` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_ LINK` wird als Aktion zurückgegeben `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |
| Ausschneiden und einfügen | Aktion | Verschieben | Verschieben |
| Ausschneiden und einfügen | Ziel | Kopien Element aus, um den Zielspeicherort an | Kopien Element aus, um den Zielspeicherort an |
| Ausschneiden und einfügen | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Element aus der ursprünglichen Speicherort |
| Ausschneiden und einfügen | Ergebnis | Element bleibt im ursprünglichen Speicherort im Speicher | Element ist vom ursprünglichen Speicherort gelöscht. |
| Kopieren und einfügen | Aktion | Kopieren | Kopieren |
| Kopieren und einfügen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Kopien Element aus, um den Zielspeicherort an |
| Kopieren und einfügen | Quelle | Behält die ursprünglichen Element | Behält die ursprünglichen Element |
| Kopieren und einfügen | Ergebnis | Element bleibt im ursprünglichen Speicherort im Speicher | Element bleibt im ursprünglichen Speicherort im Speicher |
  
Diese Informationen sollten berücksichtigt werden bei der Implementierung, ziehen der **Projektmappen-Explorer**:  
  
-   Entwurf für Szenarien mit mehreren Auswahl.  
  
-   Dateinamen (vollständiger Pfad) müssen für das Zielprojekt eindeutig sein, oder die Drop darf nicht.  
  
-   Ordnernamen müssen eindeutig sein (Groß-/Kleinschreibung) auf der Ebene, die sie gelöscht wird.  
  
-   Es gibt Unterschiede im Verhalten zwischen Dateien, die zum Zeitpunkt der (nicht in Szenarien, die oben erwähnt) ziehen offen oder geschlossen werden.  
  
-   Dateien der obersten Ebene Verhalten geringfügig anders, als Dateien in Ordnern.  
  
Ein anderes Problem zu berücksichtigen ist, wie Verschiebevorgänge für Elemente behandelt, die open-Designer oder Editoren verfügen. Das erwartete Verhalten ist wie folgt (Dies gilt für alle Projekttypen verfügbar):  
  
1.  Wenn der Editor/Designer Öffnen keine nicht gespeicherten Änderungen verfügt, sollte das Editor-Designer-Fenster im Hintergrund geschlossen werden.  
  
2.  Wenn der Editor/Designer öffnen gehen nicht gespeicherte Änderungen verfügt, soll klicken Sie dann die Quelle des Ziehvorgangs warten im Dropdownmenü auftreten, und fordern Sie die Benutzer, die offenen Dokumente vor dem Schließen des Fensters mit der eine Meldung ähnlich der folgenden nicht gespeicherte Änderungen speichern :  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
Dies gewährt dem Benutzer die Möglichkeit, Ihre Arbeit zu speichern, bevor das Ziel auf seine Datenbankkopien macht. Eine neue Methode `IVsHierarchyDropDataSource2::OnBeforeDropNotify` wurde hinzugefügt, um diese Behandlung zu aktivieren.  
  
Das Ziel kopiert klicken Sie dann den Status des Elements, wie es im Speicher ist (einschließlich nicht nicht gespeicherten Änderungen im Editor ein, wenn der Benutzer **keine**). Nachdem das Ziel der Kopiervorgang abgeschlossen wurde (in `IVsHierarchyDropDataSource::Drop`), die Quelle erhält die Möglichkeit, den Löschvorgang Teil der Verschiebevorgang abgeschlossen (im `IVsHierarchyDropDataSource::OnDropNotify`).  
  
Alle Editoren mit nicht gespeicherten Änderungen sollten geöffnet bleiben. Für diese Dokumente mit nicht gespeicherten Änderungen bedeutet dies, dass der kopieren-Teil der Verschiebevorgang erfolgt, aber der Delete-Teil wird abgebrochen. In einem Szenario mit mehreren Auswahl, wenn der Benutzer wählt **keine**, diese Dokumente mit nicht gespeicherten Änderungen nicht geschlossen oder entfernt, jedoch ohne gehen nicht gespeicherte Änderungen geschlossen und entfernt werden soll.