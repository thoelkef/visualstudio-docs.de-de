---
title: "Exemplarische Vorgehensweise: Ver&#246;ffentlichen einer Projektvorlage f&#252;r Websteuerelemente | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vorlagen, Websteuerelemente"
  - "Websteuerelementvorlagen"
ms.assetid: b56490f8-38bd-4220-a17e-5ebb30d3ac78
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# Exemplarische Vorgehensweise: Ver&#246;ffentlichen einer Projektvorlage f&#252;r Websteuerelemente
Sie können eine Projektvorlage für Websteuerelemente als Basis für andere Websteuerelement\-Projekte verwenden. Sie können die Vorlage auch als VSIX\-Erweiterung verteilen.  
  
 Um eine VSIX\-Erweiterung zu verteilen, fügen Sie diese am besten auf der Visual Studio Gallery\-Website hinzu, da Entwickler mit dem Erweiterungs\-Manager dort nach neuen und aktualisierten Erweiterungen suchen können. Sie können eine Erweiterung auch verteilen, indem Sie diese auf einen anderen Server verschieben oder auf eine CD oder ein anderes Medium brennen.  
  
 In dieser exemplarischen Vorgehensweise, bei der es sich um eine von zwei verwandten exemplarischen Vorgehensweisen handelt, wird das Erstellen und anschließende Verteilen einer Projektvorlage für Websteuerelemente vermittelt. In der anderen exemplarischen Vorgehensweise, [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio\-Erweiterungs](../extensibility/walkthrough-publishing-a-visual-studio-extension.md), wird das Erstellen und Verteilen eines Websteuerelements erklärt.  
  
 Diese exemplarische Vorgehensweise enthält folgende Abschnitte:  
  
-   Erstellen einer Projektvorlage für Websteuerelemente in einer VSIX\-Erweiterung  
  
-   Veröffentlichen der Vorlage in der Visual Studio Gallery  
  
-   Installieren der Vorlage aus der Visual Studio Gallery  
  
-   Testen der installierten Vorlage  
  
-   Hinzufügen eines Debugaktions\-Assistenten zur Vorlage  
  
## Vorbereitungsmaßnahmen  
 Sie müssen mit Websteuerelementen und der Erstellung von Projekten, dem Festlegen von Projekteigenschaften und der experimentellen Instanz von Visual Studio vertraut sein, um diese exemplarische Vorgehensweise durchführen zu können. Sowohl Visual Studio als auch das Visual Studio SDK müssen auf dem Computer installiert sein. Bevor Sie mit dieser exemplarische Vorgehensweise beginnen, müssen Sie [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio\-Erweiterungs](../extensibility/walkthrough-publishing-a-visual-studio-extension.md) abschließen.  
  
## Erstellen einer Projektvorlage für Websteuerelemente in einer VSIX\-Erweiterung  
 Erstellen Sie zunächst ein Websteuerelement\-Projekt, um eine Projektvorlage für Websteuerelemente zu erstellen. Beginnen Sie in dieser exemplarischen Vorgehensweise mit dem ColorTextControl\-Websteuerelement\-Projekt, das Sie in [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio\-Erweiterungs](../extensibility/walkthrough-publishing-a-visual-studio-extension.md) erstellt haben.  
  
 Bevor Sie eine Projektvorlage in Visual Studio Gallery veröffentlichen, verwenden Sie den Assistenten zum **Exportieren der Vorlage als VSIX**, um die Vorlage als VSIX\-Erweiterung zu exportieren, und weisen Sie ihr ein Symbol zu, das zur leichteren Identifizierung im **Erweiterungs\-Manager** dient, sowie ein Bild zur Veranschaulichung der Funktionsweise.  
  
#### So bereiten Sie ein Websteuerelement\-Projekt für die Verteilung vor  
  
1.  Öffnen Sie in Visual Studio das Projekt „MyWebControls“.  
  
2.  Verwenden Sie den **Erweiterungs\-Manager** zum Herunterladen des **Assistenten zum Exportieren von Vorlagen** von der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=194329)\-Website.  
  
     Nach der Installation des Assistenten wird **Vorlage als VSIX exportieren** im Menü **Datei** angezeigt, wenn ein Projekt geöffnet ist.  
  
3.  Klicken Sie im Menü **Datei** auf **Vorlage als VSIX exportieren**.  
  
     ![Menü "File", Export Project as VSIX](../misc/media/pcwc_exportasvsix.png "PCWC\_ExportAsVsix")  
  
4.  Wählen Sie auf der Seite **Vorlagentyp auswählen** die Option **Projektvorlage** und dann die Datei „MyWebControls.csproj“ aus. Klicken Sie auf **Weiter**.  
  
     ![Auswählen einer Projektvorlage](../misc/media/pcwc_choosetemplate.png "PCWC\_ChooseTemplate")  
  
5.  Legen Sie auf der Seite **Vorlagenoptionen auswählen** für **Vorlagenname** die Option `Extensibility Color Text Web Toolbox Control` und für **Vorlagenbeschreibung** die Option `Color text web control project that produces a VSIX extension.` fest.  
  
6.  Klicken Sie neben dem Feld **Symbolbild** auf **Durchsuchen**. Geben Sie im Feld **Dateiname**`*.*` ein. Suchen Sie die Datei „Color.bmp“, und klicken Sie auf **Öffnen**.  
  
7.  Klicken Sie neben dem Feld **Vorschaubild** auf **Durchsuchen**. Geben Sie im Feld **Dateiname**`*.*` ein. Suchen Sie die Datei „ScreenShot.bmp“, und klicken Sie auf **Öffnen**. Klicken Sie auf **Weiter**.  
  
     ![Vorlagenoptionen auswählen](../misc/media/pcwc_selecttemplateoptions2.png "PCWC\_SelectTemplateOptions2")  
  
8.  Ändern Sie auf der Seite **VSIX\-Optionen auswählen** die Option **Produktname** in `Extensibility Color Text Web Control Template`.  
  
9. Bei Bedarf können Sie **Firmenname**, **Version**, **Lizenz** und die **URL für den Leitfaden für Erste Schritte** ändern.  
  
10. Deaktivieren Sie die Option **Vorlage automatisch in Visual Studio importieren**. Klicken Sie auf **Fertig stellen**.  
  
     ![Deaktivieren des automatischen Imports der Vorlage](../misc/media/pcwc_.png "PCWC\_")  
  
     In Windows\-Explorer wird die Datei „Extensibility Color Text Web Control Template.vsix“ im Ordner „..\\My Documents\\Visual Studio *\<Version\>*\\My Exported Templates\\“ aufgeführt.  
  
## Veröffentlichen der Vorlage in der Visual Studio Gallery  
 Die Projektvorlage kann jetzt in der Visual Studio Gallery veröffentlicht werden.  
  
#### So veröffentlichen Sie die Vorlage in der Visual Studio Gallery  
  
1.  Öffnen Sie die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=194329)\-Website in einem Webbrowser.  
  
2.  Klicken Sie rechts oben auf **Anmelden**.  
  
3.  Melden Sie sich mit dem Microsoft\-Konto an. Falls Sie kein Microsoft\-Konto haben, können Sie hier eines erstellen.  
  
4.  Klicken Sie auf **Hochladen**.  
  
5.  Wählen Sie in **Schritt 1: Erweiterungstyp** die Option **Projekt\- oder Elementvorlage** aus, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie in **Schritt 2: Hochladen** auf **Durchsuchen**. Wählen Sie im Ordner „\\My Exported Templates\\“ die Datei „Extensibility Color Text Web Control Template.vsix“ aus. Klicken Sie auf **Weiter**.  
  
7.  Unter **Schritt 3: Grundlegende Informationen** werden Informationen aus dem **Assistenten zum Exportieren von Vorlagen als VSIX\-Dateien** angezeigt.  
  
8.  Legen Sie für **Kategorie** den Wert `ASP.NET` und für **Tags** den Wert `toolbox, web control, templates` fest.  
  
9. Lesen und akzeptieren Sie den Einbringungsvertrag, und geben Sie dann den angezeigten Text in das Feld ein.  
  
10. Klicken Sie auf **Beitrag erstellen**, und klicken Sie dann auf **Veröffentlichen**.  
  
11. Durchsuchen Sie die Visual Studio Gallery nach „Extensibility Color Text Web Control Template“. Die Liste für die Vorlage sollte angezeigt werden.  
  
     ![Vorlagenauflistung für neues Websteuerelement](../misc/media/pcwc_templatelisting.png "PCWC\_TemplateListing")  
  
## Installieren der Vorlage aus der Visual Studio Gallery  
 Nachdem die Projektvorlage für das Websteuerelement veröffentlicht wurde, installieren Sie sie in Visual Studio und testen sie dort.  
  
#### So installieren Sie die Projektvorlage für das Websteuerelement in Visual Studio  
  
1.  Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungs\-Manager**.  
  
2.  Klicken Sie auf **Onlinekatalog**, und suchen Sie dann nach „Extensibility Color Text Web Control Template“. Die Liste für die Vorlage sollte angezeigt werden.  
  
3.  Klicken Sie auf **Download**. Nachdem die Erweiterung heruntergeladen wurde, klicken Sie auf **Installieren**.  
  
## Testen der installierten Vorlage  
 Jetzt können Sie die Projektvorlage „Extensibility Color Text Web Control“ zum Erstellen benutzerdefinierter Websteuerelemente verwenden. Sie müssen nicht alle manuell erstellen. In diesem Abschnitt wird veranschaulicht, wie Sie mithilfe der Vorlage ein BlueColorTextControl\-Websteuerelement erstellen.  
  
#### So erstellen Sie ein Websteuerelement auf Basis einer Vorlage  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  Klicken Sie im linken Bereich auf **Onlinevorlagen**, erweitern Sie **Vorlagen**, und klicken Sie dann auf **ASP.NET**. Klicken Sie im mittleren Bereich auf **Extensibility Color Text Web Control Template**.  
  
     ![Select the extensibility color text web template](../misc/media/pcwc_newprojecttemplate.png "PCWC\_NewProjectTemplate")  
  
3.  Legen Sie für **Name** die Option `MoreWebControls` fest. Klicken Sie auf **OK**.  
  
4.  Benennen Sie „ColorTextControl.cs“ im **Projektmappen\-Explorer** in „BlueColorTextControl.cs“ um.  
  
5.  Doppelklicken Sie auf „BlueColorTextControl.cs“, um die Datei im Editor zu öffnen.  
  
6.  Ersetzen Sie im `ToolboxData`\-Attribut beide Instanzen von `ColorTextControl` durch `BlueColorTextControl`.  
  
     Diese Werte geben die Start\- und Endtags an, die für das Steuerelement generiert werden, wenn es zur Entwurfszeit aus der **Toolbox** auf eine Webseite gezogen wird.  Sie müssen mit dem Namen der Steuerelementklasse übereinstimmen, der mit dem Namen des Steuerelements identisch ist, der in der **Toolbox** angezeigt wird.  
  
     Der Anfang des Quellcodes der Steuerelementklasse sollte jetzt folgendem Code ähneln.  
  
    ```  
    namespace MoreWebControls { [DefaultProperty("Text")] [ToolboxData("<{0}:BlueColorTextControl runat=server> </{0}:BlueColorTextControl>")] [ProvideToolboxControl("MoreWebControls", false)] public class BlueColorTextControl : WebControl {  
  
    ```  
  
7.  Ändern Sie `color:green` in der `get`\-Methode in `color:blue`.  
  
    ```  
    get { String s = (String)ViewState["Text"]; return "<span style='color:blue'>" + s + "</span>"; }  
    ```  
  
     Dadurch wird der Text in ein „span“\-Tag eingeschlossen und somit blau dargestellt.  
  
8.  Erstellen Sie das MoreWebControls\-Projekt.  
  
## Testen des neuen Websteuerelements  
 Sie können jetzt testen, ob das neue Websteuerelement in der **Toolbox** verfügbar ist. Obwohl das MoreWebControls\-Projekt geöffnet ist, wird durch Drücken von F5 jedoch keine experimentelle Instanz von Visual Studio gestartet, in der das Steuerelement getestet werden kann. Das liegt daran, dass das Projekt auf der Vorlage „Extensibility Color Text Web Control“ basiert, mit der noch keine Debugaktion festgelegt werden kann. \(Im nächsten Abschnitt wird das Hinzufügen eines Assistenten zur Vorlage gezeigt, der die Debugaktion festlegt.\) Gehen Sie zunächst wie folgt vor, um das Steuerelement zu testen.  
  
#### So testen Sie das neue Websteuerelement  
  
1.  Um eine experimentelle Instanz von Visual Studio zu öffnen, starten Sie die experimentelle Instanz.  
  
    1.  Verwenden Sie in [!INCLUDE[win7](../debugger/includes/win7_md.md)] das Menü **Start** \(**Start\/Alle Programme\/Microsoft Visual Studio \<Version\> SDK\/Tools\/Experimentelle Instanz von Microsoft Visual Studio \<Version\> starten**\).  
  
    2.  Geben Sie in [!INCLUDE[win81](../debugger/includes/win81_md.md)] auf dem Bildschirm **Start** die Zeichenfolge **Experimentelle Instanz von Microsoft Visual Studio \<Version\> starten** ein.  
  
2.  Erstellen Sie ein Webanwendungsprojekt.  
  
3.  Öffnen Sie im Projekt die Datei „default.aspx“. Stellen Sie sicher, dass die Ansicht **Quelle** angezeigt wird.  
  
4.  In der **Toolbox** sollte in der Kategorie **MoreWebControls** die Option **BlueColorTextControl** angezeigt werden.  
  
     ![BlueColorTextControl für MoreWebControls](../misc/media/pcwc_toolbox2.png "PCWC\_Toolbox2")  
  
5.  Ziehen Sie ein „BlueColorTextControl“ an eine beliebige Stelle im `body`\-Tag der Webseite.  
  
6.  Fügen Sie im `ColorTextControl`\-Tag ein `Text`\-Attribut hinzu, und weisen Sie ihm `Think Blue!` als Wert zu. Das sich ergebende Tag entspricht in etwa dem folgenden Beispiel.  
  
    ```  
    <cc1:BlueColorTextControl ID="BlueColorTextControl1" Text="Think Blue!" runat="server" />  
  
    ```  
  
7.  Drücken Sie F5, um den ASP.NET Development Server zu starten.  
  
     Die Anzeige des BlueColorTextControl\-Steuerelements sollte der folgenden Abbildung entsprechen.  
  
     ![BlueColorTextControl rendert Think Blue](../misc/media/pcwc_thinkblue.png "PCWC\_ThinkBlue")  
  
8.  Schließen Sie den ASP.NET Development Server.  
  
9. Schließen Sie die experimentelle Instanz von Visual Studio.  
  
## Hinzufügen eines Debugaktions\-Assistenten zur Vorlage  
 Wie Sie, wie im vorherigen Abschnitt erwähnt, bei geöffnetem MoreWebControls\-Projekt F5 drücken, wird keine experimentelle Instanz von Visual Studio geöffnet. Stattdessen wird die Mitteilung „Ein Projekt mit dem Ausgabetyp Klassenbibliothek kann nicht direkt gestartet werden“ angezeigt. Dies ist der Fall, wenn der Speicherort der experimentellen Instanz einem Projekt nicht bekannt ist. Sie können jedoch eine Vorlage aktivieren, um den Speicherort der experimentellen Instanz auf einem Zielcomputer zu ermitteln und dann die entsprechende Debugaktion festzulegen. Danach werden alle Projekte auf dem Computer, die auf dieser Vorlage basieren, wie erwartet auf F5 reagieren.  
  
 Jede Erweiterungsprojektvorlage, die im Visual Studio SDK enthalten ist, enthält einen Assistenten, der während der Installation ausgeführt wird, die experimentelle Instanz auf dem Zielcomputer sucht und dann die Debugaktion festlegt. Sie können zu diesem Zweck Ihren eigenen Assistenten erstellen und diesen in jede zu verteilende Vorlage einbeziehen.  
  
 Wenn Sie einen Assistenten für Debugaktionen zur Vorlage „Extensibility Color Text Web Control“ hinzufügen möchten, müssen Sie die erste Version der Vorlage löschen, dann den Assistenten hinzufügen und anschließend die Vorlage erneut erstellen.  
  
#### So löschen Sie die erste Version der Vorlage  
  
1.  Klicken Sie auf der Visual Studio Gallery\-Website in der oberen linken Ecke auf **Eigene Beiträge**. Die Liste **Extensibility Color Text Web Control Template** wird angezeigt.  
  
2.  Klicken Sie auf **Löschen**, um Ihre Projektvorlage dauerhaft aus der Visual Studio Gallery zu entfernen.  
  
3.  Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungs\-Manager**.  
  
4.  Wählen Sie **Extensibility Color Text Web Control Template** aus, und klicken Sie dann auf **Deinstallieren**.  
  
5.  Schließen Sie den **Erweiterungs\-Manager**.  
  
6.  Schließen Sie die Projektmappe „MoreWebControls“.  
  
7.  Schließen Sie Visual Studio.  
  
8.  Löschen Sie den Projektmappenordner für „MoreWebControls“.  
  
9. Starten Sie Visual Studio neu, um die Deinstallation abzuschließen.  
  
 Der Assistent für die Debugaktion muss über eine öffentliche Implementierung des `Microsoft.VisualStudio.TemplateWizard.IWizard` verfügen und mit einem starken Assemblynamen signiert sein.  
  
#### So erstellen Sie den Assistenten für Debugaktionen  
  
1.  Erstellen Sie im Dialogfeld **Neues Projekt** ein **Visual C\#**\-, **Windows**\-, **Klassenbibliothek**\-Projekt, und weisen Sie ihm die Bezeichnung `MyWizard` zu.  
  
2.  Benennen Sie „class1.cs“ im neuen Projekt in „MyWizard.cs“ um.  
  
3.  Ersetzen Sie den Inhalt von „MyWizard.cs“ durch den folgenden Code.  
  
    ```  
    using System; using System.Collections.Generic; using System.Linq; using System.Text; using Microsoft.VisualStudio.TemplateWizard; using System.Globalization; using EnvDTE; namespace MyWizard { public class MyWizard : IWizard { public void BeforeOpeningFile(ProjectItem projectItem) { } public void ProjectFinishedGenerating(Project project) { foreach (Configuration config in project.ConfigurationManager) { //Set up the debug options to run "devenv /rootsuffix Exp"; config.Properties.Item("StartAction").Value = 1; //Get the full path to devenv.exe through DTE.FullName config.Properties.Item("StartProgram").Value = project.DTE.FullName; config.Properties.Item("StartArguments").Value = "/rootsuffix Exp"; } } public void ProjectItemFinishedGenerating(ProjectItem projectItem) { } public void RunFinished() { } public void RunStarted(object automationObject, Dictionary<string, string> replacementsDictionary, WizardRunKind runKind, object[] customParams) { } public bool ShouldAddProjectItem(string filePath) { return true; } } }  
  
    ```  
  
4.  Fügen Sie dem Projekt die folgenden Verweise hinzu. Wenn mehrere Optionen verfügbar sind, wählen Sie den Verweis, der über einen Pfad zu [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] verfügt.  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
5.  Klicken Sie mit der rechten Maustaste auf das Projekt „MyWizard“, und klicken Sie dann auf **Eigenschaften**. Aktivieren Sie auf der Registerkarte **Signierung** die Option **Assembly signieren**.  
  
6.  Wählen Sie in der Liste **Schlüsseldatei mit starkem Namen auswählen** die Option **\<Neu…\>** aus. Das Dialogfeld **Schlüssel für einen starken Namen erstellen** wird angezeigt.  
  
7.  Legen Sie für **Schlüsseldateiname** die Option `key.snk` fest, und deaktivieren Sie die Option **Schlüsseldatei mit Kennwort schützen**.  
  
     ![Geben Sie eine Schlüsseldatei an.](../misc/media/pcwc_strongname.png "PCWC\_StrongName")  
  
8.  Klicken Sie auf **OK**, um „key.snk“ zum Projekt hinzuzufügen.  
  
9. Erstellen Sie das Projekt „MyWizard“ als Versionsbuild. Der Assistent ist jetzt einsatzbereit.  
  
10. Schließen Sie die Projektmappe „MyWizard“.  
  
#### So beziehen Sie den Assistenten ein und erstellen die Vorlage neu  
  
1.  Befolgen Sie die Schritte des vorherigen Abschnitts, „Erstellen einer Projektvorlage für Websteuerelemente in einer VSIX\-Erweiterung“, aber nehmen Sie dabei die folgenden Ergänzungen und Änderungen vor:  
  
    -   Sie müssen den **Assistenten zum Exportieren der Vorlage als VSIX** nicht erneut herunterladen.  
  
    -   Navigieren Sie im **Assistenten zum Exportieren der Vorlage als VSIX** auf der Seite **VSIX\-Optionen auswählen** im Feld **Assistent** zur Datei „\\bin\\Release\\MyWizard.dll“, die Sie in den vorherigen Schritten erstellt haben, und wählen Sie sie dann aus.  
  
         ![Geben Sie die Assistenten&#45;Assembly an](../misc/media/pcwc_wizardassembly.png "PCWC\_WizardAssembly")  
  
    -   Wenn Sie aufgefordert werden, die vorhandene Ausgabedatei mit der Erweiterung VSIX zu überschreiben, klicken Sie auf **Ja**.  
  
2.  Wenn Sie den Abschnitt „Testen des neuen Websteuerelements“ erreichen, drücken Sie F5. Dann sollte eine experimentelle Instanz von Visual Studio gestartet werden.  
  
## Nächste Schritte  
 In dieser exemplarischen Vorgehensweise wurde die Verwendung des **Assistenten zum Exportieren der Vorlage als VSIX** zum Erstellen und Verteilen einer Projektvorlage veranschaulicht. Wenn Sie die Projektvorlage noch umfassender steuern möchten, um z. B. das im Dialogfeld **Neues Projekt** angezeigte Symbol auszuwählen, müssen Sie die Projektvorlage explizit erstellen und in einer VSIX\-Erweiterung umschließen. Weitere Informationen finden Sie unter [Erstellen und Freigeben von Projekt\- und Elementvorlagen](http://go.microsoft.com/fwlink/?LinkId=194551) auf der Visual Studio Blog\-Website.  
  
## Siehe auch  
 [Lieferung von Visual Studio\-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)