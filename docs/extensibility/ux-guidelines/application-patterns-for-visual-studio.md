---
title: "Anwendungsmuster f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Anwendungsmuster f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="a-namebkmkwindowinteractionsa-window-interactions"></a><a name="BKMK_WindowInteractions"></a> Fenster Interaktionen  
  
### <a name="overview"></a>Übersicht  
 Die beiden im Hauptfenster in Visual Studio verwendet sind Dokument-Editoren und Toolfenster. Seltene aber möglich, werden große nicht modale Dialogfelder. Obwohl es sich nicht in der Shell alle modalen handelt, sind ihre Muster sich grundlegend. Dieses Thema behandelt die Differenz zwischen dem Dokumentfenster und Toolfenster nicht modale Dialogfelder. Das modale Dialogfeld Muster finden Sie unter [Dialogs](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Vergleichen die Fenster von Verwendungsmustern  
 **Dokumentfenster** werden fast immer angezeigt, in das Dokument auch. Dadurch werden dem Dokument-Editor eine "center Phase", um zusätzliche Tool anordnen.  
  
 Ein **Toolfenster** wird am häufigsten als eine separate, kleinere Fenster, der sichtbar, ausgeblendet oder automatisch ausgeblendet werden kann – für den Rand der IDE reduziert angezeigt. Allerdings manchmal vorgestellt werden innerhalb des Dokuments auch durch Deaktivieren der **Fenster/andocken** Eigenschaft im Fenster. Dies führt zu mehr Platz, aber auch eine gemeinsame entwurfsentscheidung: beim Versuch, die in Visual Studio integrieren, müssen Sie entscheiden, ob die Funktion ein Tool- oder ein Dokumentfenster angezeigt werden soll.  
  
 **Nicht modale Dialogfelder** sollten nicht in Visual Studio. Weitgehend sie sind – definitionsgemäß – Gleitkomma-Toolfenster und daher implementiert werden sollte. Nicht modale Dialogfelder dürfen sich in Fällen, in denen die Größe eines normalen Toolfensters an der Seite der Shell angedockt eingeschränkt werden würde. Sie dürfen auch in Fällen, in denen der Benutzer im Dialogfeld auf einem sekundären Monitor verschieben wahrscheinlich wären.  
  
 Denken Sie an, zu dem Container müssen Sie sorgfältig. Häufige Muster Aspekte bei der Verwendung Design der Benutzeroberfläche sind in der folgenden Tabelle.  
  
||Dokumentfenster|Toolfenster|Nicht-modales Dialogfeld|  
|-|---------------------|-----------------|---------------------|  
|**Position**|Immer auch innerhalb des Dokuments positioniert und ist nicht an den Rändern der IDE andocken. Sie können "herausgezogen werden aus" so, dass Sie es separat von der main-Shell befindet.|Im Allgemeinen als Registerkarte an den Rändern der IDE angedockt, aber kann benutzerdefinierte zu schweben, ausgeblendete (Befestigung) oder auch innerhalb des Dokuments angedockt.|Große schwebenden Fenster getrennt von der IDE.|  
|**Commit-Modell**|*Verzögertes commit*<br /><br /> Um die Daten in einem Dokument zu speichern, muss der Benutzer die Datei/speichern, speichern oder speichern Sie alle-Befehl ausführen. Ein Dokumentfenster mit dem Konzept der die Daten darin wird "verunreinigt" klicken Sie dann auf einen der speichern Commit Befehle. Bei einem Dokumentfenster geschlossen wurde, werden alle Inhalte entweder auf dem Datenträger gespeichert oder nicht mehr.|*Sofortige commit*<br /><br /> Es gibt keine speichern Modell. Inspector-Toolfenster, die bei der Bearbeitung einer Datei, die Datei muss im aktiven Editor bzw. Designer geöffnet sein, und im Editor bzw. Designer besitzt speichern.|*Verzögerte oder sofortige commit*<br /><br /> In den meisten Fällen ein großes nicht-modales Dialogfeld erfordert eine Aktion aus, um die Änderungen zu übernehmen und für einen Vorgang "Abbrechen", der Änderungen in der Dialogfeld-Sitzung ein Rollback ausgeführt.  Dadurch wird ein nicht modales Dialogfeld aus einem Toolfenster, Toolfenster immer eine sofortige Commit-Modell enthalten.|  
|**Sichtbarkeit**|*Öffnen oder erstellen (Datei) und schließen*<br /><br /> Öffnen ein Dokumentfenster erfolgt über ein vorhandenes Dokument öffnen oder Verwenden einer Vorlage zum Erstellen eines neuen Dokuments. Es gibt keine "Open \< bestimmten Editor>" Befehl.|*Anzeigen und ausblenden*<br /><br /> Einzelinstanz-Toolfenster können angezeigt oder ausgeblendet werden. Inhalt und für Zustände innerhalb des Toolfensters beibehalten werden, ob in der Sicht oder ausgeblendet. Toolfenster mit mehreren Instanzen können geschlossen ausgeblendet sowie sein. Wenn ein Toolfenster mit mehreren Instanzen geschlossen wird, wird den Inhalt und den Status innerhalb des Toolfensters verworfen.|*Die von einem Befehl gestartet*<br /><br /> Dialogfelder werden über einen Befehl aufgabenbasierte gestartet.|  
|**Instanzen**|*Mit mehreren Instanzen*<br /><br /> Mehrere Editoren können verschiedene Dateien bearbeiten, und gleichzeitig geöffnet sein, während einige Editoren auch die gleiche Datei in mehrere Editoren geöffnet sein können (mithilfe der **Fenster > Neues Fenster** Befehl).<br /><br /> Ein einzigen Editor möglicherweise eine oder mehrere Dateien gleichzeitig (Projekt-Designer) bearbeiten.|*Einzelne oder mehrere instance*<br /><br /> Inhalt ändern, um Kontext (wie in den Eigenschaftenbrowser) entsprechen oder push Fokus/Kontext zu anderen Fenstern (Aufgabenliste, Projektmappen-Explorer).<br /><br /> Toolfenster Einzel-Instanz und mit mehreren Instanzen sollten das aktive Fenster zugeordnet werden, es sei denn, es ist kein zwingender Grund nicht zu.|*Einzel-Instanz*|  
|**Beispiele für**|**Text-Editoren**, z. B. den Codeeditor<br /><br /> **Entwurfsoberflächen**, z. B. einem Formular-Designer oder Modellierung Fläche<br /><br /> **Steuern des Layouts Dialoge ähnelt**, z. B. die Manifest-Designer|Die **Projektmappen-Explorer** bietet eine Lösung und in der Projektmappe enthaltenen Projekte<br /><br /> Die **Server-Explorer** enthält eine hierarchische Ansicht der Server und Daten Verbindungen, die der Benutzer im Fenster öffnen möchte. Öffnen ein Objekt aus der Datenbank, z. B. eine Abfrage, ein Dokument geöffnet und ermöglicht dem Benutzer beim Bearbeiten der Abfrage.<br /><br /> Die **Eigenschaftenbrowser** zeigt die Eigenschaften für das Objekt entweder in einem Dokument oder eine andere Toolfenster ausgewählt. Die Eigenschaften werden in einer hierarchischen Rasteransicht oder in komplexen wie Dialogfeld-Steuerelementen angezeigt und ermöglichen den Benutzer, die Werte für diese Eigenschaften festzulegen.||  
  
##  <a name="a-namebkmktoolwindowsa-tool-windows"></a><a name="BKMK_ToolWindows"></a> Toolfenster  
  
### <a name="overview"></a>Übersicht  
 Toolfenster unterstützen die Arbeit des Benutzers, der im Dokumentfenster erfolgt. Sie können verwendet werden, um eine Hierarchie anzuzeigen, die eine grundlegende Stammobjekt darstellt, die Visual Studio bereitstellt und können bearbeitet werden.  
  
 Wenn ein neues Toolfenster in der IDE in Erwägung ziehen, sollten die Autoren:  
  
-   Vorhandene Toolfenster Aufgabe geeignete verwenden und keine neue erstellen mit ähnlichen Funktionen. Neue Toolfenster sollten erst erstellt werden, wenn sie bieten eine deutlich andere "Tool" oder Funktionen, die in einem Fenster ähnlich oder aktivieren ein vorhandenes Fenster an einen PivotCharts Hub integriert werden kann.  
  
-   Verwenden Sie eine standard-Befehlsleiste ggf. am oberen Rand des Toolfensters.  
  
-   Mit Mustern, die bereits in anderen Toolfenstern Steuerelement Präsentation und Tastatur Navigation konsistent sein.  
  
-   Steuerelement-Präsentation in anderen Toolfenstern konsistent sein.  
  
-   Für die spezifischen Toolfenster sollte automatisch-möglichst sichtbar, damit sie angezeigt werden, wenn das übergeordnete Dokument aktiviert wird.  
  
-   Sicherstellen Sie, dass ihre Inhalte Fenster über die Tastatur (Unterstützung Pfeiltasten) navigierbar ist.  
  
#### <a name="tool-window-states"></a>Status für Toolfenster  
 Visual Studio-Toolfenster haben unterschiedliche Zustände, von die einige Benutzer (z. B. die Funktion automatisch im Hintergrund) aktiviert sind. Andere Zustände, wie z. B. automatisch angezeigt, können Sie Toolfenster im richtigen Kontext angezeigt und ausgeblendet wird, wenn Sie nicht benötigt. Es gibt fünf Status für Toolfenster insgesamt.  
  
-   **Angedockt bzw. fixierten** Toolfenster können an jeder der vier Seiten des Dokumentbereichs angefügt werden. Das Ortsmarkensymbol sieht in der Titelleiste des Fensters Tool. Das Toolfenster kann horizontal oder vertikal angedockt werden, am Rand der Shell und andere Toolfenster, und Sie können auch Registerkarten verknüpft werden.  
  
-   **Ausgeblendete** Toolfenster gelöst werden. Das Fenster kann nicht zu erkennen, verlassen eine Registerkarte (mit den Namen der Toolfenster und dessen Symbol) am Rand des Dokumentbereichs schieben. Das Toolfenster Folien Wenn ein Benutzer über die Registerkarte bewegt.  
  
-   **Automatische sichtbare** Toolfenster automatisch angezeigt, wenn ein anderes Element der Benutzeroberfläche, z. B. einen Editor gestartet wird oder den Fokus erhält.  
  
-   **Gleitkomma-** Toolfenster außerhalb der IDE zeigen. Dies ist nützlich für Konfigurationen mit mehreren Monitoren.  
  
-   **Dokument im Registerkartenformat** Toolfenster können auch innerhalb des Dokuments angedockt werden. Dies ist nützlich für große Toolfenster, z. B. den Objektkatalog, die mehr Platz als ermöglicht das Andocken an die Ränder des Frames.  
  
 ![Status für Toolfenster in Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")  
  
 **Status für Toolfenster in Visual Studio**  
  
#### <a name="single-instance-and-multi-instance"></a>Einzel-Instanz und mit mehreren Instanzen  
 Toolfenster werden Einzel-Instanz oder mehrere Instanzen. Einige Toolfenster Einzel-Instanz können im aktiven Dokumentfenster zugeordnet werden, während Toolfenster mit mehreren Instanzen nicht können. Toolfenster mit mehreren Instanzen reagieren auf den Befehl Fenster/Neues Fenster durch Erstellen einer neuen Instanz des Fensters. Die folgende Abbildung zeigt ein Toolfenster, aktivieren den Befehl Neues Fenster, wenn eine Instanz des Fensters aktiv ist:  
  
 ![Aktivierungsbefehle für Toolfenster in Visual Studio](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")  
  
 **Toolfenster, die der Befehl "Neues Fenster" aktivieren, wenn eine Instanz des Fensters aktiv ist.**  
  
 Einzelinstanz-Toolfenster können ausgeblendet oder angezeigt werden, während das Toolfenster mit mehreren Instanzen geschlossen und ausgeblendet als werden können. Alle Toolfenster können angedockt, Registerkarten verknüpft, Gleitkomma oder als Multiple Document Interface (MDI) untergeordnetes Fenster (ähnlich wie ein Dokumentfenster) festgelegt werden. Alle Toolfenster sollte auf den entsprechenden Fensterverwaltungsbefehle im Menü Fenster reagieren:  
  
 ![Verwaltungsbefehle für Fenster in Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")  
  
 **Verwaltungsbefehle für Fenster im Menü Visual Studio-Fenster**  
  
#### <a name="document-specific-tool-windows"></a>Für die spezifischen Toolfenster  
 Einige Toolfenster sollen basierend auf einem angegebenen Typ des Dokuments ändern. Diese Fenster aktualisiert ständig Funktion gilt für das aktive Fenster in der IDE widerzuspiegeln.  
  
 Beispiele für Toolfenster, deren Inhalt ändern sich entsprechend der ausgewählten Editor, sind die Toolbox und das Dokumentgliederungsfenster. Diese Fenster anzeigen ein Wasserzeichen aus, wenn ein Editor den Fokus besitzt, die keinen Kontext zum Fenster bereitstellt.  
  
#### <a name="navigable-list-tool-windows"></a>Navigierbare Liste Toolfenster  
 Einige Toolfenster zeigt eine Liste von navigierbaren Elementen, mit der Benutzer interagieren kann. In diesem Fenster sollten immer vorhanden sein Feedback für das aktuelle Element in der Liste, auch wenn das Fenster nicht aktiv ist. Die Liste muss auf reagieren, die **Gehe zu nächster Position** und **GoToPrevLocation** Befehle durch das aktuell ausgewählte Element in das Fenster auch ändern  
  
 Beispiele für Toolfenster navigierbare Liste sind im Projektmappen-Explorer und im Fenster Ergebnisse.  
  
### <a name="tool-window-types"></a>Fenstertypen Tool  
  
#### <a name="common-tool-windows-and-their-functions"></a>Allgemeine Toolfenster und ihre Funktionen  
  
|Typ|Toolfenster|Funktion|  
|----------|-----------------|--------------|  
|**Hierarchie**|Projektmappen-Explorer|Eine hierarchische Struktur, die eine Liste der darin enthaltenen Dokumente in Projekten, verschiedene Dateien und Projektmappen-Elemente anzeigt. Die Anzeige der Elemente in Projekten wird durch das Paket definiert, die den Projekttyp (z. B. anhand von verweisen, Directory-basierte oder gemischte Typen) besitzt.|  
|**Hierarchie**|Klassenansicht|Eine hierarchische Struktur der Klassen und verschiedene Elemente in der Menge an Dokumenten, unabhängig von den Dateien selbst.|  
|**Hierarchie**|Server-Explorer|Eine hierarchische Struktur, in der alle Verbindungen für den Server und Daten in der Projektmappe angezeigt.|  
|**Hierarchie**|Dokumentgliederung|Die hierarchische Struktur des aktiven Dokuments.|  
|**Raster**|Eigenschaften|Ein Raster, in dem eine Liste der Eigenschaften für das ausgewählte Objekt, zusammen mit Wert Bildlaufbereich diese Eigenschaften bearbeiten angezeigt.|  
|**Raster**|Aufgabenliste|Ein Raster, das dem Benutzer, erstellen/bearbeiten/löschen-Vorgänge und Kommentare ermöglicht.|  
|**Inhalt**|Hilfe|Ein Fenster, die Benutzern den Zugriff auf verschiedene Methoden zur Hilfe aus "How Do I?" ermöglicht. Videos zu MSDN-Foren.|  
|**Inhalt**|Dynamische Hilfe|Ein Toolfenster mit Links zu Themen, die für die aktuelle Auswahl zu helfen.|  
|**Inhalt**|Objektkatalog|Frameset zwei Spalten mit einer Liste von hierarchischen Objekt Komponenten im linken Bereich und des Objekts Eigenschaften und Methoden in der rechten Spalte.|  
|**Dialogfeld**|Suchen, die erweiterte Suche|Ein Dialogfeld, in dem der Benutzer suchen oder suchen und Ersetzen Sie in verschiedenen Dateien innerhalb der Projektmappe.|  
|**Andere**|Werkzeugkasten|Das Toolfenster verwendet, um Elemente zu speichern, die auf der Entwurfsoberflächen Bereitstellen einer konsistenten Ziehquelle für alle Designer gelöscht werden.|  
|**Andere**|Startseite|Der Benutzer-Portal zu Visual Studio Zugriff auf Feeds Neuigkeiten für Entwickler, die Visual Studio-Hilfe und die zuletzt geöffnete Projekte. Benutzer können auch benutzerdefinierte Startseiten erstellen kopieren die Datei StartPage.xaml aus Programmverzeichnis "Common7\IDE\StartPages\" Visual Studio in den Ordner StartPages in das Verzeichnis des Visual Studio-Dokumente, und den XAML-CODE durch das manuelle Bearbeiten oder öffnen sie in Visual Studio oder einem anderen Code Editor.|  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Auto||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Direkt||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Ausgabe|Das Ausgabefenster kann verwendet werden, wenn Sie Text Ereignisse oder Status deklariert haben.|  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Arbeitsspeicher||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Haltepunkte||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Wird ausgeführt||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Dokumente||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Aufrufliste||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Locals||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Überwachungselemente||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Disassemblierung||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Register||  
|**Debugger:** einer Gruppe von bestimmten Aufgaben Debuggen und Überwachen von Aktivitäten|Threads||  
  
##  <a name="a-namebkmkdocumenteditorconventionsa-document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Dokumentkonventionen-editor  
  
### <a name="document-interactions"></a>Dokument-Interaktionen  
 "Document gut" ist der größte Bereich in der IDE und, in dem der Benutzer in der Regel ihre Aufmerksamkeit liegt der Schwerpunkt für die Durchführung ihrer Aufgaben von zusätzlichen Toolfenster unterstützt werden. Dokument-Editoren stellen die grundlegenden Arbeitseinheiten, die der Benutzer öffnet und speichert in Visual Studio dar. Behalten sie eine hohe Auswahl im Projektmappen-Explorer oder anderen aktiven Hierarchie Windows gebunden. Der Benutzer sollte in der Lage, zeigen Sie auf einen dieser Hierarchie Windows und wissen, wo das Dokument enthalten ist und die Beziehung auf die Projektmappe, das Projekt oder einem anderen Stammobjekt von einer Visual Studio-Paket bereitgestellt wird.  
  
 Bearbeitung von Dokumenten, erfordert ein konsistentes Erscheinungsbild. Damit den Benutzer auf die jeweilige Aufgabe statt auf Fenster Management und Suche nach Befehlen konzentrieren können, wählen Sie eine Strategie der Dokument-Ansicht, die am besten der Benutzeraufgaben für diesen Dokumenttyp bearbeiten.  
  
#### <a name="common-interactions-for-the-document-well"></a>Allgemeine Aktivitäten für das Dokument auch  
  
-   Verwalten einer konsistenten Interaktionsmodell im allgemeinen **neue Datei** und **geöffnete Datei** auftritt.  
  
-   Aktualisieren Sie verwandten Funktionen in verwandten Fenstern und Menüs, wenn im Dokumentfenster geöffnet.  
  
-   Befehle im Menü entsprechend in integriert sind allgemeine Menüs wie z. B. **Bearbeiten**, **Format**, und **Ansicht** Menüs. Wenn eine beträchtliche Menge an spezielle Befehle verfügbar sind, kann ein neues Menü sichtbar also nur, wenn das Dokument den Fokus besitzt erstellt werden.  
  
-   Am oberen Rand der Editor kann eine eingebettete Symbolleiste platziert werden. Dies empfiehlt sich, dass eine separate Symbolleiste, die außerhalb des Editors angezeigt wird.  
  
-   Stets eine Auswahl im Projektmappen-Explorer oder ähnliche aktive Hierarchiefenster.  
  
-   Durch Doppelklicken auf ein Dokument im Projektmappen-Explorer sollten dieselbe Aktion wie **Öffnen**.  
  
-   Wenn Sie mehrere Editoren für ein Dokument verwendet werden kann, sollte der Benutzer außer Kraft setzen oder Zurücksetzen der Standardaktion für ein bestimmtes Dokument verwenden werden die **Öffnen mit** im Dialogfeld, indem Sie mit der rechten Maustaste auf die Datei und auswählen **Öffnen mit** aus dem Kontextmenü.  
  
-   Erstellen Sie einen Assistenten in einem Dokument auch keine.  
  
### <a name="user-expectations-for-specific-document-types"></a>Benutzererwartungen für bestimmte Dokumenttypen  
 Es gibt verschiedene grundlegende Arten von Dokument-Editoren, und jede hat eine Reihe von Aktivitäten, die konsistent mit anderen vom gleichen Typ sind.  
  
-   **Texteditoren:** Code-Editor, Protokolldateien  
  
-   **Entwurfsoberfläche:** WPF-Forms-Designer, Windows Forms  
  
-   **Dialogfeld-Stil-Editor:** Manifest-Designer-Eigenschaften  
  
-   **Modell-Designer:** Workflow-Designer, Codemap, Architekturdiagramm, Fortschritt  
  
 Es gibt auch mehrere nicht-Editor-Typen, die das Dokument verwenden. Während sie Dokumente selbst bearbeiten, müssen sie Standardinteraktionen für Dokumentfenster durchführen.  
  
-   **Berichte:** IntelliTrace Bericht des Berichts, Hyper-V, Profilerbericht  
  
-   **Dashboard:** Diagnose-Hub  
  
#### <a name="text-based-editors"></a>Textbasierte-Editoren  
  
-   Das Dokument ist Teil in der Vorschau Registerkartenmodell, mit dem für die Vorschau des Dokuments, ohne es zu öffnen.  
  
-   Die Struktur des Dokuments möglicherweise innerhalb eines Toolfensters Companion wie z. B. eine dokumentgliederung dargestellt werden.  
  
-   IntelliSense (falls zutreffend) verhält sich konsistent mit anderen Codeeditoren.  
  
-   Popups oder unterstützende Benutzeroberfläche führen Sie für vorhandene ähnliche Benutzeroberfläche wie z.B. CodeLens ähnliche Formatvorlagen und Muster.  
  
-   Nachrichten zum Dokumentstatus werden in einem Infoleisten-Steuerelement am oberen Rand des Dokuments oder in der Statusleiste angezeigt.  
  
-   Der Benutzer muss in der Lage, Anpassen der Darstellung von Schriftarten und Farben, die mithilfe einer **Tools > Optionen** Seite Freigegebene Seite Schriftarten und Farben oder einer bestimmten im Editor.  
  
#### <a name="design-surfaces"></a>Entwurfsoberflächen  
  
-   Ein leerer Designer müsste ein Wasserzeichen auf der Oberfläche, die angibt, wie für den Einstieg.  
  
-   Wechseln zwischen den Ansichten Mechanismen führen Sie die vorhandenen Muster wie z. B. zum Öffnen von einem Code-Editor und Registerkarten im Dokumentfenster ermöglicht die Interaktion mit beider Bereiche doppelklicken.  
  
-   Hinzufügen von Elementen auf der Entwurfsoberfläche sollten über die Toolbox durchgeführt werden, es sei denn, ein spezifisches Toolfenster erforderlich ist.  
  
-   Elemente auf der Entwurfsoberfläche werden ein Auswahlmodell konsistent folgen.  
  
-   Eingebettete Symbolleisten enthalten jedoch nicht häufig-Befehle für die spezifischen Befehle wie z. B. **Speichern**.  
  
#### <a name="dialog-style-editors"></a>Dialogfeld-Stil-Editor  
  
-   Steuerelementlayout sollten normale Dialogfeld Layoutkonventionen befolgt werden.  
  
-   Registerkarten innerhalb des Editors sollte nicht die Darstellung der Dokumentregisterkarten entsprechen, sollten sie einen der beiden zulässigen inneren Registerkarte Stile übereinstimmen.  
  
-   Benutzer müssen die Steuerelemente mithilfe der Tastatur interagieren können; entweder den Editor aktivieren und TAB-Steuerelemente oder standard Tastenkürzel verwenden.  
  
-   Der Designer sollte die allgemeine Modell speichern verwenden. Auch andere Schaltflächen angemessen sein können, sollte das keine insgesamt speichern oder Commit-Schaltflächen auf der Oberfläche platziert werden.  
  
#### <a name="model-designers"></a>Modell-Designer  
  
-   Ein leerer Designer müsste ein Wasserzeichen auf der Oberfläche, die angibt, wie für den Einstieg.  
  
-   Hinzufügen von Elementen auf der Entwurfsoberfläche sollte über die Toolbox erfolgen.  
  
-   Elemente auf der Entwurfsoberfläche werden ein Auswahlmodell konsistent folgen.  
  
-   Eingebettete Symbolleisten enthalten jedoch nicht häufig-Befehle für die spezifischen Befehle wie z. B. **Speichern**.  
  
-   Auf den ersten Hinweisende oder Wasserzeichen möglicherweise eine Legende angezeigt.  
  
-   Der Benutzer muss in der Lage, Anpassen der Darstellung der Schriftarten/Farben mit einer **Tools > Optionen** Seite Freigegebene Seite Schriftarten und Farben oder einer bestimmten im Editor.  
  
#### <a name="reports"></a>Berichte  
  
-   Berichte werden in der Regel ausschließlich und nicht Teil des Modells speichern. Sie enthalten jedoch möglicherweise Benutzerinteraktion z. B. Links zu anderen relevanten Informationen oder Abschnitte, die erweitert und reduziert werden.  
  
-   Die meisten Befehle auf der Oberfläche sollte nicht die Schaltflächen links.  
  
-   Layout sollten eine Kopfzeile hinzufügen, und befolgen Sie die Richtlinien der Standardbericht Layout.  
  
#### <a name="dashboards"></a>Dashboards  
  
-   Dashboards müssen ein Interaktionsmodell selbst, aber als Mittel zum bieten einer Vielzahl von anderen Tools dienen.  
  
-   Sie das Modell speichern nicht teilnehmen.  
  
-   Benutzer müssen für die Interaktion mit den Steuerelementen, die über Tastatur, aktivieren den Editor und mit der Tabulatortaste Steuerelemente oder standard Tastenkürzel verwenden können.  
  
##  <a name="a-namebkmkdialogsa-dialogs"></a><a name="BKMK_Dialogs"></a> Dialogfelder  
  
### <a name="introduction"></a>Einführung  
 Dialogfelder in Visual Studio unterstützen sollten in der Regel eine einzelne Arbeitseinheit des Benutzers und dann verworfen werden.  
  
 Wenn Sie festgestellt haben, dass Sie ein Dialogfeld benötigen, haben Sie drei Optionen in der Rangordnung:  
  
1.  Die Funktionen in einem der freigegebenen Dialogfelder in Visual Studio integriert.  
  
2.  Erstellen Sie eigene Dialogfeld unter Verwendung eines Musters finden Sie in einen vorhandenen ähnliche Dialog.  
  
3.  Erstellen Sie einen neuen Dialog, folgende Interaktion und Layoutrichtlinien.  
  
 Dieses Thema beschreibt die Vorgehensweise zum Auswählen des richtigen Dialogfeld-Musters in Visual Studio-Workflows und die allgemeinen Konventionen für Dialogfeld-Entwurf.  
  
### <a name="themes"></a>Designs  
 Dialogfelder in Visual Studio führen Sie einen der zwei grundlegende Formate:  
  
#### <a name="standard-unthemed"></a>Standard (Unthemed)  
 Die meisten Dialogfelder werden standard-Dienstprogramm Dialoge und sollte Unthemed sein. Führen Sie nicht die Standardsteuerelemente Re-Vorlage, oder versuchen Sie, stilisierte "modernen" Schaltflächen oder Steuerelemente zu erstellen. Steuerelemente und führen Sie die Chrome-Darstellung [Windows-Desktop Interaktion Standardrichtlinien für die Dialogfelder](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx).  
  
#### <a name="themed"></a>Design  
 Spezialgebiet "Signatur" Dialoge möglicherweise Design. Design Dialogfelder haben eine eigene Darstellung, auch über einige spezielle Interaktion-Muster, das den Stil zugeordnet. Design des Dialogs nur, wenn sie diese Anforderungen erfüllt:  
  
-   Das Dialogfeld ist eine gemeinsame Erfahrung, die erkannt und oft oder von vielen Benutzern verwendet werden (z. B. die **Neues Projekt** Dialogfeld.  
  
-   Das Dialogfeld markanter Produkt Marke Elemente enthält (z. B. die **Konteneinstellungen** Dialogfeld).  
  
-   Das Dialogfeld wird angezeigt, als Bestandteil eines größeren Flusses, die anderen versehene Dialogfelder enthält (z. B. die **verbundenen Dienst hinzufügen** Dialogfeld).  
  
-   Das Dialogfeld ist ein wichtiger Teil eine Erfahrung, die eine strategische Rolle Höherstufen oder Unterscheidung von einer Produktversion spielt.  
  
 Ein Dialogfeld mit Design zu erstellen, verwenden Sie die entsprechende Umgebung Farben und halten Sie das richtige Layout und die Interaktion Muster. (Siehe [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md))  
  
### <a name="dialog-design"></a>Dialogfeld-Entwurf  
 Ausgereifte Dialoge berücksichtigen Sie die folgenden Elemente:  
  
-   Der Task wird unterstützt  
  
-   Das Dialogfeld Textformat, Sprache und Terminologie  
  
-   Auswahl des Steuerelements und UI-Konventionen  
  
-   Das visuelle Layout-Spezifikation und Steuerelement-Ausrichtung  
  
-   Tastaturzugriff  
  
#### <a name="content-organization"></a>Organisation der Inhalte  
 Beachten Sie die Unterschiede zwischen diesen grundlegenden Arten von Dialogfeldern:  
  
-   [Einfache Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) Steuerelemente in einem einzelnen modale Fenster darstellen. Die Präsentation möglicherweise komplexe Steuerelementmuster, einschließlich einer Feldauswahl oder einer Symbolleiste Variationen.  
  
-   [Überlappende Dialoge](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) werden verwendet, um Platz auf dem Bildschirm optimal nutzen, wenn eine einzige Benutzeroberfläche mehrere Gruppen von Steuerelementen umfasst. Im Dialogfeld Gruppen werden über Registerkarten-Steuerelemente, Steuerelemente für die Seitennavigation und Schaltflächen "überlappende" werden, so, dass der Benutzer auswählen kann, welche Gruppe zu einem bestimmten Zeitpunkt finden Sie unter.  
  
-   [Assistenten](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) eignen sich für Benutzer über eine logische Sequenz der Schritte zum Abschließen einer Aufgabe weiterleiten. Eine Reihe von Auswahlmöglichkeiten sequenzielle Panels, manchmal Einführung in anderen Workflows ("Verzweigungen") auf eine Auswahl in der vorherigen Seite bereitgestellt werden.  
  
####  <a name="a-namebkmksimpledialogsa-simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Einfache Dialogfelder  
 Ein einfaches Dialogfeld ist eine Darstellung der Steuerelemente in einem modalen Fenster an. In dieser Präsentation möglicherweise komplexe Steuerelementmuster, z. B. eine Feldauswahl Variationen. Führen Sie für einfache Dialogfelder Standardlayout Allgemein als auch für bestimmte Layouts für komplexe Steuerelement Gruppierungen erforderlich sind.  
  
 ![Einfaches Dialogfeld in Visual Studio](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")  
  
 **Erstellen Sie Schlüssel für einen starken Namen ist ein Beispiel für ein einfaches Dialogfeld in Visual Studio.**  
  
####  <a name="a-namebkmklayereddialogsa-layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Überlappende Dialogfelder  
 Überlappende Dialoge gehören Registerkarten, Dashboards und eingebettete Strukturen. Sie werden verwendet, um Immobilien zu maximieren, wenn mehrere von Steuerelementen, die in eine einzige Benutzeroberfläche angeboten Gruppen. Die Gruppierungen sind überlagernd, damit der Benutzer auswählen kann, die Gruppierung zu einem gegebenen Zeitpunkt angezeigt.  
  
 Im einfachsten Fall ist der Mechanismus zum Wechseln zwischen Gruppen ein Registerkarten-Steuerelement. Mehrere Alternativen stehen zur Verfügung. Finden Sie unter Festlegen der Priorität und Schichten für das am besten geeignete Format auswählen.  
  
 Die **Tools > Optionen** Dialog ist ein Beispiel für ein Dialogfeld mit Ebenen mit einer eingebetteten Struktur:  
  
 ![Dialogfeld mit Ebenen in Visual Studio](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")  
  
 **Extras > Optionen ist ein Beispiel für ein Dialogfeld mit Ebenen in Visual Studio.**  
  
####  <a name="a-namebkmkwizardsa-wizards"></a><a name="BKMK_Wizards"></a> Assistenten  
 Assistenten sind hilfreich für das Weiterleiten von Benutzer über eine logische Sequenz von Schritten in den Abschluss einer Aufgabe. Eine Reihe von Optionen werden in sequenzieller Bereiche angeboten, und der Benutzer muss durch jeden Schritt vor dem Fortfahren mit der nächsten fortfahren. Sobald genügend Standardwerte verfügbar sind, werden die **Fertig stellen** Schaltfläche ist aktiviert.  
  
 Modale Assistenten für Aufgaben verwendet werden, die:  
  
-   Enthalten Sie verzweigen, wobei unterschiedliche Pfade je nach Benutzerauswahl angeboten werden  
  
-   Enthalten Sie Abhängigkeiten zwischen den Schritten, die Benutzereingaben über die vorherigen Schritte, in denen die nachfolgenden Schritte abhängig  
  
-   Sind komplex, dass die Benutzeroberfläche verwendet werden soll, um die Installationsoptionen sowie die möglichen Ergebnisse in jedem Schritt wird erläutert  
  
-   Sind transaktional, erfordern eine Reihe von Schritten vollständig abgeschlossen werden, bevor Änderungen übernommen werden.  
  
### <a name="common-conventions"></a>Allgemeine Konventionen  
 Um den optimalen Entwurf und Funktionalität mit der Dialogfelder zu erzielen, befolgen Sie diese Konventionen Dialogfeldgröße, Position, Standards, steuern die Konfiguration und Ausrichtung, UI Text, Titelleisten, Schaltflächen und Zugriffstasten.  
  
 Layout-spezifische Richtlinien finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Größe  
 Dialoge sollten eine minimale Bildschirmauflösung von 1024 x 768 passen, und anfängliche Dialogfeldgröße darf 900 x 700 Pixel nicht überschreiten. Dialoge können geändert werden, aber es ist nicht erforderlich.  
  
 Es gibt zwei empfohlene für Dialoge mit änderbarer Größe:  
  
1.  Eine minimale Größe für den Dialog definiert, die für die Gruppe Steuerelemente ohne Clipping optimieren und anpassen ist, um sinnvolle Lokalisierung Wachstum.  
  
2.  Dass die Größe skaliert, Benutzer Sitzung beibehalten. Z. B. wenn der Benutzer ein Dialogfeld auf 150 % skaliert, wird einem nachfolgenden Starten des Dialogfelds 150 % angezeigt.  
  
#### <a name="position"></a>Position  
 Dialoge müssen in der IDE beim ersten Starten zentriert angezeigt werden. Für nicht veränderbare Größen Dialoge, es ist nicht erforderlich, dass die letzte Position des Dialogfelds beibehalten werden, damit er auf nachfolgende Aufrufe zentriert angezeigt wird. Für Dialoge mit änderbarer Größe sollte die Größe auf nachfolgende Aufrufe beibehalten werden. Für Dialoge mit änderbarer Größe, die gebunden sind, muss die Position nicht beibehalten werden. Angezeigt werden die in der IDE zentriert wird verhindert, dass das Dialogfeld in einer Position zu unvorhersehbaren oder nicht mehr angezeigt werden, bei der Konfiguration des Benutzers geändert wurde. Für nicht modale Dialogfelder, die neu angeordnet werden können, sollte auf nachfolgende Aufrufe Position des Benutzers verwaltet werden, wie das Dialogfeld häufig als Bestandteil eines größeren Workflows verwendet werden kann.  
  
 Wenn Dialoge anderen Dialogfelder erzeugen müssen, sollte das oberste Dialogfeld kaskadiert werden rechts und nach-unten aus dem übergeordneten Element, sodass diese für den Benutzer offensichtlich ist, die sie an die Stelle navigiert sind.  
  
#### <a name="modality"></a>Modalität  
 Modal wird bedeutet, dass Benutzer abzuschließen, oder das Dialogfeld abbrechen, bevor Sie fortfahren. Da modale Dialogfelder den Benutzer von der Interaktion mit anderen Teilen der Umgebung zu sperren, sollten Sie durch das Feature Aufgabenverlauf so selten wie möglich verwenden werden. Wenn ein modaler Vorgang erforderlich ist, hat Visual Studio eine Anzahl von freigegebenen Dialoge, die Funktionen in integriert werden können. Wenn Sie ein neues Dialogfeld erstellen möchten, folgen Sie Interaktionsmuster für einen vorhandenen Dialog mit ähnlichen Funktionen.  
  
 Wenn Benutzer müssen zwei Aktivitäten auf einmal ausführen, z. B. **Suchen** und **Ersetzen** beim Schreiben von neuem Code, das Dialogfeld sollte nicht modal, damit der Benutzer problemlos zwischen ihnen wechseln kann. Visual Studio verwendet die Toolfenster in der Regel für diese Art von verknüpfte Aufgabe-Editor-Unterstützung.  
  
#### <a name="control-configuration"></a>Konfiguration  
 Seien Sie konsistent mit vorhandenen Konfigurationen, die dasselbe in Visual Studio ausführen.  
  
#### <a name="title-bars"></a>Titelleisten  
  
-   Der Text in der Titelleiste muss den Namen des Befehls widerspiegeln, die das Programm gestartet.  
  
-   Im Dialogfeld Titelleisten sollte kein Symbol verwendet werden. Verwenden Sie in Fällen, in denen das System erfordert das Visual Studio-Logo.  
  
-   Dialoge sollten keine minimieren oder Maximieren Sie Schaltflächen.  
  
-   Hilfe-Schaltflächen in der Titelleiste sind veraltet. Fügen Sie diese nicht auf neue Dialoge. Wenn sie vorhanden sind, sollten sie ein Hilfethema gestartet, im Prinzip für die Aufgabe relevant ist.  
  
 ![Titelleistenspezifikationen für Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")  
  
 **Richtlinie Spezifikationen für Titelleisten in Visual Studio-Dialogfelder.**  
  
#### <a name="control-buttons"></a>Schaltflächen  
 Im allgemeinen **OK**/**Abbrechen**/**Hilfe** Schaltflächen in der unteren rechten Ecke des Dialogfelds horizontal angeordnet werden soll. Die alternative vertikale Stapel ist zulässig, wenn ein Dialogfeld mehrere andere Schaltflächen am unteren Rand des Dialogfelds verfügt, die visual Verwechslungen mit den Schaltflächen des Steuerelements darstellen würde.  
  
 ![Konfigurationen für Steuerelementschaltflächen in Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")  
  
 **Akzeptable Konfigurationen für Steuerelementschaltflächen in Visual Studio-Dialogfelder**  
  
 Das Dialogfeld muss es sich um eine Standardschaltfläche für das Steuerelement enthalten. So bestimmen Sie den besten Befehl als Standard verwenden, wählen aus den folgenden Optionen (aufgeführt in der Rangfolge):  
  
-   Wählen Sie den sichersten und sicherste-Befehl als Standard. Dies bedeutet wahrscheinlich zu Vermeidung von Datenverlusten unbeabsichtigten Zugriff auswählen.  
  
-   Wenn Daten verloren gehen und Sicherheit Faktoren sind, wählen Sie dann den Standardbefehl basierend auf der Einfachheit halber. Die wahrscheinlichste-Befehl als Standard steigert den Workflow des Benutzers, wenn das Dialogfeld häufige oder sich wiederholende Aufgaben unterstützt.  
  
 Vermeiden Sie die Auswahl einer dauerhaft destruktiven Aktion für den Standardbefehl. Wenn ein Befehl vorhanden ist, wählen Sie stattdessen einen sichereren Befehl als Standard.  
  
#### <a name="access-keys"></a>Zugriffstasten  
 Verwenden Sie keine Zugriffstasten für **OK**/**Abbrechen**/**Hilfe** Schaltflächen. Diese Schaltflächen sind standardmäßig Tastenkombinationen zugeordnet:  
  
|Name der Schaltfläche|Tastenkombination|  
|-----------------|-----------------------|  
|OK|Eingabe|  
|Abbrechen|Esc|  
|Hilfe|F1|  
  
#### <a name="imagery"></a>Bilder  
 Verwenden Sie Bilder sparsam in Dialogfeldern. Verwenden Sie die große Symbole nicht in Dialogfeldern, lediglich, um Speicherplatz zu verwenden. Verwenden Sie Bilder nur, wenn sie ein wichtiger Bestandteil der Meldung für den Benutzer, z. B. ein Warnsymbol oder Status Animationen vermittelt werden.  
  
###  <a name="a-namebkmkprioritizingandlayeringa-prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Festlegen der Priorität und Ebenen  
  
#### <a name="prioritizing-your-ui"></a>Priorisieren die Benutzeroberfläche  
 Es kann erforderlich sein, bestimmte Elemente der Benutzeroberfläche zu bringen und erweiterte Verhalten und Optionen (einschließlich undurchsichtig Befehle) in Dialogfeldern. Bringen Sie häufig verwendete Funktionen zu, indem des Arbeitsbereichs dafür, und es sichtbar standardmäßig in der Benutzeroberfläche mit einer Beschriftung, wenn das Dialogfeld angezeigt wird.  
  
#### <a name="layering-your-ui"></a>Schichten von der Benutzeroberfläche  
 Wenn Sie festgestellt haben, dass ein Dialogfeld erforderlich ist, aber die zugehörige Funktionen, die dem Benutzer angezeigt werden sollen nicht ausreichend, was in ein einfaches Dialogfeld angezeigt werden kann, müssen Sie die UI-Ebene. Die am häufigsten verwendeten Ebenen-Methoden, die Visual Studio verwendet werden, Registerkarten und Fluren oder Dashboards. In einigen Fällen möglicherweise entsprechenden Bereiche, die erweitern und reduzieren können. Adaptive Benutzeroberfläche wird in Visual Studio im Allgemeinen nicht empfohlen.  
  
 Es gibt vor- und Nachteile zu den verschiedenen Methoden der Benutzeroberfläche über die Registerkarte Steuerelemente überlagern. Überprüfen Sie die Liste unten, um sicherzustellen, dass Sie eine Technik, die Ebenen auswählen, die für Ihre Situation geeignet ist.  
  
##### <a name="tabbing"></a>Tabulator  
  
|Switching-Mechanismus|Vor- und angemessene Verwendung|Nachteile und unangemessene Verwendung|  
|-------------------------|------------------------------------|-----------------------------------------|  
|Registersteuerelement|Dialogfelder in verwandte logisch gruppieren<br /><br /> Hilfreich für weniger als fünf (oder die Anzahl der Registerkarten, die über das Dialogfeld in eine Zeile passen) Seiten von verwandten Steuerelementen im Dialogfeld<br /><br /> Registerkartenbezeichnungen müssen kurz sein: ein oder zwei Wörter, die schnell den Inhalt<br /><br /> System Dialogfeld Format<br /><br /> Beispiel: **Datei-Explorer > Element**|Beschreibende kurze Bezeichnungen kann schwierig sein<br /><br /> Im Allgemeinen erweitern nicht über fünf Registerkarten in einem Dialogfeld<br /><br /> Ungeeignet, wenn zu viele Registerkarten für eine Zeile sind; Verwenden Sie eine alternative Überlagerung-Technik<br /><br /> Nicht erweiterbare|  
|Seitenleistennavigation|Einfache switching-Gerät, das weitere Kategorien als Registerkarten aufnehmen kann<br /><br /> Flache Liste mit Kategorien (ohne Hierarchie)<br /><br /> Erweiterbar<br /><br /> Beispiel: **anpassen... > Befehl hinzufügen**|Keine gute Verwendung für horizontalen Bereich, wenn es weniger als drei Gruppen<br /><br /> Aufgabe möglicherweise besser geeignet, um eine Dropdown-Liste|  
|Struktursteuerelement|Ermöglicht unbegrenzte Anzahl an Kategorien<br /><br /> Ermöglicht die Gruppierung und/oder die Hierarchie von Kategorien<br /><br /> Erweiterbar<br /><br /> Beispiel: **Tools > Optionen**|Stark geschachtelte Hierarchien kann eine übermäßige horizontalen Bildlauf<br /><br /> Visual Studio verfügt über eine Overabundance von Strukturansichten|  
|Assistent|Unterstützt die Ausführung der Aufgabe angeleitet durch aufgabenbasierte, aufeinander folgende Schritte. Der Assistent stellt eine übergeordnete Aufgabe, und die einzelnen Bereiche darstellen Unteraufgaben, die für die gesamte Aufgabe benötigt.<br /><br /> Nützlich, wenn der Task Ui-Grenzen schneidet, als wenn der Benutzer andernfalls müssten verwenden Sie mehrere Editoren und Toolfenster, um den Vorgang abzuschließen<br /><br /> Nützlich, wenn der Task das Verzweigen erfordert<br /><br /> Nützlich, wenn die Aufgabe Abhängigkeiten zwischen den einzelnen Schritten enthält.<br /><br /> Nützlich, wenn mehrere ähnliche Aufgaben mit einer Entscheidung Verzweigung in ein Dialogfeld zum Reduzieren der Anzahl der verschiedenen ähnliche Dialogfelder angezeigt werden können.|Für jede Aufgabe, die kein sequenziellen Workflows erforderlich ist<br /><br /> Benutzer können Sie meinen und von einem Assistenten durch zu viele Schritte verwechselt werden.<br /><br /> Assistenten haben grundsätzlich Bildschirmfläche beschränkt.|  
  
##### <a name="hallways-or-dashboards"></a>Fluren oder dashboards  
 Fluren und Dashboards sind Dialogfelder oder Bereiche, die als starten verweist auf den anderen Dialogfeldern und Fenstern dienen. Ausgereifte "Gang" Flächen sofort nur die am häufigsten verwendeten Optionen, Befehle und Einstellungen, sodass der Benutzer leicht häufige Aufgaben. Wie eine reale Gang Doorways für den Zugriff auf die Räume dahinter bereitstellt, gesammelt hier die Benutzeroberfläche weniger übliche in separaten "Räume" (häufig andere Dialogfelder) Funktionen, die von den wichtigsten Gang zugegriffen werden kann.  
  
 Sie können auch eine Benutzeroberfläche, die alle verfügbaren Funktionen in einer einzelnen Auflistung bietet, statt die weniger übliche Funktionalität in separaten Speicherorten Umgestaltung einfach ein Dashboard.  
  
 ![Hallway-Konzept in Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")  
  
 **Hallway-Konzept zum Verfügbarmachen von zusätzlichen UI in Outlook**  
  
##### <a name="adaptive-ui"></a>Adaptive Benutzeroberfläche  
 Ein- oder Ausblenden der Benutzeroberfläche basierend auf Ihrer Verwendung oder eine Self-gemeldeten Benutzerfunktionalität ist eine weitere Möglichkeit zur Darstellung der benötigten Benutzeroberfläche und gleichzeitig andere Teile von. Dies wird in Visual Studio, nicht empfohlen, die Algorithmen für die Entscheidung, wann ein- oder Ausblenden der Benutzeroberfläche können schwierig sein, und die Regeln werden immer falsch für eine Gruppe von Fällen.  
  
##  <a name="a-namebkmkprojectsa-projects"></a><a name="BKMK_Projects"></a> Projekte  
  
### <a name="projects-in-the-solution-explorer"></a>Projekte im Projektmappen-Explorer  
 Die meisten Projekte werden als anhand von verweisen, Directory-basierte oder gemischten klassifiziert. Alle drei Typen von Projekten werden im Projektmappen-Explorer gleichzeitig unterstützt. Der Stamm des Benutzererlebnisses bei der Arbeit mit Projekten findet innerhalb dieses Fensters. Anderes Projektknoten Verweis, Verzeichnis oder Projekten im gemischten Modus Typ sind, ist ein allgemeines Interaktionsmuster, das als Ausgangspunkt angewendet werden soll, bevor Sie in projektspezifische Benutzermuster gehen auseinander.  
  
 Es muss immer Projekte:  
  
-   Unterstützen Sie die Möglichkeit, Projektordner zum Organisieren von Inhalt von Projekten hinzufügen  
  
-   Verwalten eines konsistenten Modells zum Projekt Persistenz  
  
 Projekte sollten konsistent interaktionsmodelle für auch beibehalten werden:  
  
-   Entfernen von Projektelementen  
  
-   Speichern von Dokumenten  
  
-   Projekt Eigenschaft bearbeiten  
  
-   Bearbeiten das Projekt in einer alternativen Ansicht  
  
-   Drag & Drop-Operationen  
  
### <a name="drag-and-drop-interaction-model"></a>Drag & Drop-Interaktion  
 Projekte klassifizieren selbst als anhand von verweisen (nur Verweise auf Projektelemente im Speicher beibehalten werden können), in der Regel verzeichnisbasierte (können nur Projektelemente physisch dauerhaft gespeichert innerhalb eines Projekts Hierarchie), oder gemischt (Verweise oder physischen Elementen beibehalten werden können). Die IDE unterstützt alle drei Typen von Projekten gleichzeitig innerhalb der **Projektmappen-Explorer**.  
  
 Hinsichtlich der Drag & Drop-die folgenden Merkmale treffen sollte, mit jeder Art von Projekt innerhalb der **Projektmappen-Explorer**:  
  
-   **Referenz-basiertes Projekt:** Der Kernpunkt ist, dass das Projekt um einen Verweis auf ein Element im Speicher zieht. Wenn ein Verweis-basiertes Projekt als Quelle für einen Verschiebevorgang fungiert, sollte es nur den Verweis auf das Element aus dem Projekt entfernen. Das Element sollte nicht tatsächlich von der Festplatte gelöscht werden. Wenn ein Referenz-basiertes Projekt als Ziel für einen Vorgang verschieben (oder kopieren) fungiert, sollten sie einen Verweis auf das ursprüngliche Quellelement hinzufügen, ohne dass eine private Kopie des Elements.  
  
-   **Directory-basiertes Projekt:** aus Sicht einer Drag & Drop ist das Projekt um physikalisches Element anstelle eines Verweises ziehen. Wenn ein Verzeichnis-basiertes Projekt als Quelle für einen Verschiebevorgang fungiert, sollte es am Ende das Löschen der physischen Elements von der Festplatte als auch aus dem Projekt entfernt. Wenn ein Verzeichnis-basiertes Projekt als Ziel für einen Vorgang verschieben (oder kopieren) fungiert, sollte eine Kopie des Quellelements in den Zielspeicherort zu vereinfachen.  
  
-   **Gemischte Zielprojekt:** aus einer Drag & Drop-Sicht, das Verhalten dieser Art von Projekt ist aufgrund der Natur des Elements (ein Verweis auf ein Element im Speicher) oder das Element selbst gezogen wird. Das richtige Verhalten für Verweise und physischen Elemente werden oben beschrieben.  
  
 Wenn gab es nur eine Art von Projekt in der **Projektmappen-Explorer**, Drag & Drop-Vorgänge einfach sein würde. Weil jedes Projektsystem die Möglichkeit, eigene Drag & Drop-Verhalten zu definieren, sollten bestimmte Richtlinien (basierend auf dem Windows-Explorer Drag & Drop-Verhalten) eingehalten werden, um eine vorhersagbare Benutzerfunktionalität zu gewährleisten:  
  
-   Eine unveränderte ziehen Sie die Operation in der **Projektmappen-Explorer** (Wenn weder STRG oder UMSCHALT-Tasten gedrückt werden) führt zum Verschieben.  
  
-   Ziehen bei gedrückter Umschalttaste Vorgang sollte auch in einem Verschiebevorgang führen.  
  
-   STRG + Ziehen Vorgang sollte einen Kopiervorgang führen.  
  
-   Anhand von verweisen und gemischten Projektsysteme unterstützen das Konzept hinzufügen einen Link (oder ein Verweis) auf das Quellelement. Wenn diese Projekte sind das Ziel eines Drag & Drop-Vorgangs (Wenn **STRG + UMSCHALT** gedrückt gehalten wird), er führt einen Verweis auf das Element zum Projekt hinzugefügt wird  
  
 Nicht alle Drag & Drop-Vorgänge sind für Kombinationen von Verweis, Verzeichnis und gemischte Projekte. Insbesondere ist es problematisch, vorzugeben, um einen Move-Vorgang zwischen einem verzeichnisbasierte Quellprojekt und verweisbasierte Zielprojekt zu ermöglichen, da das Quellprojekt verzeichnisbasierte auf das Quellelement nach Abschluss der Verschiebung zu löschen. Das Zielprojekt anhand von Verweisen würde dann einen Verweis auf ein gelöschtes Element am Ende angezeigt.  
  
 Es ist ebenfalls irreführend, um einen Kopiervorgang zwischen diesen Typen von Projekten zu ermöglichen, da das Zielprojekt anhand von Verweisen eine unabhängige Kopie des Quellelements machen sollten, vorzugeben. Auf ähnliche Weise sollte STRG + UMSCHALT, die in einem Directory-basierte Zielprojekt ziehen nicht zugelassen werden, da ein Verzeichnis-basiertes Projekt Verweise beibehalten werden kann. In Fällen, in denen die Drag & Drop-Vorgang wird nicht unterstützt, sollte die IDE unterbinden die Dropdownliste und dem Benutzer keine Ablage Cursor (in der folgenden Tabelle dargestellt).  
  
 Um Drag & Drop-Verhalten ordnungsgemäß zu implementieren, das Quellprojekt des Ziehvorgangs seiner Natur kommunizieren muss (z. B. ist es Verweis oder verzeichnisbasierte?) für das Zielprojekt. Diese Informationen wird durch das Zwischenablageformat angezeigt, die von der Quelle bereitgestellt wird. Als Quelle eines Drag (oder Kopiervorgang Zwischenablage) ein Projekt bieten entweder **CF_VSREFPROJECTITEM**S oder **CF_VSSTGPROJECTITEMS** je nachdem, ob das Projekt anhand von verweisen oder verzeichnisbasierten. Beide Formate haben den gleichen Dateninhalt, die mit Windows **CF_HDROP** formatieren, nur sind Zeichenfolgenlisten, anstatt Sie Dateinamen, Double -**NULL** beendet die Liste der **Projref** Zeichenfolgen (der von zurückgegebene **IVsSolution::GetProjrefOfItem** oder **:: GetProjrefOfProject** nach Bedarf).  
  
 Als Ziel eines Drop (oder Zwischenablagevorgang einfügen), sollte ein Projekt akzeptieren beide **CF_VSREFPROJECTITEMS** und **CF_VSSTGPROJECTITEMS**, jedoch je nach Art des Zielprojekts und das Source-Projekt die genaue Behandlung des Drag & Drop-Vorgangs variiert. Das Quellprojekt deklariert sind ihrem Wesen nach, ob es bietet **CF_VSREFPROJECTITEMS** oder **CF_VSSTGPROJECTITEMS**. Das Ziel des Ablegevorgangs eigene Art versteht und daher hat genügend Informationen, ob eine Move, Copy und Entscheidungen oder Link ausgeführt werden soll. Der Benutzer ändert auch die Drag & Drop-Vorgang ausgeführt werden soll, durch Drücken der STRG, UMSCHALT oder STRG und UMSCHALT-Tasten. Es ist wichtig für das Ablageziel an ordnungsgemäß im Voraus in welchen Vorgang durchgeführt wird seine **DragEnter** und **DragOver** Methoden. Die **Projektmappen-Explorer** automatisch weiß, ob die Quelle und dem Zielprojekt desselben Projekts sind.  
  
 Ziehen Projektelemente für Instanzen von Visual Studio (z. B. von einer Instanz von devenv.exe zu einem anderen) wird ausdrücklich nicht unterstützt. Die **Projektmappen-Explorer** auch direkt wird deaktiviert.  
  
 Der Benutzer sollte immer möglich die Auswirkung eines Drag & Drop-Vorgangs durch Auswählen eines Elements, ziehen es an den Zielort und beobachten, die die folgenden Mauszeiger angezeigt wird, bevor das Element gelöscht wird:  
  
|Mauszeiger|Befehl|Beschreibung|  
|-------------------|-------------|-----------------|  
|![Symbol „Keine Ablage“ für Maus](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop")|Keine Ablage|Element kann nicht am angegebenen Speicherort abgelegt werden.|  
|![Symbol "Kopieren" für Maus](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy")|Kopieren|Element wird an den Zielspeicherort kopiert werden.|  
|![Symbol "Verschieben" für Maus](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove")|Verschieben|Element wird an den Zielspeicherort verschoben werden.|  
|![Symbol "Verweis hinzufügen" für Maus](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef")|Verweis hinzufügen|Ein Verweis auf das ausgewählte Element wird an den Zielort hinzugefügt werden.|  
  
#### <a name="reference-based-projects"></a>Verweisbasierte Projekte  
 Die folgende Tabelle fasst die Drag & Drop (sowie Ausschneiden/Kopieren/Einfügen) Vorgänge, die ausgeführt werden sollte basierend auf der Art des Elements und der Modifizierer Quellschlüssel gedrückt für verwiesen-basierte Zielprojekte:  
  
|||Das Quellelement: Verweislink /|Das Quellelement: physische Artikel oder Dateisystem (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Kein Modifizierer|Aktion|Verschieben|Link|  
|Kein Modifizierer|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Verweis auf das ursprüngliche Element hinzugefügt|  
|Kein Modifizierer|Quelle|Löscht Verweis zum ursprünglichen Element|Behält die ursprünglichen Element|  
|Kein Modifizierer|Ergebnis|**Den Wert DROPEFFECT_MOVE** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|**DROPEFFECT_LINK** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|  
|Umschalt + Ziehen|Aktion|Verschieben|Keine Ablage|  
|Umschalt + Ziehen|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Keine Ablage|  
|Umschalt + Ziehen|Quelle|Löscht Verweis zum ursprünglichen Element|Keine Ablage|  
|Umschalt + Ziehen|Ergebnis|**Den Wert DROPEFFECT_MOVE** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|Keine Ablage|  
|STRG + Ziehen|Aktion|Kopieren|Keine Ablage|  
|STRG + Ziehen|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Keine Ablage|  
|STRG + Ziehen|Quelle|Verweis auf das ursprüngliche Element beibehalten|Keine Ablage|  
|STRG + Ziehen|Ergebnis|**DROPEFFECT_COPY** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|Keine Ablage|  
|STRG + UMSCHALT + ziehen|Aktion|Link|Link|  
|STRG + UMSCHALT + ziehen|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Verweis auf das ursprüngliche Element hinzugefügt|  
|STRG + UMSCHALT + ziehen|Quelle|Verweis auf das ursprüngliche Element beibehalten|Behält die ursprünglichen Element|  
|STRG + UMSCHALT + ziehen|Ergebnis|**DROPEFFECT_LINK** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|**DROPEFFECT_LINK** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|  
|STRG + UMSCHALT + ziehen|Hinweis|Identisch mit Drag & Drop-Verhalten für Tastenkombinationen in Windows-Explorer.||  
|Ausschneiden und einfügen|Aktion|Verschieben|Link|  
|Ausschneiden und einfügen|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Verweis auf das ursprüngliche Element hinzugefügt|  
|Ausschneiden und einfügen|Quelle|Verweis auf das ursprüngliche Element beibehalten|Behält die ursprünglichen Element|  
|Ausschneiden und einfügen|Ergebnis|Element bleibt im ursprünglichen Speicherort|Element bleibt im ursprünglichen Speicherort|  
|Kopieren und einfügen|Aktion|Kopieren|Link|  
|Kopieren und einfügen|Quelle|Verweis auf das ursprüngliche Element hinzugefügt|Verweis auf das ursprüngliche Element hinzugefügt|  
|Kopieren und einfügen|Ergebnis|Verweis auf das ursprüngliche Element beibehalten|Behält die ursprünglichen Element|  
|Kopieren und einfügen|Aktion|Element bleibt im ursprünglichen Speicherort|Element bleibt im ursprünglichen Speicherort|  
  
#### <a name="directory-based-projects"></a>Verzeichnisbasierte Projekte  
 Die folgende Tabelle fasst die Drag & Drop (sowie Ausschneiden/Kopieren/Einfügen) Vorgänge, die ausgeführt werden sollte basierend auf der Art des Elements und der Modifizierer Quellschlüssel für verzeichnisbasierte Zielprojekte gedrückt:  
  
|||Das Quellelement: Verweislink /|Das Quellelement: physische Artikel oder Dateisystem (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Kein Modifizierer|Aktion|Verschieben|Verschieben|  
|Kein Modifizierer|Ziel|Kopien Element Zielspeicherort|Kopien Element Zielspeicherort|  
|Kein Modifizierer|Quelle|Löscht Verweis zum ursprünglichen Element|Löscht Verweis zum ursprünglichen Element|  
|Kein Modifizierer|Ergebnis|**VERSCHIEBEN von DROPEFFECT_** wird als Aktion zurückgegeben **:: Löschen** und Element bleibt im ursprünglichen Speicherort|**VERSCHIEBEN von DROPEFFECT_** wird als Aktion zurückgegeben **:: Löschen** und Element bleibt im ursprünglichen Speicherort|  
|Umschalt + Ziehen|Aktion|Verschieben|Verschieben|  
|Umschalt + Ziehen|Ziel|Kopien Element Zielspeicherort|Kopien Element Zielspeicherort|  
|Umschalt + Ziehen|Quelle|Löscht Verweis zum ursprünglichen Element|Löscht Element aus dem ursprünglichen Speicherort|  
|Umschalt + Ziehen|Ergebnis|**VERSCHIEBEN von DROPEFFECT_** wird als Aktion zurückgegeben **:: Löschen** und Element bleibt im ursprünglichen Speicherort|**VERSCHIEBEN von DROPEFFECT_** wird als Aktion zurückgegeben **:: Löschen** und Element bleibt im ursprünglichen Speicherort|  
|STRG + Ziehen|Aktion|Kopieren|Kopieren|  
|STRG + Ziehen|Ziel|Kopien Element Zielspeicherort|Kopien Element Zielspeicherort|  
|STRG + Ziehen|Quelle|Verweis auf das ursprüngliche Element beibehalten|Verweis auf das ursprüngliche Element beibehalten|  
|STRG + Ziehen|Ergebnis|**DROPEFFECT_ KOPIEREN** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|**DROPEFFECT_ KOPIEREN** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|  
|STRG + UMSCHALT + ziehen||Keine Ablage|Keine Ablage|  
|Ausschneiden und einfügen|Aktion|Verschieben|Verschieben|  
|Ausschneiden und einfügen|Ziel|Kopien Element Zielspeicherort|Kopien Element Zielspeicherort|  
|Ausschneiden und einfügen|Quelle|Löscht Verweis zum ursprünglichen Element|Löscht Element aus dem ursprünglichen Speicherort|  
|Ausschneiden und einfügen|Ergebnis|Element bleibt im ursprünglichen Speicherort|Element wird vom ursprünglichen Speicherort gelöscht.|  
|Kopieren und einfügen|Aktion|Kopieren|Kopieren|  
|Kopieren und einfügen|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Kopien Element Zielspeicherort|  
|Kopieren und einfügen|Quelle|Behält die ursprünglichen Element|Behält die ursprünglichen Element|  
|Kopieren und einfügen|Ergebnis|Element bleibt im ursprünglichen Speicherort|Bleibt im ursprünglichen Speicherort ins Speicher|  
  
#### <a name="mixed-target-projects"></a>Gemischte Zielprojekte  
 In der folgenden Tabelle sind die Drag & Drop (sowie Ausschneiden/Kopieren/Einfügen) Vorgänge, die ausgeführt werden soll basierend auf der Art des Elements und der Modifizierer Quellschlüssel gedrückt für gemischte Zielprojekte zusammengefasst:  
  
|||Das Quellelement: Verweislink /|Das Quellelement: physische Artikel oder Dateisystem (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Kein Modifizierer|Aktion|Verschieben|Verschieben|  
|Kein Modifizierer|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Kopien Element Zielspeicherort|  
|Kein Modifizierer|Quelle|Löscht Verweis zum ursprünglichen Element|Löscht Verweis zum ursprünglichen Element|  
|Kein Modifizierer|Ergebnis|**VERSCHIEBEN von DROPEFFECT_** wird als Aktion zurückgegeben **:: Löschen** und Element bleibt im ursprünglichen Speicherort|**VERSCHIEBEN von DROPEFFECT_** wird als Aktion zurückgegeben **:: Löschen** und Element vom ursprünglichen Speicherort gelöscht|  
|Umschalt + Ziehen|Aktion|Verschieben|Verschieben|  
|Umschalt + Ziehen|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Kopien Element Zielspeicherort|  
|Umschalt + Ziehen|Quelle|Löscht Verweis zum ursprünglichen Element|Löscht Element aus dem ursprünglichen Speicherort|  
|Umschalt + Ziehen|Ergebnis|**VERSCHIEBEN von DROPEFFECT_** wird als Aktion zurückgegeben **:: Löschen** und Element bleibt im ursprünglichen Speicherort|**VERSCHIEBEN von DROPEFFECT_** wird als Aktion zurückgegeben **:: Löschen** und Element vom ursprünglichen Speicherort gelöscht|  
|STRG + Ziehen|Aktion|Kopieren|Kopieren|  
|STRG + Ziehen|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Kopien Element Zielspeicherort|  
|STRG + Ziehen|Quelle|Verweis auf das ursprüngliche Element beibehalten|Behält die ursprünglichen Element|  
|STRG + Ziehen|Ergebnis|**DROPEFFECT_ KOPIEREN** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|**DROPEFFECT_ KOPIEREN** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|  
|STRG + UMSCHALT + ziehen|Aktion|Link|Link|  
|STRG + UMSCHALT + ziehen|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Verweis auf den ursprünglichen Quellelement hinzugefügt|  
|STRG + UMSCHALT + ziehen|Quelle|Verweis auf das ursprüngliche Element beibehalten|Behält die ursprünglichen Element|  
|STRG + UMSCHALT + ziehen|Ergebnis|**DROPEFFECT_ LINK** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|**DROPEFFECT_ LINK** wird als Aktion zurückgegeben **:: Drop** und Element bleibt im ursprünglichen Speicherort|  
|Ausschneiden und einfügen|Aktion|Verschieben|Verschieben|  
|Ausschneiden und einfügen|Ziel|Kopien Element Zielspeicherort|Kopien Element Zielspeicherort|  
|Ausschneiden und einfügen|Quelle|Löscht Verweis zum ursprünglichen Element|Löscht Element aus dem ursprünglichen Speicherort|  
|Ausschneiden und einfügen|Ergebnis|Element bleibt im ursprünglichen Speicherort|Element wird vom ursprünglichen Speicherort gelöscht.|  
|Kopieren und einfügen|Aktion|Kopieren|Kopieren|  
|Kopieren und einfügen|Ziel|Verweis auf das ursprüngliche Element hinzugefügt|Kopien Element Zielspeicherort|  
|Kopieren und einfügen|Quelle|Behält die ursprünglichen Element|Behält die ursprünglichen Element|  
|Kopieren und einfügen|Ergebnis|Element bleibt im ursprünglichen Speicherort|Element bleibt im ursprünglichen Speicherort|  
  
 Diese Informationen sollten in Betracht gezogen werden, bei der Implementierung, ziehen der **Projektmappen-Explorer**:  
  
-   Entwerfen Sie für Szenarien mit mehreren Auswahl.  
  
-   Dateinamen (vollständiger Pfad) für das Zielprojekt eindeutig sein müssen oder die Drop nicht zulässig.  
  
-   Namen müssen eindeutig sein (Groß-/Kleinschreibung) auf der Ebene sind diese gelöscht wird.  
  
-   Es gibt Unterschiede im Verhalten zwischen Dateien, die zum Zeitpunkt der ziehen (nicht in der oben genannten Szenarios erwähnt) offen oder geschlossen sind.  
  
-   Dateien der obersten Ebene Verhalten geringfügig anders, als Dateien in Ordnern.  
  
 Ein weiteres Problem, zu berücksichtigen ist Verschiebevorgänge für Elemente zu behandeln, die geöffneten Designer und Editoren arbeiten. Das erwartete Verhalten ist wie folgt (Dies gilt für alle Projekttypen):  
  
1.  Verfügt der open-Editor-Designer keine nicht gespeicherten Änderungen, sollte das Editor-Designer-Fenster automatisch geschlossen werden.  
  
2.  Wenn die open-Editor-Designer nicht gespeicherte Änderungen verfügt, sollte die Quelle des Ziehvorgangs warten, für die Dropdownliste, und klicken Sie dann den Benutzer bitten, die Änderungen in der geöffneten Dokumente speichern, vor dem Schließen des Fensters mit einer Aufforderung angezeigt, die etwa wie folgt:  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
 Dies ermöglicht dem Benutzer die Möglichkeit, Ihre Arbeit zu speichern, bevor das Ziel der kopiert wird. Eine neue Methode **IVsHierarchyDropDataSource2::OnBeforeDropNotify** Aktivieren dieser Behandlung hinzugefügt wurde.  
  
 Das Ziel kopiert anschließend den Zustand des Elements, wie im Speicher (einschließlich nicht nicht gespeicherten Änderungen im Editor ein, wenn der Benutzer **keine**). Nachdem das Ziel der Kopiervorgang abgeschlossen wurde (in **IVsHierarchyDropDataSource::Drop**), die Quelle ist die Möglichkeit gegeben, die löschen-Teil der Verschiebevorgang abgeschlossen (im **IVsHierarchyDropDataSource::OnDropNotify**).  
  
 Alle Editoren mit nicht gespeicherten Änderungen sollte geöffnet bleiben. Für diese Dokumente mit nicht gespeicherten Änderungen bedeutet dies, dass der Kopiervorgang für den Verschiebevorgang erfolgt jedoch Bereich löschen wird abgebrochen. In einem Szenario mit mehreren Auswahl, wenn der Benutzer **keine**, diese Dokumente mit nicht gespeicherten Änderungen nicht geschlossen oder entfernt, jedoch ohne ungespeicherte Änderungen geschlossen und entfernt werden soll.