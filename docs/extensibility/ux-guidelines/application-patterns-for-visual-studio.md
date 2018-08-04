---
title: Anwendungsmuster für Visual Studio | Microsoft-Dokumentation
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
ms.openlocfilehash: 0bd7ad3434f854a66ce3cd966afbaf25c089efc8
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513386"
---
# <a name="application-patterns-for-visual-studio"></a>Anwendungsmuster für Visual Studio
##  <a name="BKMK_WindowInteractions"></a> Fenster-Interaktionen  
  
### <a name="overview"></a>Übersicht  
Die beiden im Hauptfenster-Typen, die in Visual Studio verwendet werden, Dokument-Editoren und Toolfenster. Seltene, aber möglich ist, sind große nicht modale Dialogfelder. Obwohl es sich alle in der Shell nicht modale handelt, sind ihre Muster grundlegend. Dieser Abschnitt enthält die Differenz zwischen Dokumentfenster und Toolfenster nicht modale Dialogfelder. Modales Dialogfeld Muster finden Sie im [Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Vergleichen die Fenster von Verwendungsmustern  
**Dokumentfenster** werden fast immer angezeigt, in das Dokument gut. Dadurch wird dem Dokument-Editor eine "center Phase" zusätzliche Toolfenster um anordnen.  
  
Ein **Toolfenster** wird meist als separate, kleinere Fenster reduziert, die für den Rand der IDE angezeigt. Dies kann sichtbar, ausgeblendet oder automatisch ausgeblendete sein. Allerdings manchmal Toolfenster werden angezeigt in das Dokument nun, durch Deaktivieren der **Fensterandocken/** Eigenschaft im Fenster. Dies führt zu mehr Platz, aber auch eine allgemeine entwurfsentscheidung: beim Versuch, die in Visual Studio zu integrieren, müssen Sie entscheiden, ob das Feature ein Toolfenster oder ein Dokumentfenster angezeigt wird.  
  
**Nicht modale Dialogfelder** wird davon abgeraten, in Visual Studio. Die meisten nicht modale Dialogfelder sind, per definitionem Gleitkomma-Toolfenster und sollte auf diese Weise implementiert werden. Nicht modale Dialogfelder dürfen sich in Fällen, in dem die Größe von einem normalen Toolfenster angedockt wird, auf die Seite der Shell zu eingeschränkt erweisen wird. Sie dürfen auch in Fällen, in denen der Benutzer wahrscheinlich um das Dialogfeld zu einem sekundären Monitor verschieben wäre.  
  
Stellen Sie sich, zu dem Container müssen Sie sorgfältig durch. Allgemeine Nutzung Muster-Überlegungen zum Entwurf der Benutzeroberfläche werden in der folgenden Tabelle.  
  
||Dokumentfenster|Toolfenster|Nicht-modales Dialogfeld|  
|-|---------------------|-----------------|---------------------|  
| **Position** | Immer auch innerhalb des Dokuments positioniert und ist nicht an den Rändern der IDE andocken. Sie können "abgerufen werden, deaktiviert", damit es separat von der main-Shell gleitet. | In der Regel als Registerkarte rund um die Ränder der IDE angedockt jedoch können benutzerdefinierte zu schweben, werden automatisch ausgeblendete (unpinned) oder auch innerhalb des Dokuments angedockt.|Große unverankertes Fenster getrennt von der IDE. |  
| **Commit-Modell** | *Verzögertes commit*<br /><br /> Um die Daten in einem Dokument speichern möchten, muss der Benutzer ausgeben der **Datei &gt; speichern**, **speichern**, oder **Alles speichern** Befehl. Ein Dokumentfenster wurde das Konzept der Daten darin wird "verschmutzte", klicken Sie dann ein Commit ausgeführt, auf einen der speichern Befehle. Wenn Sie ein Dokumentfenster schließen, werden alle Inhalte entweder auf dem Datenträger gespeichert oder verloren geht. | *Sofortige commit*<br /><br /> Es gibt keine speichern Modell. Für Inspector-Toolfenster, die bei der Bearbeitung von Dateien, die Datei muss im aktiven Editor oder Designer geöffnet sein, und Editor oder Designer besitzt den Speichervorgang. | *Verzögerte oder sofortige commit*<br /><br /> In den meisten Fällen ein großes nicht-modales Dialogfeld erfordert eine Aktion, die Änderungen zu übernehmen und kann für einen Vorgang "Abbrechen", der alle Änderungen innerhalb der Dialogfeld-Sitzung ein Rollback ausgeführt.  Dies unterscheidet es sich um ein nicht modales Dialogfeld aus einem Toolfenster, Toolfenster immer eine sofortige Commit-Modell enthalten. |  
| **Sichtbarkeit** | *(Datei) öffnen oder erstellen und schließen*<br /><br /> Öffnen ein Dokumentfenster erfolgt entweder über ein vorhandenes Dokument öffnen oder mithilfe einer Vorlage zum Erstellen eines neuen Dokuments. Es gibt keine "Open \<bestimmten Editor >" Befehl. | *Anzeigen und ausblenden*<br /><br /> Einzelinstanz-Toolfenster können ausgeblendet oder angezeigt wird. Inhalt und Status innerhalb des Toolfensters beizubehalten, ob in der Ansicht oder ausgeblendet. Mehrfachinstanz-Toolfenster können geschlossen ausgeblendet als auch sein. Wenn ein Mehrfachinstanz-Toolfenster geschlossen wird, wird Inhalt und Status innerhalb des Toolfensters verworfen. | *Von einem Befehl gestartet*<br /><br /> Dialogfelder werden über eine aufgabenbasierte gestartet. |  
| **Instanzen** | *Mit mehreren Instanzen*<br /><br /> Einige Editoren können zur gleichen Zeit und verschiedene Dateien bearbeiten, geöffnet sein können, während einige Editoren auch die gleiche Datei in mehrere Editoren geöffnet sein können (mithilfe der **Fenster &gt; neues Fenster** Befehl).<br /><br /> Ein einzigen Editor möglicherweise eine oder mehrere Dateien gleichzeitig (Projekt-Designer) bearbeiten. | *Einzelnen oder mehreren Instanzen*<br /><br /> Inhalt ändern, um widerzuspiegeln Kontext (wie in den Eigenschaften-Browser) oder mithilfe von Push übertragen Fokus/Kontext zu anderen Fenstern (Aufgabenliste, Projektmappen-Explorer).<br /><br /> Sowohl mit mehreren Instanzen als auch Einzelinstanz-Toolfenster sollte mit das aktive Fenster verknüpft sein, es sei denn, es ist ein guter Grund nicht zu. | *Einzel-Instanz* |  
| **Beispiele** | **Text-Editoren**, wie Sie den Code-Editor<br /><br /> **Entwurfsoberflächen**, z. B. einen Formular-Designer oder eine Oberfläche für die Modellierung<br /><br /> **Steuern des Layouts für Dialogfelder ähnlich**, wie Sie den Manifest-Designer | Die **Projektmappen-Explorer** bietet eine Lösung und innerhalb der Projektmappe enthaltenen Projekte<br /><br /> Die **Server-Explorer** wird eine hierarchische Ansicht von Servern und -Verbindungen, die der Benutzer entscheidet, in das Fenster zu öffnen. Öffnen ein Objekt aus der Datenbankhierarchie, wie eine Abfrage, einem Dokumentfenster geöffnet und ermöglicht dem Benutzer, die Abfrage zu bearbeiten.<br /><br /> Die **Eigenschaftenbrowser** werden Eigenschaften für das Objekt ausgewählt, entweder in einem Dokumentfenster oder ein anderes Toolfenster angezeigt. Die Eigenschaften werden angezeigt, entweder in einer hierarchischen Rasteransicht oder komplexen-ähnliches Dialogfeld-Steuerelemente und ermöglicht dem Benutzer, die Werte für diese Eigenschaften festzulegen. | |  
  
##  <a name="BKMK_ToolWindows"></a> Toolfenster  
  
### <a name="overview"></a>Übersicht  
Toolfenster unterstützen die Arbeit des Benutzers, das im Dokumentfenster ausgeführt wird. Sie können verwendet werden, um eine Hierarchie anzuzeigen, die eine grundlegende Stammobjekt darstellt, die Visual Studio bereitstellt, und bearbeiten können.  
  
Wenn ein neues Toolfenster in der IDE in Betracht ziehen, sollten Autoren:  
  
-   Vorhandene Toolfenster Aufgabe geeignete verwenden und keine neuen erstellen mit ähnlichen Funktionen. Neue Toolfenster sollte nur erstellt werden, wenn sie bieten ein deutlich abweichende "Tool" oder eine Funktionalität, die in ein ähnliches Fenster, oder indem Sie ein vorhandenes Fenster in einem tabellenpivotierung Hub umwandeln kann nicht integriert werden.  
  
-   Verwenden Sie eine standardmäßige Befehlsleiste aus, wenn erforderlich, am oberen Rand des Toolfensters.  
  
-   Mit Mustern, die bereits in anderen Toolfenstern für die Steuerelement-Präsentation und Tastatur Navigation konsistent sein.  
  
-   Steuerelement-Präsentation in andere Toolfenster konsistent sein.  
  
-   Stellen Sie dokumentspezifische Toolfenster automatisch sichtbar Wenn möglich, sodass diese angezeigt werden, wenn nur das übergeordnete Dokument aktiviert ist.  
  
-   Stellen Sie sicher, dass ihre Inhalte Fenster über die Tastatur (Support-unten-Tasten) navigierbar ist.  
  
#### <a name="tool-window-states"></a>Status für Toolfenster  
Visual Studio-Toolfenster müssen die verschiedenen Zustände, von die einige Benutzer (z. B. das Feature für Automatisches Ausblenden) aktiviert sind. Andere Zustände, wie automatisch sichtbar, können Sie Toolfenster im richtigen Kontext angezeigt werden soll und auszublenden, wenn Sie nicht benötigt. Es gibt fünf Status für Toolfenster insgesamt.  
  
-   **Angedockt/angeheftet** Toolfenster können an jeder der vier Seiten des Dokumentbereichs angefügt werden. Das Pushpin-Symbol wird in der Titelleiste des Toolfensters angezeigt werden. Das Toolfenster kann horizontal oder vertikal angedockt werden, am Rand der Shell und andere Toolfenster, und Sie können auch Registerkarten verknüpft werden.  
  
-   **Automatisch ausgeblendete** Toolfenster werden gelöst. Ziehen Sie das Fenster wieder eingeblendet, wenn eine Registerkarte (mit dem Namen des Toolfensters und das entsprechende Symbol) am Rand des Dokumentbereichs. Das Toolfenster wird eingeblendet, wenn ein Benutzer über die Registerkarte bewegt wird.  
  
-   **Automatisch sichtbar** Toolfenster automatisch angezeigt, wenn ein weiterer Teil der Benutzeroberfläche, z. B. einem Editor gestartet wird oder den Fokus erhält.  
  
-   **Unverankerte** Toolfenstern bewegen Sie den Mauszeiger außerhalb der IDE. Dies ist nützlich für Konfigurationen mit mehreren Bildschirmen.  
  
-   **Dokument im Registerkartenformat** Toolfenster können auch innerhalb des Dokuments angedockt werden. Dies ist nützlich für große Toolfenster, z. B. den Objektkatalog, die mehr Platz als an die Ränder des Rahmens Andocken kann.  
  
![In Visual Studio Zuständen des Toolfensters](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Status für Toolfenster in Visual Studio
  
#### <a name="single-instance-and-multi-instance"></a>Einzelinstanzen und Mehrinstanzen  
Toolfenster sind Einzel-Instanz oder mit mehreren Instanzen. Einige Einzelinstanz-Toolfenster können das aktive Dokumentfenster, zugeordnet werden, während Mehrfachinstanz-Toolfenster nicht können. Mehrfachinstanz-Toolfenster zu reagieren, um die **Fenster &gt; neues Fenster** Befehl erstellen eine neue Instanz des Fensters. Die folgende Abbildung zeigt ein Toolfenster, die den neuen Fenster-Befehl aktivieren, wenn eine Instanz des Fensters aktiv ist:  
  
![Aktivierungsbefehle für Toolfenster "Neues Fenster" Befehl, wenn eine Instanz des Fensters ist aktiv](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Fenster "Neues Fenster" Befehl aktivieren, wenn eine Instanz des Fensters aktiv ist.  
  
Einzelinstanz-Toolfenster können ausgeblendet oder angezeigt werden, während das Mehrfachinstanz-Toolfenster geschlossen und ausgeblendet als werden können. Alle Toolfenster können angedockt, Registerkarten verknüpft, Gleitkomma oder als untergeordnetes Multiple Document Interface (MDI) Fenster (ähnlich wie ein Dokumentfenster) festgelegt werden. Alle Toolfenster sollte auf die entsprechenden Fenster Management-Befehle im Menü Fenster reagieren:  
  
![Verwaltungsbefehle für Fenster in Visual Studio im Menü](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Verwaltungsbefehle für Fenster in Visual Studio im Menü
  
#### <a name="document-specific-tool-windows"></a>Für die spezifischen Toolfenster  
Einige Toolfenster sollen basierend auf einem angegebenen Typ des Dokuments ändern. Diese Windows update-Funktionalität, die für das aktive Fenster in der IDE entsprechend ständig.  
  
Beispiele für Toolfenster, deren Inhalt entsprechend der ausgewählten Editor zu ändern, sind die Toolbox und der Dokumentgliederung. Diese Fenster zeigen ein Wasserzeichen auf, wenn ein Editor den Fokus besitzt, die keine Kontext zum Fenster bietet.  
  
#### <a name="navigable-list-tool-windows"></a>Navigierbare Liste-Toolfenster  
Einige Toolfenster zeigt eine Liste von navigierbaren Elementen, die, denen der Benutzer interagieren kann. In dieser Art von Fenster wird sollte immer vorhanden sein Feedback für das aktuelle Element in der Liste, auch wenn das Fenster aktiv ist. Die Liste sollte reagieren, um die **Gehe zu nächster Position** und **GoToPrevLocation** Befehle ändern auch das aktuell ausgewählte Element im Fenster  
  
Beispiele für Toolfenster navigierbare Liste werden im Projektmappen-Explorer und das Fenster Suchergebnisse.  
  
### <a name="tool-window-types"></a>Tool-Fenstertypen  
  
#### <a name="common-tool-windows-and-their-functions"></a>Allgemeinen Toolfenster und ihre Funktionen

**Hierarchische Toolfenster**
| Toolfenster | Funktion | 
| --- | --- | 
| Projektmappen-Explorer | Eine hierarchische Struktur, die eine Liste der darin enthaltenen Dokumente in Projekten, verschiedene Dateien und Projektmappenelemente anzeigt. Die Anzeige der Elemente innerhalb von Projekten wird durch das Paket definiert, die den Projekttyp (z. B. anhand von verweisen, Directory-basierte oder gemischte Typen) besitzt. | 
| Klassenansicht | Eine hierarchische Struktur der Klassen und verschiedene Elemente in den Arbeitsseiten von Dokumenten, unabhängig von der die Dateien selbst. | 
| Server-Explorer | Eine hierarchische Struktur, in dem alle Verbindungen für den Server und Daten in der Projektmappe angezeigt. | 
| Dokumentgliederung | Die hierarchische Struktur des aktiven Dokuments. | 

**Raster-Toolfenster**
| Toolfenster | Funktion | 
| --- | --- | 
| Eigenschaften | Ein Raster, das eine Liste der Eigenschaften für das ausgewählte Objekt, zusammen mit Wert dateiöffnungs-so bearbeiten Sie diese Eigenschaften werden angezeigt. | 
| Aufgabenliste | Ein Raster, das dem Benutzer, zu erstellen, bearbeiten und Löschen von Aufgaben und Kommentare ermöglicht. | 

**Inhalte von Toolfenstern**
| Toolfenster | Funktion | 
| --- | --- | 
| Hilfe | Ein Fenster, die Benutzern den Zugriff auf die verschiedenen Methoden zum Abrufen von Hilfeinformationen, über die "Gewusst?" ermöglicht. Videos zu MSDN-Foren. | 
| Dynamische Hilfe | Ein Toolfenster, in dem Links zu Themen, die für die aktuelle Auswahl Hilfe angezeigt. | 
| Objektkatalog | Frameset zwei Spalten mit einer Liste von hierarchisches Objekt Komponenten im linken Bereich, und des Objekts Eigenschaften und Methoden in der rechten Spalte. | 

**Dialogfeld-Toolfenster**
| Toolfenster | Funktion | 
| --- | --- | 
| Find | Ein Dialogfeld, mit dem Benutzer suchen oder suchen und Ersetzen Sie in verschiedenen Dateien innerhalb der Projektmappe. |
| Erweiterte Suche | Ein Dialogfeld, mit dem Benutzer suchen oder suchen und Ersetzen Sie in verschiedenen Dateien innerhalb der Projektmappe. | 

**Andere Toolfenster**
| Toolfenster | Funktion | 
| --- | --- | 
| Werkzeugkasten | Das Toolfenster verwendet, um Elemente zu speichern, die auf Entwurfsoberflächen, eine konsistente Ziehquelle bereitstellen, für alle Designer gelöscht werden. |
| Startseite | Portal für Visual Studio mit Zugriff auf Feeds von Neuigkeiten für Entwickler, Visual Studio-Hilfe und zuletzt geöffnete Projekte des Benutzers. Benutzer können auch benutzerdefinierte Startseiten erstellen, durch Kopieren der Datei "StartPage.xaml" aus der "Common7\IDE\StartPages\" Verzeichnis für die Dateien von Visual Studio-Programm, des Ordners StartPages in Visual Studio Verzeichnis, und klicken Sie dann entweder Bearbeiten der XAML-Dokumente indem Sie manuell oder durch Sie sie in Visual Studio oder einem anderen Codeeditor öffnen. | 

**Debugger-Tool-Fenster**
| Toolfenster | Funktion | 
| --- | --- |
| Auto ||  
| Direkt ||  
| Ausgabe | Das Fenster "Ausgabe" kann verwendet werden, wenn Sie Text Ereignisse oder Status deklariert haben. |  
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
Die "document gut" ist der größte Bereich in der IDE und ist, in denen der Benutzer in der Regel ihre Aufmerksamkeit liegt der Schwerpunkt für die Durchführung ihrer Aufgaben, die von ergänzenden Toolfenster unterstützt. Dokument-Editoren stellen die grundlegenden Arbeitseinheiten, die der Benutzer öffnet und speichert in Visual Studio dar. Behalten sie eine starke Objektidentität Auswahl mit Projektmappen-Explorer oder in anderen Fenstern für die aktive Hierarchie verknüpft. Der Benutzer sollte sein können, zeigen Sie auf einen dieser Hierarchie-Fenster, und wissen, wo das Dokument enthalten ist und dessen Beziehung zu einem der Projektmappe das Projekt oder einem anderen Stammobjekt, die von einem Visual Studio-Paket bereitgestellt.  
  
Dokumentbearbeitung erfordert eine konsistente benutzererfahrung. Damit wird den Benutzer auf die aktuelle Aufgabe nicht auf die fensterverwaltung und das Suchen von Befehlen zu konzentrieren, wählen Sie eine Strategie der Dokument-anzeigen, die am besten der Benutzeraufgaben für diesen Dokumenttyp bearbeiten.  
  
#### <a name="common-interactions-for-the-document-well"></a>Allgemeine Aktivitäten, die für das Dokument gut  
  
-   Verwalten einer konsistenten Interaktionsmodell in der allgemeinen **neue Datei** und **geöffnete Datei** auftritt.  
  
-   Aktualisieren Sie verwandten Funktionen im zugehörigen Fenster und Menüs, wenn das Dokumentfenster geöffnet wird.  
  
-   Befehle im Menü werden entsprechend integriert allgemeine Menüs wie **bearbeiten**, **Format**, und **Ansicht** Menüs. Wenn eine beträchtliche Menge an spezielle Befehle verfügbar sind, kann ein neues Menü erstellt werden. Dieses neue Menü sollte angezeigt werden, nur, wenn das Dokument den Fokus besitzt.  
  
-   Eine eingebettete Symbolleiste kann am oberen Rand der Editor platziert werden. Dies empfiehlt sich, dass eine separate Symbolleiste, die außerhalb des Editors angezeigt wird.  
  
-   Immer eine Auswahl im Projektmappen-Explorer oder ähnliche aktiv verwalten Fenster "Aufrufhierarchie".  
  
-   Durch Doppelklicken auf ein Dokument im Projektmappen-Explorer sollten dieselbe Aktion wie ausführen **öffnen**.  
  
-   Wenn Sie mehrere Editoren auf einem Dokument verwendet werden kann, muss der Benutzer außer Kraft setzen oder Zurücksetzen der Standardaktion für ein bestimmtes Dokument mit werden die **Öffnen mit** im Dialogfeld, indem Sie mit der rechten Maustaste auf die Datei und auswählen **öffnen Mit** aus dem Kontextmenü.  
  
-   Erstellen Sie einen Assistenten in einem Dokument nicht gut.  
  
### <a name="user-expectations-for-specific-document-types"></a>Die Erwartungen der Benutzer für bestimmte Dokumenttypen  
Es gibt mehrere unterschiedliche Basistypen von Dokument-Editor, und jede hat eine Reihe von Interaktionen, die für andere Benutzer des gleichen Typs konsistent sind.  
  
-   **Textbasierten Editor:** Code-Editor, Protokolldateien  
  
-   **Entwurfsoberfläche:** WPF Forms Designer, Windows Forms  
  
-   **Dialogfeld-Stil-Editor:** Manifest-Designer-Projekteigenschaften  
  
-   **Modell-Designer:** Workflow-Designer, Codemap, Architekturdiagramm, Fortschritt  
  
Es gibt auch mehrere nicht-Editor-Typen, die das Dokument verwenden. Während sie Dokumente selbst bearbeiten nicht, müssen sie Standardinteraktionen für Dokumentfenster folgen.  
  
-   **Berichte:** IntelliTrace Bericht des Berichts, Hyper-V, Profiler-Berichtsansicht  
  
-   **Dashboard:** Diagnose-Hub  
  
#### <a name="text-based-editors"></a>Textbasierte Editoren  
  
-   Das Dokument ist Teil der Vorschau Registerkartenmodell, mit dem für die Vorschau des Dokuments ohne ihn zu öffnen.  
  
-   Die Struktur des Dokuments kann in einem Begleit-Toolfenster, z. B. eine dokumentgliederung dargestellt werden.  
  
-   IntelliSense (falls zutreffend) verhält sich konsistent mit anderer Code-Editoren.  
  
-   Popups oder Unterstützung Benutzeroberfläche führen Sie ähnliche Formate und Muster für die vorhandenen ähnlichen Benutzeroberfläche, wie z.B. CodeLens ein.  
  
-   Meldungen zum Dokumentstatus werden in einem Infoleisten-Steuerelement am oberen Rand des Dokuments oder in der Statusleiste angezeigt.  
  
-   Der Benutzer muss sein können, Anpassen die Darstellung von Schriftarten und Farben, die mit einem **Tools > Optionen** Seite der freigegebenen Schriftarten und Farben Seite oder einen bestimmten in den Editor.  
  
#### <a name="design-surfaces"></a>Entwurfsoberflächen  
  
-   Ein leerer Designer müssen ein Wasserzeichen auf der Oberfläche, der angibt, wie Sie beginnen.  
  
-   Ansicht-switching-Mechanismen folgen vorhandenen Muster wie z. B. Doppelklicken Sie darauf, einen Code-Editor oder Registerkarten im Dokumentfenster ermöglicht die Interaktion mit beider Bereiche zu öffnen.  
  
-   Hinzufügen von Elementen auf der Entwurfsoberfläche sollte über die Toolbox ausgeführt werden, wenn ein Toolfenster für hochspezifische erforderlich ist.  
  
-   Elemente auf der Oberfläche folgen ein Modells konsistent Auswahl.  
  
-   Eingebettete Symbolleisten enthalten nur, die nicht häufig-Befehle für die spezifischen Befehle wie z. B. **speichern**.  
  
#### <a name="dialog-style-editors"></a>Dialogfeld-Stil-Editor  
  
-   Steuern des Layouts sollten normale Dialogfeld Layoutkonventionen befolgt werden.  
  
-   Registerkarten im Editor sollten nicht mit der Darstellung der Dokumentregisterkarten übereinstimmen, können sie einen der beiden zulässigen inneren Registerkarte Stile sollten übereinstimmen.  
  
-   Benutzer müssen sich mit den Steuerelementen, die mithilfe der Tastatur interagieren können; entweder den Editor wird aktiviert und wechseln mit der Tabulatortaste durch Steuerelemente oder mithilfe von standardmäßigen mnemonischen Zeichen.  
  
-   Der Designer sollte die allgemeine Modell speichern verwenden. Keine allgemeinen speichern "oder" Commit-Schaltflächen sollten auf der Oberfläche platziert werden, obwohl andere Schaltflächen geeignet sein können.  
  
#### <a name="model-designers"></a>Modell-Designer  
  
-   Ein leerer Designer müssen ein Wasserzeichen auf der Oberfläche, der angibt, wie Sie beginnen.  
  
-   Hinzufügen von Elementen auf der Entwurfsoberfläche sollte über die Toolbox ausgeführt werden.  
  
-   Elemente auf der Oberfläche folgen ein Modells konsistent Auswahl.  
  
-   Eingebettete Symbolleisten enthalten nur, die nicht häufig-Befehle für die spezifischen Befehle wie z. B. **speichern**.  
  
-   Auf der Oberfläche auf oder ein Wasserzeichen möglicherweise eine Legende angezeigt.  
  
-   Der Benutzer muss in der Lage, die Darstellung der die Schriftarten/Farben anpassen einer **Tools > Optionen** Seite der freigegebenen Schriftarten und Farben Seite oder einen bestimmten in den Editor.  
  
#### <a name="reports"></a>Berichte  
  
-   Berichte werden in der Regel Informationen nur und nicht einbezogen, in dem Modell speichern. Sie enthalten jedoch möglicherweise Interaktionen, wie Links zu anderen relevanten Informationen oder die Abschnitte, die erweitert und reduziert werden.  
  
-   Die meisten Befehle auf der Oberfläche sollte nicht die Schaltflächen links sein.  
  
-   Layout sollten eine Kopfzeile hinzufügen und befolgen Sie die Standardbericht Layout-Richtlinien.  
  
#### <a name="dashboards"></a>Dashboards  
  
-   Dashboards kein Interaktionsmodell selbst, aber als eine Möglichkeit, eine Vielzahl von anderen Tools zu bieten.  
  
-   Sie nicht im Modell speichern teilnehmen.  
  
-   Benutzer müssen sich für die Interaktion mit den Steuerelementen, die mithilfe der Tastatur und aktivieren den Editor, und wechseln mit der Tabulatortaste durch Steuerelemente oder mithilfe von standardmäßigen mnemonischen Code des können.  
  
##  <a name="BKMK_Dialogs"></a> Dialogfelder  
  
### <a name="introduction"></a>Einführung  
Dialogfelder in Visual Studio sollte in der Regel eine einzelne Arbeitseinheit des Benutzers unterstützen, und klicken Sie dann verworfen werden.  
  
Wenn Sie ermittelt haben, dass Sie ein Dialogfeld benötigen, haben Sie drei Optionen entspricht, in Reihenfolge ihrer Priorität:  
  
1.  Integrieren Sie Ihre Funktionen in einem der freigegebenen Dialogfelder in Visual Studio.  
  
2.  Erstellen Sie Ihre eigenen Dialogfeld unter Verwendung eines Musters finden Sie in einen vorhandenen ähnliche Dialog.  
  
3.  Erstellen Sie ein neues Dialogfeld "," folgende Interaktion "und" Layout Leitlinien.  
  
In diesem Abschnitt wird beschrieben, wie zum Auswählen des richtigen Dialogfeld-Musters in Visual Studio-Workflows und die allgemeine Konventionen für den Entwurf von Dialogfeld wird.  
  
### <a name="themes"></a>Designs  
Dialogfelder in Visual Studio führen Sie eine der zwei grundlegende Formate:  
  
#### <a name="standard-unthemed"></a>Standard (Unthemed)  
Die meisten Dialogfelder werden standard-Dienstprogramm-Dialogfelder und sollte Unthemed. Verwenden Sie nicht die Standardsteuerelemente Re-Vorlage oder stilisierte "modernen" Schaltflächen oder Steuerelemente zu erstellen. Steuerelemente, und führen Sie die Chrome-Darstellung [Windows Desktop Interaktion Standardrichtlinien für die Dialogfelder](/windows/desktop/uxguide/win-dialog-box).  
  
#### <a name="themed"></a>Design  
Spezielle "Signatur" Dialogfelder möglicherweise mit Design. Mit Design versehen sind eine eigene Darstellung, die auch einige spezielle Interaktionsmuster, die dem Stil zugeordnete verfügt. Design "das Dialogfeld nur dann, wenn sie diese Anforderungen erfüllt:  
  
-   Das Dialogfeld ist eine umfassende Umgebung, die angezeigt und häufig oder von vielen Benutzern verwendet werden (z. B. die **neues Projekt** Dialogfeld.  
  
-   Das Dialogfeld enthält die Elemente der Marke gut sichtbaren Produkte (z. B. die **Kontoeinstellungen** Dialogfeld).  
  
-   Das Dialogfeld wird angezeigt, wie ein wichtiger Teil eines größeren Flusses, die anderen Dialogfelder mit Design enthält (z. B. die **verbundenen Dienst hinzufügen** Dialogfeld).  
  
-   Das Dialogfeld "ist ein wichtiger Bestandteil der eine Benutzeroberfläche, die in Höherstufen oder eine Produktversion Unterscheidung eine strategische Rolle spielt.  
  
Wenn Sie ein Dialogfeld mit Design zu erstellen, verwenden Sie die Farben für die richtige Umgebung, und führen Sie das richtige Layout und die Interaktionsmuster. (Finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)  
  
### <a name="dialog-design"></a>Dialogfeld-Entwurf  
Ausgereifte Dialogfelder berücksichtigen Sie die folgenden Elemente:  
  
-   Die Benutzeraufgabe, die unterstützt werden  
  
-   Das Dialogfeld Text-Format, Sprache und Terminologie  
  
-   Auswahl des Steuerelements und UI-Konventionen  
  
-   Ausrichtung für visuelle Layout-Spezifikation und Kontrolle  
  
-   Tastaturzugriff  
  
#### <a name="content-organization"></a>Organisation von Inhalten  
Beachten Sie die Unterschiede zwischen diesen grundlegenden Typen von Dialogfeldern:  
  
-   [Einfache Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) Steuerelemente in einem einzelnen modale Fenster darstellen. Die Präsentation kann es sich um Variationen des komplexen Steuerelementmuster, z. B. eine Auswahl des Felds oder einer Symbolleiste enthalten.  
  
-   [Layered Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) werden verwendet, um Platz auf dem Bildschirm optimal zu nutzen, wenn ein einzelnes Element der Benutzeroberfläche mehrere Gruppen von Steuerelementen enthält. Das Dialogfeld Gruppierungen "über Registerkarten-Steuerelementen, Steuerelemente für die Seitennavigation oder Schaltflächen schichtenförmige", damit der Benutzer zu einem bestimmten Zeitpunkt finden Sie unter der Gruppe auswählen kann.  
  
-   [Assistenten](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) eignen sich zum Weiterleiten des Benutzers über eine logische Abfolge von Schritten auf den Abschluss einer Aufgabe. In sequenziellen Bereichen, manchmal Einführung in anderen Workflows ("Branches") eine in den vorherigen Bereich vorgenommenen Auswahl abhängig, werden eine Reihe von Optionen angeboten.  
  
####  <a name="BKMK_SimpleDialogs"></a> Einfache Dialogfelder  
Ein einfaches Dialogfeld ist eine Darstellung der Steuerelemente in einem einzelnen modale Fenster. In dieser Präsentation möglicherweise abweichungen von komplexen Steuerelementmustern, z. B. eine Feldauswahl. Führen Sie für einfache Dialoge das Standardlayout für die allgemeine als auch für bestimmte Layouts für komplexe Steuerelement Gruppierungen erforderlich sind.
  
![> Erstellen Sie Schlüssel für einen starken Namen wird ein Beispiel für ein einfaches Dialogfeld in Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704 Artikelnr-01_CreateStrongNameKey")<br />Erstellen Sie Schlüssel für einen starken Namen wird ein Beispiel für ein einfaches Dialogfeld in Visual Studio.
  
####  <a name="BKMK_LayeredDialogs"></a> Überlappende Dialogfelder  
Überlappende Dialoge enthalten Registerkarten, Dashboards und eingebettete Strukturen. Sie werden verwendet, um Platz zu maximieren, wenn mehrere Gruppen von Steuerelementen in einem einzelnen Element der Benutzeroberfläche angeboten vorhanden sind. Die Gruppierungen geschichtet werden, damit der Benutzer die Gruppierung auf einem beliebigen Zeitpunkt auswählen kann.  
  
Im einfachsten Fall ist der Mechanismus für das Wechseln zwischen Gruppen ein Registerkarten-Steuerelement. Es gibt verschiedene Alternativen zur Verfügung. Festlegen der Priorität und Überlagerung für das am besten geeignete Format auswählen angezeigt.  
  
Die **Tools &gt; Optionen** Dialog ist ein Beispiel für ein Dialogfeld mit Ebenen mit einer eingebetteten Struktur:  
  
![Extras > Optionen ist ein Beispiel für ein Dialogfeld mit Ebenen in Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704 Artikelnr-02_ToolsOptions")<br />Extras > Optionen ist ein Beispiel für ein Dialogfeld mit Ebenen in Visual Studio.
  
####  <a name="BKMK_Wizards"></a> Assistenten  
Assistenten sind nützlich für das Weiterleiten des Benutzers über eine logische Abfolge von Schritten bei der Durchführung einer Aufgabe. Eine Reihe von Optionen werden in sequenzieller Bereiche angeboten, und der Benutzer muss durch jeden Schritt vor dem Fortfahren zur nächsten fortfahren. Sobald genügend Standardwerte verfügbar sind, werden die **Fertig stellen** Schaltfläche ist aktiviert.  
  
 Modale-Assistenten für Aufgaben verwendet werden, die:  
  
-   Enthalten Sie, Verzweigungen, wobei unterschiedliche Pfade je nach Benutzerauswahl angeboten werden  
  
-   Enthalten Sie Abhängigkeiten zwischen den Schritten, die in nachfolgende Schritten auf Benutzereingaben aus der vorherigen Schritte ab abhängen  
  
-   Sind ausreichend komplex, dass die Benutzeroberfläche verwendet werden soll, um die angebotenen Optionen sowie die möglichen Ergebnisse in jedem Schritt wird erläutert  
  
-   Sind transaktional ist, dass eine Reihe von Schritten in ihrer Gesamtheit abgeschlossen werden, bevor ein Commit für Änderungen ausgeführt wird  
  
### <a name="common-conventions"></a>Häufig verwendete Konventionen  
Um eine optimale Designs und der Funktionen, die mit Ihrer Dialogen zu erzielen, befolgen Sie diese Konventionen Größe des Dialogfelds, Position, Standards, die Konfiguration der Zugriffssteuerung und Ausrichtung, Benutzeroberfläche Text, Titelleisten, Steuerschaltflächen und Zugriffsschlüssel.  
  
Layout-spezifische Richtlinien finden Sie [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Größe  
Dialogfelder sollte innerhalb einer mindestauflösung von 1024 x 768 Bildschirm passen, und Größe des ersten Dialogfelds darf 900 x 700 Pixel nicht überschreiten. Möglicherweise ist Dialogfelder mit veränderbarer Größe, aber es ist nicht erforderlich.  
  
Es gibt zwei Empfehlungen für Dialoge mit änderbarer Größe:  
  
1.  Dass eine Mindestgröße für den Dialog definiert, das für die Gruppe "Steuerelemente" ohne Clipping optimieren und anpassen ist, um sinnvolle Lokalisierung Wachstum zu ermöglichen.  
  
2.  Dass die Größe skaliert Benutzer aus mehreren Sitzungen beibehalten. Z. B. wenn der Benutzer ein Dialogfeld, um 150 % hochskaliert wird, zeigt klicken Sie dann einen nachfolgenden Start des Dialogs 150 %.  
  
#### <a name="position"></a>Position  
Dialoge müssen in der IDE beim ersten Start zentriert angezeigt werden. Die letzte Position nicht veränderbare Größen Dialogfelder muss nicht beibehalten werden, damit sie auf den nachfolgenden Starts zentriert angezeigt werden. 

Für Dialoge mit änderbarer Größe sollte die Größe auf nachfolgenden Starts beibehalten werden. Für modale Dialogfelder mit veränderbarer Größe muss die Position nicht persistent gespeichert werden. Anzeigen, sie in der IDE zentriert wird verhindert, dass das Dialogfeld in eine unvorhersehbare oder unbrauchbar Position angezeigt werden, wenn Anzeigekonfiguration des Benutzers geändert wurde. 

Für nicht modale Dialoge, die neu positioniert werden können, sollten auf nachfolgenden Starts Position des Benutzers beibehalten werden, wie das Dialogfeld häufig als ein wesentlicher Bestandteil eines größeren Workflows verwendet werden kann.  
  
Wenn Dialogfelder andere Dialogfelder erzeugen müssen, sollte das oberste Dialogfeld kaskadiert werden rechts und nach unten aus dem übergeordneten Element so, dass die It für den Benutzer ersichtlich ist, die sie an einen neuen Ort navigiert haben.  
  
#### <a name="modality"></a>Modalität  
Modal wird bedeutet, dass Benutzer aufgefordert werden, abgeschlossen oder das Dialogfeld zu schließen, bevor Sie fortfahren. Da modale Dialogfelder Interaktion mit anderen Teilen der Umgebung des Benutzers blockieren, sollten Sie durch Ihre Features Aufgabenverlauf so selten wie möglich verwenden werden. Wenn ein modaler Vorgang erforderlich ist, hat Visual Studio eine Anzahl von freigegebenen Dialogfelder, die, denen Sie Ihre Funktionen in integrieren können. Wenn Sie ein neues Dialogfeld erstellen möchten, folgen Sie diesem Interaktionsmuster einen vorhandenen Dialog mit ähnlichen Funktionen aus.  
  
Wenn der Benutzer zwei Aktivitäten gleichzeitig ausführen müssen, wie **finden** und **ersetzen** beim Schreiben von neuem Code aus, das Dialogfeld muss nicht modales, damit der Benutzer problemlos zwischen diesen wechseln kann. Visual Studio verwendet die Toolfenster in der Regel für diese Art von verknüpfte Aufgabe-Editor-Unterstützung.  
  
#### <a name="control-configuration"></a>Die Konfiguration der Zugriffssteuerung  
Mit vorhandenen steuerelementkonfigurationen, die den selben in Visual Studio Zweck konsistent sein.  
  
#### <a name="title-bars"></a>Titelleisten  
  
-   Der Text in der Titelleiste muss der Name des Befehls widerspiegeln, die sie gestartet.  
  
-   Symbol "keine" sollte auf Titelleisten Dialogfeld verwendet werden. Verwenden Sie in Fällen, in denen das System eine erfordert das Visual Studio-Logo.  
  
-   Dialogfelder dürfen keine minimieren oder Maximieren Sie die Schaltflächen.  
  
-   Hilfe-Schaltflächen in der Titelleiste sind veraltet. Fügen Sie sie nicht für neue Dialogfelder. Wenn sie vorhanden sind, sollten sie ein Hilfethema gestartet, vom Konzept her für die Aufgabe relevant ist.  
  
 ![Spezifikationen der Richtlinie für Titelleisten in Visual Studio-Dialogfeldern](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704 Artikelnr-03_TitleBarSpecs")<br />Spezifikationen der Richtlinie für Titelleisten in Visual Studio-Dialogfelder
  
#### <a name="control-buttons"></a>Steuerschaltflächen  
Im allgemeinen **OK**, **Abbrechen**, und **Hilfe** Schaltflächen in der unteren rechten Ecke des Dialogfelds horizontal angeordnet werden soll. Die alternative vertikale Stapel ist zulässig, wenn ein Dialogfeld mehrere andere Schaltflächen am unteren Rand des Dialogfelds enthält, die visual Verwechslungen mit den Schaltflächen des Steuerelements darstellen würde.  
  
![Zulässige Konfigurationen für Steuerelementschaltflächen in Visual Studio-Dialogfeldern](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704 Artikelnr-04_ControlButtonConfig")<br />Zulässige Konfigurationen für Steuerelementschaltflächen in Visual Studio-Dialogfelder
  
Das Dialogfeld muss es sich um eine Standardschaltfläche für das Steuerelement enthalten. Um zu bestimmen, die beste Befehl aus, um als Standard verwenden, wählen Sie die folgenden Optionen (aufgeführt in der Rangfolge):  
  
-   Wählen Sie den Befehl am sichersten und sichersten, als Standard. Dies bedeutet, dass des Befehls, die wahrscheinlich zu verhindern, dass Daten verloren gehen, und vermeiden unbeabsichtigte Systemzugriff.  
  
-   Wenn Daten verloren gehen und die Sicherheit nicht Faktoren sind, wählen Sie dann den Standardbefehl basierend auf der Einfachheit halber ein. Die wahrscheinlichste-Befehls als Standard steigert den Workflow des Benutzers, wenn das Dialogfeld häufige oder sich wiederholende Aufgaben unterstützt.  
  
Vermeiden Sie die Auswahl einer dauerhaft destruktiven Aktion für den Standardbefehl. Wenn so ein Befehl vorhanden ist, wählen Sie stattdessen einen sichereren Befehl als Standard.  
  
#### <a name="access-keys"></a>Zugriffsschlüssel  
Verwenden Sie nicht die Zugriffsschlüssel für **OK**, **Abbrechen**, oder **Hilfe** Schaltflächen. Diese Schaltflächen sind standardmäßig auf Tastenkombinationen zugeordnet:  
  
| Schaltflächenname | Tastenkombination |  
| --- | --- |  
| OK | EINGABETASTE |  
| Abbrechen | Esc |  
| Hilfe | F1 |  
  
#### <a name="imagery"></a>Bilder  
Verwenden Sie Bilder nur selten in Dialogfeldern. Verwenden Sie keine große Symbole in Dialogfeldern nur, um Speicherplatz zu verwenden. Verwenden Sie Bilder aus, nur dann, wenn sie ein wichtiger Teil die Nachricht an den Benutzer, z. B. Warnsymbole oder Status Animationen Sicherheitssystemen sind.  
  
###  <a name="BKMK_PrioritizingAndLayering"></a> Priorisieren und Schichten  
  
#### <a name="prioritizing-your-ui"></a>Priorisieren die Benutzeroberfläche  
Es ist möglicherweise erforderlich, bestimmte Elemente der Benutzeroberfläche in den Vordergrund zu bringen, und platzieren Sie erweiterte Verhalten und die Optionen (einschließlich ungewöhnliche Befehle) in Dialogfeldern. Bringen Sie häufig verwendete Funktionen in den Vordergrund, indem des Arbeitsbereichs für sie und Sichtbarmachung standardmäßig in der Benutzeroberfläche mit einer textbezeichnung, wenn das Dialogfeld angezeigt wird.  
  
#### <a name="layering-your-ui"></a>Schichten von der Benutzeroberflächenautomatisierungs  
Wenn Sie ermittelt haben, dass ein Dialogfeld erforderlich ist, aber die zugehörige Funktionen, die Sie dem Benutzer anzeigen möchten daran hinausgeht, was in einem einfachen Dialogfeld angezeigt werden kann, müssen Sie Ihre UI-Ebene. Am häufigsten verwendeten Schichten-Methoden, die Visual Studio verwendet werden, Registerkarten und Fluren oder Dashboards. In einigen Fällen möglicherweise entsprechenden Bereiche, die erweitern und reduzieren können. Adaptive Benutzeroberfläche wird in Visual Studio in der Regel nicht empfohlen.  
  
Es gibt vor- und Nachteile zu den verschiedenen Methoden der Benutzeroberfläche über die Registerkarte "-ähnliche Steuerelemente Schichten. Überprüfen Sie die Liste unten aus, um sicherzustellen, dass Sie eine Überlagerung-Technik auswählen, die für Ihre Situation geeignet ist.  
  
##### <a name="tabbing"></a>Wechseln mit der Tabulatortaste  
  
| Durch den Wechsel des Mechanismus | Vor- und angemessene Verwendung | Nachteile und nicht ordnungsgemäße Verwendung |  
| --- | --- | --- |  
| Registersteuerelement | Dialogfeldseiten logisch zu gruppieren, in dem Verwandte<br /><br />Für weniger als fünf (oder die Anzahl der Registerkarten, die in einer Zeile entsprechen, über das Dialogfeld ") hilfreich Seiten von verwandten Steuerelementen im Dialogfeld"<br /><br />Registerkartenbezeichnungen müssen kurz sein: ein oder zwei Wörter, die einfach den Inhalt identifizieren können<br /><br />Eine allgemeine Systemstil-Dialogfeld<br /><br />Beispiel: **Datei-Explorer &gt; -Elementeigenschaften** | Vornehmen von beschreibenden kurzen Bezeichnungen kann schwierig sein<br /><br />Im Allgemeinen skalieren nicht nach fünf Registerkarten in einem Dialogfeld<br /><br />Nicht geeignet, wenn Sie viele Registerkarten für eine Zeile (verwenden Sie eine alternative Schichten Technik) haben<br /><br />Nicht erweiterbar. |  
| Seitenleistennavigation | Einfache durch den Wechsel des Gerät, das weitere Kategorien als Registerkarten aufnehmen kann<br /><br />Flache Liste von Kategorien (ohne Hierarchie)<br /><br />Erweiterbar<br /><br />Beispiel: **anpassen... &gt; Befehl "hinzufügen"** | Nicht für eine gute Verwendung der horizontalen Bereich, wenn weniger als drei Gruppen vorhanden sind<br /><br />Aufgabe möglicherweise besser geeignet, um eine Dropdownliste sein. |  
| Struktursteuerelement | Ermöglicht unbegrenzte Anzahl an Kategorien<br /><br />Ermöglicht die Gruppierung und/oder die Hierarchie der Kategorien<br /><br />Erweiterbar<br /><br />Beispiel: **Tools &gt; Optionen** | Stark geschachtelte Hierarchien kann eine übermäßige horizontalen Bildlauf<br /><br />Visual Studio verfügt über eine Overabundance von Strukturansichten |  
| Assistent | Unterstützt Sie bei Abschluss der Aufgabe, durch den Benutzer aufgabenbasierte, sequenziellen Schritte zur Verfügung stellt: der Assistent stellt eine übergeordnete Aufgabe und die einzelnen Bereiche darstellen, erforderlich, um die gesamte Aufgabe Unteraufgaben<br /><br />Ist nützlich, wenn die Aufgabe über Benutzeroberflächen, mehrere als wenn der Benutzer andernfalls müssten verwenden mehrere Editoren und Tools zu Windows so, dass die Aufgabe abgeschlossen<br /><br />Ist nützlich, wenn der Task Verzweigungen erfordert.<br /><br />Ist nützlich, wenn Sie den Task Abhängigkeiten zwischen den Schritten enthält.<br /><br />Ist nützlich, wenn mehrere ähnliche Aufgaben mit einer Entscheidung Verzweigung in ein Dialogfeld zum Reduzieren der Anzahl der andere ähnliche Dialogfelder angezeigt werden kann | Für jede Aufgabe, die einen sequenziellen Workflow keine erfordert nicht geeignet.<br /><br />Benutzer können schwer und von einem Assistenten mit zu vielen Schritten verwechselt werden.<br /><br />Assistenten haben grundsätzlich Platz auf dem Bildschirm begrenzt. |  
  
##### <a name="hallways-or-dashboards"></a>Fluren oder -dashboards  
Fluren und Dashboards werden Dialogfelder oder Bereiche, die als starten verweist auf die anderen Dialogfelder und Fenster dienen. Die ausgereifte "Gang" offenbart sofort, nur die am häufigsten verwendeten Optionen, Befehle und Einstellungen, sodass der Benutzer sofort häufige Aufgaben. Wie Sie eine reale Gang Doorways für den Zugriff auf die Räume dahinter bereitstellt, hier die Benutzeroberfläche weniger übliche separate "Räume" (häufig andere Dialogfelder) verwandter Funktionen, die von den wichtigsten Gang zugegriffen werden kann zu sammeln.  
  
Sie können auch eine Benutzeroberfläche, die alle verfügbaren Funktionen in einer einzelnen Auflistung bietet, anstatt die weniger übliche-Funktionalität in verschiedenen Standorten refactoring einfach ein Dashboard ist.  
  
![Hallway-Konzept für das Verfügbarmachen von zusätzlichen Benutzeroberfläche in Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704 Artikelnr-08_Hallway")<br />Hallway-Konzept für das Verfügbarmachen von zusätzlichen Benutzeroberfläche in Outlook
  
##### <a name="adaptive-ui"></a>Adaptive Benutzeroberfläche  
Ein- oder Ausblenden der Benutzeroberfläche basierend auf Nutzung oder eine selbst der Benutzeroberfläche ist eine weitere Möglichkeit zur Darstellung der benötigten Benutzeroberfläche gleichzeitig das Ausblenden von anderen Teilen von. Dies sollte nicht in Visual Studio die Algorithmen für die Entscheidung zwischen ein- oder Ausblenden der Benutzeroberfläche können schwierig sein, und die Regeln werden immer für eine beliebige Gruppe von Fällen falsch sein.  
  
##  <a name="BKMK_Projects"></a> Projekte  
  
### <a name="projects-in-the-solution-explorer"></a>Projekte im Projektmappen-Explorer  
Die meisten Projekte werden als anhand von verweisen, Directory-basierte oder gemischte klassifiziert. Alle drei Typen von Projekten werden im Projektmappen-Explorer gleichzeitig unterstützt. Der Stamm der benutzererfahrung bei der Arbeit mit Projekten findet innerhalb dieses Fensters. Obwohl verschiedene Projektknoten Verweis, Verzeichnis oder Projekten im gemischten Modus vom Typ sind, besteht ein allgemeines Interaktionsmuster, das als Ausgangspunkt vor dem in-Projekt – bestimmter Benutzermuster Auseinanderlaufende angewendet werden soll.  
  
Projekte sollten Sie stets:  
  
-   Unterstützen Sie die Möglichkeit, Projektordner zum Organisieren von Inhalt des Projekts hinzufügen  
  
-   Beibehalten eines konsistenten Modells zum projektpersistenz  
  
Projekte sollten auch für konsistente interaktionsmodelle beibehalten:  
  
-   Entfernen von Projektelementen  
  
-   Speichern von Dokumenten  
  
-   Projekt Eigenschaft bearbeiten  
  
-   Bearbeiten das Projekt in einer alternativen Ansicht  
  
-   Drag & Drop-Vorgänge  
  
### <a name="drag-and-drop-interaction-model"></a>Drag & Drop-Interaktion  
Projekte in der Regel Klassifizieren von sich selbst als anhand von verweisen (nur Verweise auf die Projektelemente im Speicher beibehalten werden können), Directory-basierte (können nur Projektelemente physisch beibehalten gespeichert innerhalb eines Projekts Hierarchie), oder gemischt (können Verweise beibehalten werden. (oder physischen Elementen). Die IDE unterstützt alle drei Typen von Projekten gleichzeitig innerhalb der **Projektmappen-Explorer**.  
  
Hinsichtlich der Drag & Drop die folgenden Merkmale treffen sollten, um jede Art von Projekt in der **Projektmappen-Explorer**:  
  
-   **Referenz-basiertes Projekt:** der wichtigste Punkt ist, dass das Projekt um einen Verweis auf ein Element im Speicher zieht. Wenn Sie ein Referenz-basiertes Projekt als Quelle für einen Verschiebevorgang fungiert, sollten sie nur den Verweis auf das Element aus dem Projekt entfernen. Das Element sollte von der Festplatte nicht tatsächlich gelöscht werden. Wenn Sie ein Referenz-basiertes Projekt als Ziel für einen Vorgang verschieben (oder kopieren) fungiert, sollten sie einen Verweis auf dem ursprünglichen Quellelement hinzufügen, ohne dass eine private Kopie des Elements.  
  
-   **Verzeichnisbasiertes Projekt:** aus einem Drag & Drop-Sicht, das Projekt für das physische Element statt einen Verweis zieht. Wenn ein Verzeichnisbasiertes Projekt als Quelle für einen Verschiebevorgang fungiert, sollte es am Ende das Löschen der physischen Elements von der Festplatte als auch aus dem Projekt entfernen. Wenn ein Verzeichnisbasiertes Projekt als Ziel für einen Vorgang verschieben (oder kopieren) fungiert, sollte es eine Kopie des Quellelements in den Zielspeicherort erstellen.  
  
-   **Gemischte Zielprojekt:** aus Sicht einer Drag & Drop das Verhalten dieser Art von Projekt ist aufgrund der Natur des Elements gezogen wird, entweder (einen Verweis auf ein Element im Speicher) oder das Element selbst. Das richtige Verhalten für Verweise und physischen Elementen oben beschrieben werden.  
  
Wenn es nur eine Art von Projekt in gab der **Projektmappen-Explorer**, Drag & Drop-Vorgänge einfach wäre. Da jede Projektsystem die Möglichkeit, eigene Drag & Drop-Verhalten definiert hat, sollten bestimmte Richtlinien (basierend auf dem Windows Explorer-Drag & Drop-Verhalten) befolgt werden, um eine vorhersagbare benutzererfahrung zu gewährleisten:  
  
-   Einer unveränderten Ziehen mit der der **Projektmappen-Explorer** (Wenn weder STRG-UMSCHALT-Taste gedrückt gehalten werden) sollten dazu führen, ein Verschiebevorgang.  
  
-   Ziehen bei gedrückter Umschalttaste Vorgang soll auch zu einem Verschiebevorgang führen.  
  
-   Ziehen Sie mit der STRG-Taste Vorgang sollte in einem Kopiervorgang führen.  
  
-   Anhand von verweisen und gemischte Projektsystemen unterstützen das Konzept des Hinzufügens einer Verknüpfung (oder referenzieren) auf das Quellelement. Wenn diese Projekte sind das Ziel eines Drag & Drop-Vorgangs (Wenn **STRG + UMSCHALT** gedrückt gehalten wird), sie sollten dazu führen, einen Verweis auf das Element dem Projekt hinzugefügt wird  
  
Nicht alle Drag & Drop-Vorgänge sind Kombinationen von verweisbasierte, Directory-basierte und gemischte Projekte sinnvoll. Insbesondere ist es problematisch, vorzugeben, um einen Verschiebevorgang zwischen einem verzeichnisbasierte-Source-Projekt und eine verweisbasierte Zielprojekt zu ermöglichen, da das Quellprojekt verzeichnisbasierte zugreifen kann, um das Quellelement nach Abschluss der Verschiebung zu löschen. Das Zielprojekt verweisbasierte würde dann einen Verweis auf ein gelöschtes Element erhalten.  
  
Es ist jedoch auch irreführend sein, um einen Kopiervorgang zwischen diesen Typen von Projekten zu ermöglichen, da das Zielprojekt anhand von Verweisen eine unabhängige Kopie des Quellelements durchführen dürfen, vorzugeben. Auf ähnliche Weise sollte STRG + UMSCHALT, die Sie in ein Verzeichnis-basierte Zielprojekt ziehen nicht zulässig, da ein Verzeichnisbasiertes Projekt Verweise beibehalten werden kann. In Fällen, in denen die Drag & Drop-Vorgang nicht unterstützt wird, sollte die IDE unterbinden die Dropdownliste und dem Benutzer anzeigen, den keine Ablage-Cursor (in Zeiger in der folgenden Tabelle dargestellt).  
  
Um Drag & Drop-Verhalten ordnungsgemäß zu implementieren, muss das Quellprojekt des Ziehvorgangs seiner Natur in das Zielprojekt kommunizieren können. (Beispielsweise ist es Referenz - oder Verzeichnis-basierte?) Diese Informationen wird durch das Format der Zwischenablage angezeigt, die von der Quelle bereitgestellt werden. Als Quelle eines Drag & (oder Kopieren der Zwischenablagevorgang) sollte bieten ein Projekt entweder `CF_VSREFPROJECTITEMS` oder `CF_VSSTGPROJECTITEMS` , je nachdem, ob das Projekt anhand von verweisen oder verzeichnisbasierte. Beide Formate haben den gleichen Dateninhalt, der ähnelt der Windows `CF_HDROP` formatieren mit dem Unterschied, dass Listen von Zeichenfolgen, anstatt von Dateinamen, einen Double-Wert - sind`NULL` beendet Sie die Liste der `Projref` Zeichenfolgen (wie vom zurückgegeben`IVsSolution::GetProjrefOfItem`oder `::GetProjrefOfProject` je nach Bedarf).  
  
Als Ziel einer Drop (oder die Zwischenablage einfügen-Vorgang), sollte ein Projekt akzeptieren sowohl `CF_VSREFPROJECTITEMS` und `CF_VSSTGPROJECTITEMS`, obwohl die genaue Behandlung von den Drag & Drop-Vorgang abhängig von der Art der das Zielprojekt und das Quellprojekt variiert. Das Quellprojekt deklariert seiner Natur von, ob es bietet `CF_VSREFPROJECTITEMS` oder `CF_VSSTGPROJECTITEMS`. Das Ziel des Ablegevorgangs eigene Art versteht und hat daher genügend Informationen, um Entscheidungen zu treffen, ob eine verschieben, kopieren oder Link ausgeführt werden soll. Der Benutzer ändert auch die Drag & Drop-Vorgang durch Drücken der STRG, UMSCHALTTASTE gedrückt, oder sowohl STRG und Umschalttaste ausgeführt werden soll. Es ist wichtig für das Ablageziel, um ordnungsgemäß anzugeben, welcher Vorgang im Voraus in ausgeführt wird seine `DragEnter` und `DragOver` Methoden. Die **Projektmappen-Explorer** automatisch weiß, ob das Source-Projekt und das Zielprojekt desselben Projekts sind.  
  
Ziehen Projektelemente auf Instanzen von Visual Studio (z. B. von einer Instanz von devenv.exe in einen anderen), wird ausdrücklich nicht unterstützt. Die **Projektmappen-Explorer** auch direkt wird deaktiviert.  
  
Der Benutzer muss immer bestimmen Sie die Auswirkungen eines Drag & Drop-Vorgangs durch Auswahl eines Elements, ziehen es an den Zielspeicherort und beobachten, die von den folgenden Mauszeiger angezeigt wird, bevor das Element gelöscht wird:  
  
| Mauszeiger | Befehl | Beschreibung |  
| :---: | --- | --- |  
| ![Symbol für "keine Ablage" mit der Maus](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Keine Ablage | Element kann nicht am angegebenen Speicherort abgelegt werden. |  
| ![Symbol für "Copy" der Maus](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Kopieren | Element wird an den Zielspeicherort kopiert werden. |  
| ![Maus Symbol "verschieben"](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Verschieben | Element wird an den Zielspeicherort verschoben werden. |  
| ![Symbol für "Verweis hinzufügen" Maus](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Verweis hinzufügen | Ein Verweis auf das ausgewählte Element wird an den Zielspeicherort hinzugefügt werden. |

#### <a name="reference-based-projects"></a>Referenz-basierte Projekte  
 Die folgende Tabelle enthält die Drag & Drop (sowie Ausschneiden/Kopieren/Einfügen) Vorgänge, die ausgeführt werden sollte aufgrund der Natur von Quelle Element und Modifizierer gedrückt für verwiesen basierende Zielprojekte:  
  
| Modifizierer | Kategorie | Das Quellelement: Verweis/Link | Das Quellelement: physische Element oder das Dateisystem (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Kein Modifizierer | Aktion | Verschieben | Link |  
| Kein Modifizierer | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Verweis auf das ursprüngliche Element hinzugefügt |  
| Kein Modifizierer | Quelle | Löscht Verweis zum ursprünglichen Element | Beibehalten des ursprünglichen Elements |  
| Kein Modifizierer | Ergebnis | `DROPEFFECT_MOVE` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_LINK` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |  
| Umschalt + Ziehen | Aktion | Verschieben | Keine Ablage |  
| Umschalt + Ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Keine Ablage |  
| Umschalt + Ziehen | Quelle | Löscht Verweis zum ursprünglichen Element | Keine Ablage |  
| Umschalt + Ziehen | Ergebnis | `DROPEFFECT_MOVE` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | Keine Ablage |  
| STRG + Ziehen | Aktion | Kopieren | Keine Ablage |  
| STRG + Ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Keine Ablage |  
| STRG + Ziehen | Quelle | Beibehalten Referenz zum ursprünglichen Element | Keine Ablage |  
| STRG + Ziehen | Ergebnis | `DROPEFFECT_COPY` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | Keine Ablage |  
| STRG + UMSCHALT + ziehen | Aktion | Link | Link |  
| STRG + UMSCHALT + ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Verweis auf das ursprüngliche Element hinzugefügt |  
| STRG + UMSCHALT + ziehen | Quelle | Beibehalten Referenz zum ursprünglichen Element | Beibehalten des ursprünglichen Elements |  
| STRG + UMSCHALT + ziehen | Ergebnis | `DROPEFFECT_LINK` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_LINK` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |  
| STRG + UMSCHALT + ziehen | Hinweis | Identisch mit Drag & Drop-Verhalten für Tastenkombinationen im Windows-Explorer. ||  
| Ausschneiden und einfügen | Aktion | Verschieben | Link |  
| Ausschneiden und einfügen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Verweis auf das ursprüngliche Element hinzugefügt |  
| Ausschneiden und einfügen | Quelle | Beibehalten Referenz zum ursprünglichen Element|Beibehalten des ursprünglichen Elements |  
| Ausschneiden und einfügen | Ergebnis | Element bleibt im ursprünglichen Speicherort im Speicher | Element bleibt im ursprünglichen Speicherort im Speicher |  
| Kopieren und einfügen | Aktion | Kopieren | Link |  
| Kopieren und einfügen | Quelle | Verweis auf das ursprüngliche Element hinzugefügt | Verweis auf das ursprüngliche Element hinzugefügt |  
| Kopieren und einfügen | Ergebnis | Beibehalten Referenz zum ursprünglichen Element | Beibehalten des ursprünglichen Elements |  
| Kopieren und einfügen | Aktion | Element bleibt im ursprünglichen Speicherort im Speicher | Element bleibt im ursprünglichen Speicherort im Speicher |  
  
#### <a name="directory-based-projects"></a>Verzeichnisbasierte Projekte  
Die folgende Tabelle enthält die Drag & Drop (sowie Ausschneiden/Kopieren/Einfügen) Vorgänge, die ausgeführt werden sollte aufgrund der Natur von Element "und"-Modifizierer Quellschlüssel gedrückt für verzeichnisbasierte Zielprojekte:  
  
| Modifizierer | Kategorie | Das Quellelement: Verweis/Link | Das Quellelement: physische Element oder das Dateisystem (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Kein Modifizierer | Aktion | Verschieben | Verschieben |  
| Kein Modifizierer | Ziel | Kopien Element Zielspeicherort | Kopien Element Zielspeicherort |  
| Kein Modifizierer | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Verweis zum ursprünglichen Element | | Kein Modifizierer | Ergebnis | `DROPEFFECT_MOVE` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_MOVE` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |  
| Umschalt + Ziehen | Aktion | Verschieben | Verschieben |  
| Umschalt + Ziehen | Ziel | Kopien Element Zielspeicherort | Kopien Element Zielspeicherort |  
| Umschalt + Ziehen | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Element aus der ursprünglichen Speicherort |
| Umschalt + Ziehen | Ergebnis | `DROPEFFECT_MOVE` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_MOVE` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |  
| STRG + Ziehen | Aktion | Kopieren | Kopieren |  
| STRG + Ziehen | Ziel | Kopien Element Zielspeicherort | Kopien Element Zielspeicherort |  
| STRG + Ziehen | Quelle | Beibehalten Referenz zum ursprünglichen Element | Beibehalten Referenz zum ursprünglichen Element |  
| STRG + Ziehen | Ergebnis | `DROPEFFECT_COPY` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_COPY` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |  
| STRG + UMSCHALT + ziehen | | Keine Ablage | Keine Ablage |  
| Ausschneiden und einfügen | Aktion | Verschieben | Verschieben |  
| Ausschneiden und einfügen | Ziel | Kopien Element Zielspeicherort | Kopien Element Zielspeicherort |  
| Ausschneiden und einfügen | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Element aus der ursprünglichen Speicherort |  
| Ausschneiden und einfügen | Ergebnis | Element bleibt im ursprünglichen Speicherort im Speicher | Element wird vom ursprünglichen Speicherort im Speicher gelöscht. |  
| Kopieren und einfügen | Aktion | Kopieren | Kopieren |  
| Kopieren und einfügen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Kopien Element Zielspeicherort |  
| Kopieren und einfügen | Quelle | Beibehalten des ursprünglichen Elements | Beibehalten des ursprünglichen Elements |  
| Kopieren und einfügen | Ergebnis | Element bleibt im ursprünglichen Speicherort im Speicher | Element bleibt im ursprünglichen Speicherort ins Speicher |
  
#### <a name="mixed-target-projects"></a>Mixed-Zielprojekte  
Die folgende Tabelle enthält die Drag & Drop (sowie Ausschneiden/Kopieren/Einfügen) Vorgänge, die ausgeführt werden sollte aufgrund der Natur von Quelle Element und Modifizierer gedrückt für gemischte-Zielprojekte:  
  
| Modifizierer | Kategorie | Das Quellelement: Verweis/Link | Das Quellelement: physische Element oder das Dateisystem (`CF_HDROP`) |  
| --- | --- | --- | --- |
| Kein Modifizierer | Aktion | Verschieben | Verschieben |
| Kein Modifizierer | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Kopien Element Zielspeicherort |
| Kein Modifizierer | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Verweis zum ursprünglichen Element |
| Kein Modifizierer | Ergebnis | `DROPEFFECT_ MOVE` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_ MOVE` wird zurückgegeben, als Aktion aus `::Drop` und Element aus der ursprünglichen Speicherort im Speicher gelöscht wird |
| Umschalt + Ziehen | Aktion | Verschieben | Verschieben |
| Umschalt + Ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Kopien Element Zielspeicherort |
| Umschalt + Ziehen | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Element aus der ursprünglichen Speicherort | 
| Umschalt + Ziehen | Ergebnis | `DROPEFFECT_ MOVE` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_ MOVE` wird zurückgegeben, als Aktion aus `::Drop` und Element aus der ursprünglichen Speicherort im Speicher gelöscht wird |
| STRG + Ziehen | Aktion | Kopieren | Kopieren |
| STRG + Ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Kopien Element Zielspeicherort |
| STRG + Ziehen | Quelle | Beibehalten Referenz zum ursprünglichen Element | Beibehalten des ursprünglichen Elements |
| STRG + Ziehen | Ergebnis | `DROPEFFECT_ COPY` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_ COPY` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |
| STRG + UMSCHALT + ziehen | Aktion | Link | Link |
| STRG + UMSCHALT + ziehen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Fügt der Verweis auf die ursprüngliche Quellelement |
| STRG + UMSCHALT + ziehen | Quelle | Beibehalten Referenz zum ursprünglichen Element | Beibehalten des ursprünglichen Elements |
| STRG + UMSCHALT + ziehen | Ergebnis | `DROPEFFECT_ LINK` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher | `DROPEFFECT_ LINK` wird zurückgegeben, als Aktion aus `::Drop` und Element bleibt im ursprünglichen Speicherort im Speicher |
| Ausschneiden und einfügen | Aktion | Verschieben | Verschieben |
| Ausschneiden und einfügen | Ziel | Kopien Element Zielspeicherort | Kopien Element Zielspeicherort |
| Ausschneiden und einfügen | Quelle | Löscht Verweis zum ursprünglichen Element | Löscht Element aus der ursprünglichen Speicherort |
| Ausschneiden und einfügen | Ergebnis | Element bleibt im ursprünglichen Speicherort im Speicher | Element wird vom ursprünglichen Speicherort im Speicher gelöscht. |
| Kopieren und einfügen | Aktion | Kopieren | Kopieren |
| Kopieren und einfügen | Ziel | Verweis auf das ursprüngliche Element hinzugefügt | Kopien Element Zielspeicherort |
| Kopieren und einfügen | Quelle | Beibehalten des ursprünglichen Elements | Beibehalten des ursprünglichen Elements |
| Kopieren und einfügen | Ergebnis | Element bleibt im ursprünglichen Speicherort im Speicher | Element bleibt im ursprünglichen Speicherort im Speicher |
  
Diese Details sollten in Betracht gezogen werden, bei der Implementierung, ziehen der **Projektmappen-Explorer**:  
  
-   Entwerfen Sie für Szenarien mit mehreren Auswahl.  
  
-   Dateinamen (vollständiger Pfad) für das Zielprojekt eindeutig sein müssen, oder der Ablegevorgang nicht zulässig sein soll.  
  
-   Ordner müssen eindeutig sein (Groß-/Kleinschreibung) auf der Ebene, die sie gelöscht wird.  
  
-   Es gibt Unterschiede im Verhalten zwischen Dateien, die zum Zeitpunkt der ziehen Sie (im oben genannten Szenarien nicht aufgeführt) offen oder geschlossen werden.  
  
-   Dateien der obersten Ebene verhält sich etwas anders als Dateien in Ordnern.  
  
Ein weiteres Problem, zu berücksichtigen ist das Durchführen von Move-Vorgänge für Elemente, die geöffneten Designer oder Editoren verfügen. Das erwartete Verhalten ist wie folgt (Dies gilt für alle Projekttypen):  
  
1.  Wenn der Editor/Designer Öffnen keine nicht gespeicherten Änderungen verfügt, sollte der Designer/Editor-Fenster automatisch geschlossen werden.  
  
2.  Wenn der Editor/Designer Öffnen nicht gespeicherte Änderungen verfügt, soll klicken Sie dann die Quelle des Ziehvorgangs Warten der Dropdownliste aus, und klicken Sie dann den Benutzer bitten, die nicht gespeicherte Änderungen in geöffneten Dokumente zu speichern, vor dem Schließen des Fensters mit einer Eingabeaufforderung etwa wie folgt :  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
Dadurch wird dem Benutzer die Möglichkeit, Ihre Arbeit zu speichern, bevor das Ziel auf seine Datenbankkopien ausführt. Eine neue Methode `IVsHierarchyDropDataSource2::OnBeforeDropNotify` aktivieren Sie diese Behandlung hinzugefügt wurde.  
  
Das Ziel kopiert dann den Zustand des Elements, wie es im Speicher ist (einschließlich der nicht gespeicherten Änderungen nicht im Editor aus, wenn der Benutzer **keine**). Nachdem das Ziel der Kopiervorgang abgeschlossen wurde (in `IVsHierarchyDropDataSource::Drop`), die Quelle ist die Möglichkeit gegeben, den löschen-Teil der Verschiebevorgang abgeschlossen (in `IVsHierarchyDropDataSource::OnDropNotify`).  
  
Alle Editoren mit nicht gespeicherten Änderungen sollte geöffnet bleiben. Für diese Dokumente mit ungespeicherten Änderungen bedeutet dies, dass der kopieren-Teil des Verschiebevorgangs wird ausgeführt, aber der Delete-Teil wird abgebrochen. In einem Szenario mit mehreren Auswahl, wenn der Benutzer wählt **keine**, diese Dokumente mit ungespeicherten Änderungen sollten nicht geschlossen oder entfernt werden, aber ohne nicht gespeicherte Änderungen geschlossen und entfernt werden soll.