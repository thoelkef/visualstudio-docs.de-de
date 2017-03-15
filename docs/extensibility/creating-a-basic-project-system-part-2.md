---
title: "Erstellen eine grundlegende Projektsystem, Teil 2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schreiben ein Projektsystem"
  - "Projektsystem"
  - "Lernprogramm"
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Erstellen eine grundlegende Projektsystem, Teil 2
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der ersten exemplarischen Vorgehensweise in dieser Reihe [Erstellen eine grundlegende Projektsystem, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md), zeigt, wie Sie ein einfaches Projekt\-System erstellen. Diese exemplarische Vorgehensweise baut auf das grundlegende Projektsystem von Visual Studio\-Vorlage, eine Eigenschaftenseite und andere Features hinzufügen. Sie müssen die erste exemplarischen Vorgehensweise abschließen, bevor Sie diese starten.  
  
 In dieser exemplarischen Vorgehensweise erfahren, wie ein Projekt zu erstellen, die Project\-Datei namens Erweiterung .myproj verfügt. Um die exemplarische Vorgehensweise abzuschließen, müssen Sie nicht Ihre eigene Sprache erstellt werden, da die exemplarischen Vorgehensweise aus dem vorhandenen Visual C\#\-Projektsystem ist.  
  
 Diese exemplarische Vorgehensweise zeigt, wie Sie diese Aufgaben ausführen:  
  
-   Erstellen Sie eine Visual Studio\-Vorlage.  
  
-   Bereitstellen einer Visual Studio\-Vorlage.  
  
-   Erstellen Sie einen Projekt Typ untergeordneter Knoten in der **Neues Projekt** \(Dialogfeld\).  
  
-   Aktivieren Sie die parameterersetzung in der Visual Studio\-Vorlage.  
  
-   Erstellen Sie eine Projekteigenschaftenseite.  
  
> [!NOTE]
>  Die Schritte in dieser exemplarischen Vorgehensweise basieren auf einem C\#\-Projekt. Jedoch können Sie mit Ausnahme von Informationen wie z. B. Dateinamenerweiterungen und Code dieselben Schritte für ein Visual Basic\-Projekt verwenden.  
  
## Erstellen einer Visual Studio\-Vorlage  
 [Erstellen eine grundlegende Projektsystem, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md) Zeigt, wie eine grundlegende Projektvorlage erstellen und mit dem Projektsystem hinzuzufügen. Darüber hinaus wird zum Registrieren von dieser Vorlage mit Visual Studio mithilfe der <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> \-Attribut, das den vollständigen Pfad des Ordners \\Templates\\Projects\\SimpleProject\\ in der Registrierung schreibt.  
  
 Durch Visual Studio\-Vorlage \(VSTEMPLATE\-Datei\) anstelle einer grundlegenden Projektvorlage verwenden, können Sie steuern, wie in die Vorlage angezeigt wird die **Neues Projekt** \(Dialogfeld\), und wie Vorlagenparameter ersetzt werden.  Eine VSTEMPLATE\-Datei ist eine XML\-Datei, die beschreibt, wie Quelldateien enthalten sein, wenn ein Projekt mit der Projektvorlage für das System erstellt wird. Das Projektsystem selbst wird durch Sammeln der VSTEMPLATE\-Datei und die Quelldateien in einer ZIP\-Datei erstellt und bereitgestellt durch Kopieren die ZIP\-Datei an einem Speicherort, der in Visual Studio bezeichnet wird. Dieser Prozess wird weiter unten in dieser exemplarischen Vorgehensweise ausführlich erläutert.  
  
1.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], öffnen Sie die SimpleProject\-Lösung, die Sie, indem Sie die folgenden erstellt [Erstellen eine grundlegende Projektsystem, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2.  Suchen Sie in der Datei SimpleProjectPackage.cs die ProvideProjectFactory\-Attribut. Ersetzen Sie den zweiten Parameter \(Projektname\) mit Null, und der vierte Parameter \(der Pfad zum Projektordner Vorlage\) mit ".\\\\NullPath", wie folgt.  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null, "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj", ".\\NullPath", LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  Fügen Sie eine XML\-Datei mit dem Namen SimpleProject.vstemplate in den Ordner \\Templates\\Projects\\SimpleProject\\ hinzu.  
  
4.  Ersetzen Sie den Inhalt der SimpleProject.vstemplate durch den folgenden Code ein.  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"> <TemplateData> <Name>SimpleProject Application</Name> <Description> A project for creating a SimpleProject application </Description> <Icon>SimpleProject.ico</Icon> <ProjectType>SimpleProject</ProjectType> </TemplateData> <TemplateContent> <Project File="SimpleProject.myproj" ReplaceParameters="true"> <ProjectItem ReplaceParameters="true" OpenInEditor="true"> Program.cs </ProjectItem> <ProjectItem ReplaceParameters="true" OpenInEditor="false"> AssemblyInfo.cs </ProjectItem> </Project> </TemplateContent> </VSTemplate>  
    ```  
  
5.  In der **Eigenschaften** wählen Sie im Fenster alle fünf Dateien in den Ordner \\Templates\\Projects\\SimpleProject\\ und legen die **Buildvorgang** auf **ZipProject**.  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 Der Abschnitt \< TemplateData \> bestimmt die Position und die Darstellung des Projekttyps SimpleProject in der **Neues Projekt** im Dialogfeld wie folgt:  
  
-   Das Element \< Name \> den Namen der Projektvorlage SimpleProject Anwendung sein.  
  
-   Das \< Description \>\-Element enthält die Beschreibung, die in angezeigt wird der **Neues Projekt** im Dialogfeld, wenn die Projektvorlage ausgewählt ist.  
  
-   Das \< Icon \>\-Element gibt das Symbol an, das zusammen mit den Projekttyp SimpleProject angezeigt wird.  
  
-   Das Element \< ProjectType \> Projekttyp im Namen der **Neues Projekt** \(Dialogfeld\). Dieser Name wird den Projekt\-Name\-Parameter des Attributs ProvideProjectFactory ersetzt.  
  
    > [!NOTE]
    >  \< ProjectType \>\-Elements übereinstimmen muss die `LanguageVsTemplate` Argument der `ProvideProjectFactory` Attribut in der Datei SimpleProjectPackage.cs.  
  
 Der Abschnitt \< TemplateContent \> beschreibt diese Dateien, die generiert werden, wenn ein neues Projekt erstellt wird:  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   Datei "AssemblyInfo.cs"  
  
 Alle drei Dateien haben `ReplaceParameters` auf True festgelegt, wodurch Parameter ersetzt.  Die Datei "Program.cs" hat `OpenInEditor` auf True festgelegt, wodurch die Datei im Code\-Editor geöffnet werden, wenn ein Projekt erstellt wird.  
  
 Weitere Informationen zu den Elementen im Schema Visual Studio\-Vorlage finden Sie unter der [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Wenn ein Projekt mehrere Visual Studio\-Vorlage enthält, ist jeder Vorlage in einem separaten Ordner. Jede Datei in diesem Ordner müssen die **Buildvorgang** festgelegt **ZipProject**.  
  
## Hinzufügen einer minimalen VSCT\-Datei  
 Im Setup\-Modus eine neue oder geänderte Visual Studio\-Vorlage erkennen muss Visual Studio ausgeführt werden. Setupmodus erfordert eine VSCT\-Datei vorhanden sein. Aus diesem Grund müssen Sie eine minimale VSCT\-Datei zum Projekt hinzufügen.  
  
1.  Fügen Sie eine XML\-Datei mit dem Namen SimpleProject.vsct SimpleProject\-Projekt hinzu.  
  
2.  Ersetzen Sie den Inhalt der Datei SimpleProject.vsct durch den folgenden Code ein.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"> </CommandTable>  
    ```  
  
3.  Legen Sie die **Buildvorgang** dieser Datei in **VSCTCompile**. Hierzu können Sie nur in der CSPROJ\-Datei nicht in der **Eigenschaften** Fenster. Stellen Sie sicher, dass die **Buildvorgang** dieser Datei wird festgelegt **keine** an diesem Punkt.  
  
    1.  Mit der rechten Maustaste des Knotens SimpleProject, und klicken Sie dann auf **Bearbeiten SimpleProject.csproj**.  
  
    2.  Suchen Sie in der CSPROJ\-Datei das SimpleProject.vsct\-Element.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Ändern Sie den Buildvorgang auf **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  die Projektdatei und schließen Sie Editor.  
  
    5.  Speichern Sie den Knoten SimpleProject und dann in der **Projektmappen\-Explorer** klicken Sie auf **Projekt erneut laden**.  
  
## Untersuchen die Buildschritte für Visual Studio\-Vorlage  
 Das Buildsystem für VSPackage\-Projekt führt Visual Studio normalerweise im Installationsmodus, bei die VSTEMPLATE\-Datei geändert wurde oder das Projekt mit der VSTEMPLATE\-Datei wird neu erstellt. Sie können durch Festlegen den Ausführlichkeitsgrad der MSBuild auf Normal oder höher nachvollziehen.  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie die **Projekte und Projektmappen** Knoten, und wählen Sie dann **Erstellen und führen Sie**.  
  
3.  Legen Sie **MSBuild\-Projektbuilds Ausgabe Ausführlichkeit** auf **Normal**. Klicken Sie auf **OK**.  
  
4.  Das SimpleProject\-Projekt neu.  
  
 Der Buildschritt die ZIP\-Datei erstellen sollte dem folgenden Beispiel entsprechen.  
  
```  
ZipProjects: 1>  Zipping ProjectTemplates 1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip... 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip". 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip". 1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip 1>ZipItems: 1>  Zipping ItemTemplates 1>  SimpleProject ->  
```  
  
## Bereitstellen einer Visual Studio\-Vorlage  
 Visual Studio\-Vorlagen enthalten keine Pfadinformationen. Aus diesem Grund muss die ZIP\-Datei der Vorlage an einem Speicherort bereitgestellt werden, die Visual Studio bekannt ist. Der Speicherort des Ordners ProjectTemplates ist in der Regel **\< % LocalAppData% \> \\Microsoft\\VisualStudio\\14.0Exp\\ProjectTemplates**.  
  
 Um die Projekt\-Factory bereitstellen zu können, muss das Installationsprogramm über Administratorrechte verfügen. Vorlagen unter dem Knoten der Visual Studio\-Installation bereitgestellt: **...\\Microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates**.  
  
## Testen Visual Studio\-Vorlage  
 Testen Sie die Projekt\-Factory, um festzustellen, ob eine Projekthierarchie wird mithilfe der Visual Studio\-Vorlage erstellt.  
  
1.  Zurücksetzen der experimentellen Instanz von Visual Studio SDK.  
  
     Auf [!INCLUDE[win7](../debugger/includes/win7_md.md)]: finden Sie im Startmenü die **Microsoft Visual Studio und Microsoft Visual Studio SDK\/Tools** und wählen Sie dann **Microsoft Visual Studio experimentelle Instanz zurücksetzen**.  
  
     In höheren Versionen von Windows: Geben Sie auf der Startseite **Zurücksetzen der Microsoft Visual Studio \< Version \> experimentelle Instanz**.  
  
2.  Ein Eingabeaufforderungsfenster wird angezeigt. Wenn Sie sehen, dass die Wörter `Press any key to continue`, drücken Sie die EINGABETASTE. Wenn das Fenster geschlossen wurde, öffnen Sie Visual Studio.  
  
3.  Das SimpleProject\-Projekt neu erstellen und mit dem Debuggen beginnen. Die experimentelle Instanz angezeigt wird.  
  
4.  Erstellen Sie in der experimentellen Instanz ein SimpleProject\-Projekt. In der **Neues Projekt** wählen Sie im Dialogfeld **SimpleProject**.  
  
5.  Eine neue Instanz der SimpleProject sollte angezeigt werden.  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2\_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2\_MyProj")  
  
## Erstellen einen Projekt Typ untergeordneter Knoten  
 Sie können einen Typ Projektknoten einen untergeordneten Knoten hinzufügen der **Neues Projekt** \(Dialogfeld\).  Für den Projekttyp SimpleProject könnten Sie z. B. untergeordneten Knoten für konsolenanwendungen, Window\-Applikationen, ASP.NET\-Webanwendungen und usw. verfügen.  
  
 Untergeordnete Knoten werden erstellt, durch die Projektdatei ändern und die Elemente \< ZipProject \> \< OutputSubPath \> untergeordnete Elemente hinzugefügt. Wenn während der Erstellung oder Bereitstellung eine Vorlage kopiert wird, wird jeder untergeordnete Knoten einen Unterordner des Ordners Vorlagen Projekt.  
  
 In diesem Abschnitt zeigt, wie einen Konsole untergeordneter Knoten für den Projekttyp SimpleProject erstellt wird.  
  
1.  Benennen Sie den Ordner \\Templates\\Projects\\SimpleProject\\ in \\Templates\\Projects\\ConsoleApp\\.  
  
2.  In der **Eigenschaften** Fenster, wählen Sie alle fünf Dateien im Ordner \\Templates\\Projects\\ConsoleApp\\ und stellen Sie sicher, dass die **Buildvorgang** auf festgelegt ist **ZipProject**.  
  
3.  Fügen Sie die folgende Zeile am Ende des Abschnitts \< TemplateData \> direkt vor dem Endtag ein, in der Datei SimpleProject.vstemplate.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Dies bewirkt, dass die Konsolenanwendungsvorlage angezeigt werden, in der Konsole untergeordnete Knoten und in der SimpleProject übergeordneten Knoten, der untergeordnete Knoten übergeordnet ist.  
  
4.  Speichern Sie die Datei SimpleProject.vstemplate.  
  
5.  Fügen Sie in der CSPROJ\-Datei \< OutputSubPath \> in der ZipProject\-Elemente. Entladen Sie das Projekt, wie zuvor aus, und bearbeiten Sie die Projektdatei.  
  
6.  Suchen Sie nach den Elementen \< ZipProject \>. Klicken Sie auf jedes Element \< ZipProject \> Fügen Sie \< OutputSubPath \> Element hinzu, und geben sie den Wert Konsole. Die ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico"> <OutputSubPath>Console</OutputSubPath> </ZipProject>  
    ```  
  
7.  Fügen Sie der Projektdatei dieses \< PropertyGroup \> hinzu:  
  
    ```  
    <PropertyGroup> <VsTemplateLanguage>SimpleProject</VsTemplateLanguage> </PropertyGroup>  
    ```  
  
8.  Speichern Sie die Datei, und Laden Sie das Projekt erneut.  
  
## Testen den Projekt Typ untergeordneten Knoten  
 Testen Sie die geänderte Projektdatei an, ob die **Konsole** untergeordneten Knoten befindet sich im die **Neues Projekt** \(Dialogfeld\).  
  
1.  Führen Sie die **Zurücksetzen der Microsoft Visual Studio experimentelle Instanz** Tool.  
  
2.  Das SimpleProject\-Projekt neu erstellen und mit dem Debuggen beginnen. Die experimentelle Instanz sollte angezeigt werden.  
  
3.  In der **Neues Projekt** Dialogfeld klicken Sie auf die **SimpleProject** Knoten. Die **Konsolenanwendung** Vorlage sollte angezeigt werden, der **Vorlagen** Bereich.  
  
4.  Erweitern Sie die **SimpleProject** Knoten. Die **Konsole** untergeordneten Knoten angezeigt werden soll. Die **SimpleProject Anwendung** Vorlage wird weiterhin angezeigt, in der **Vorlagen** Bereich.  
  
5.  . Klicken Sie auf **Abbrechen** und das Debuggen beendet  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2\_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2\_Subfolder")  
  
## Projekt\-Vorlagenparameter ersetzen  
 [Erstellen eine grundlegende Projektsystem, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md) wurde gezeigt, wie Sie überschreiben die `ProjectNode.AddFileFromTemplate` Methode, um eine grundlegende Art von Vorlage Parameter ersetzt werden. Dieser Abschnitt zeigt, wie Sie die komplexere Visual Studio\-Vorlagenparameter zu verwenden.  
  
 Beim Erstellen eines Projekts mit Visual Studio\-Vorlage in die **Neues Projekt** klicken Sie im Dialogfeld Vorlage Parameter werden durch Zeichenfolgen, um die Anpassung des Projekts. Ein Vorlagenparameter ist ein spezielles Token, das beginnt und endet mit einem Dollarzeichen, z. B. $time$. Die folgenden beiden Parameter sind besonders für die Anpassung in Projekten, die auf der Vorlage basieren:  
  
-   $GUID \[1\-10\] $ wird durch eine neue Guid ersetzt. Sie können bis zu 10 eindeutige GUIDs, z. B. $guid1$ angeben.  
  
-   $safeprojectname$ ist, den Namen eines Benutzers in der **Neues Projekt** Dialogfeld geändert, dass alle unsicheren Zeichen sowie Leerzeichen entfernt.  
  
 Eine vollständige Liste der Vorlagenparameter, finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  Wenn Sie eigene benutzerdefinierte Vorlagenparameter erstellen möchten, finden Sie unter [NIB: Gewusst wie: Übergeben von benutzerdefinierten Parametern an Vorlagen](http://msdn.microsoft.com/de-de/5bc2ad11-84c7-4683-a276-e5e00d85d8fb).  
  
#### Projekt\-Vorlagenparameter ersetzen  
  
1.  Entfernen Sie in der Datei SimpleProjectNode.cs die `AddFileFromTemplate` Methode.  
  
2.  Klicken Sie in der Datei \\Templates\\Projects\\ConsoleApp\\SimpleProject.myproj suchen Sie die Eigenschaft Namespace \< Root \>, und ändern Sie seinen Wert in $safeprojectname$.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  Ersetzen Sie in der Datei \\Templates\\Projects\\SimpleProject\\Program.cs den Inhalt der Datei durch den folgenden Code ein:  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace $safeprojectname$ { [Guid("$guid1$")] public class $safeprojectname$ { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
4.  Das SimpleProject\-Projekt neu erstellen und mit dem Debuggen beginnen. Die experimentelle Instanz sollte angezeigt werden.  
  
5.  Erstellen Sie eine neue SimpleProject. \(In der **Projekttypen** aus **SimpleProject**. Unter **Visual Studio installierte Vorlagen**, auf **Konsolenanwendung**.\)  
  
6.  Öffnen Sie die Datei Program.cs, in das Projekt neu erstellt. Es sollte etwa wie folgt aussehen \(GUID\-Werte in der Datei variieren.\):  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace Console_Application1 { [Guid("00000000-0000-0000-00000000-00000000)"] public class Console_Application1 { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
## Erstellen eine Eigenschaftenseite des Projekts  
 Sie können eine Eigenschaftenseite für den Projekttyp erstellen, sodass Benutzer anzeigen und Ändern von Eigenschaften in Projekten, die auf der Vorlage basieren können. In diesem Abschnitt erfahren Sie, wie auf einer Eigenschaftenseite konfigurationsunabhängige erstellt. Diese grundlegenden Eigenschaftenseite verwendet ein Eigenschaftenraster, um die öffentlichen Eigenschaften angezeigt, die Sie in der Eigenschaftenseitenklasse verfügbar machen.  
  
 Leiten Sie die Eigenschaft Seitenklasse aus der `SettingsPage` Basisklasse. Von bereitgestellten Eigenschaftenraster der `SettingsPage` Klasse unterstützt die meisten primitiven Datentypen und weiß, wie sie angezeigt.  Darüber hinaus die `SettingsPage` Klasse weiß, wie Eigenschaftswerte in der Projektdatei beibehalten werden.  
  
 Die Eigenschaftenseite, die Sie in diesem Abschnitt erstellen können Sie alter und speichern diese Eigenschaften:  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace.  
  
1.  Fügen Sie in der Datei SimpleProjectPackage.cs Dies `ProvideObject` \-Attribut auf die `SimpleProjectPackage` Klasse:  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))] public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     Dadurch wird die Eigenschaft Page\-Klasse registriert `GeneralPropertyPage` mit COM.  
  
2.  Fügen Sie in der Datei SimpleProjectNode.cs beiden überschriebenen Methoden der `SimpleProjectNode` Klasse:  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; } protected override Guid[] GetPriorityProjectDesignerPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; }  
    ```  
  
     Beide Methoden wird ein Array von GUIDs\-Eigenschaftenseite zurückzugeben.  Die GeneralPropertyPage\-GUID ist das einzige Element im Array an, damit der **Eigenschaftenseiten** Dialogfeld wird nur eine Seite angezeigt.  
  
3.  Fügen Sie eine Klassendatei mit dem Namen GeneralPropertyPage.cs SimpleProject\-Projekt hinzu.  
  
4.  Ersetzen Sie den Inhalt dieser Datei mithilfe des folgenden Codes:  
  
    ```  
    using System; using System.Runtime.InteropServices; using Microsoft.VisualStudio; using Microsoft.VisualStudio.Project; using System.ComponentModel; namespace SimpleProject { [ComVisible(true)] [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")] public class GeneralPropertyPage : SettingsPage { private string assemblyName; private OutputType outputType; private string defaultNamespace; public GeneralPropertyPage() { this.Name = "General"; } [Category("AssemblyName")] [DisplayName("AssemblyName")] [Description("The output file holding assembly metadata.")] public string AssemblyName { get { return this.assemblyName; } } [Category("Application")] [DisplayName("OutputType")] [Description("The type of application to build.")] public OutputType OutputType { get { return this.outputType; } set { this.outputType = value; this.IsDirty = true; } } [Category("Application")] [DisplayName("DefaultNamespace")] [Description("Specifies the default namespace for added items.")] public string DefaultNamespace { get { return this.defaultNamespace; } set { this.defaultNamespace = value; this.IsDirty = true; } } protected override void BindProperties() { this.assemblyName = this.ProjectMgr.GetProjectProperty( "AssemblyName", true); this.defaultNamespace = this.ProjectMgr.GetProjectProperty( "RootNamespace", false); string outputType = this.ProjectMgr.GetProjectProperty( "OutputType", false); this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType); } protected override int ApplyChanges() { this.ProjectMgr.SetProjectProperty( "AssemblyName", this.assemblyName); this.ProjectMgr.SetProjectProperty( "OutputType", this.outputType.ToString()); this.ProjectMgr.SetProjectProperty( "RootNamespace", this.defaultNamespace); this.IsDirty = false; return VSConstants.S_OK; } } }  
    ```  
  
     Die `GeneralPropertyPage` Klasse verfügbar macht, die drei öffentlichen Eigenschaften Stammnamespace, AssemblyName und OutputType. Da der AssemblyName keine Set\-Methode verfügt, wird es als schreibgeschützte Eigenschaft angezeigt. OutputType ist eine Enumerationskonstante, sodass er als Dropdown\-Liste angezeigt wird.  
  
     Die `SettingsPage` \-Basisklasse stellt `ProjectMgr` Eigenschaften beibehalten werden. Die `BindProperties` \-Methode verwendet `ProjectMgr` beibehaltenen Werte abgerufen und die entsprechenden Eigenschaften festgelegt.  Die `ApplyChanges` \-Methode verwendet `ProjectMgr` zum Abrufen der Werte der Eigenschaften und in der Projektdatei beibehalten. Der Eigenschaftensatz legt `IsDirty` auf true, um anzugeben, dass die Eigenschaften beibehalten werden müssen.  Dauerhaftigkeit tritt auf, wenn Sie das Projekt oder die Projektmappe speichern.  
  
5.  Erstellen Sie die Lösung SimpleProject, und starten Sie das Debuggen. Die experimentelle Instanz sollte angezeigt werden.  
  
6.  Erstellen Sie eine neue SimpleProject\-Anwendung, in der experimentellen Instanz.  
  
7.  Visual Studio ruft die Projekt\-Factory zum Erstellen eines Projekts mithilfe der Visual Studio\-Vorlage. Die neue Datei "Program.cs" wird im Code\-Editor geöffnet.  
  
8.  Mit der rechten Maustaste des Projektknoten im **Projektmappen\-Explorer**, und klicken Sie dann auf **Eigenschaften**. Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2\_PropPage")  
  
## Testen die Eigenschaftenseite des Projekts  
 Jetzt können Sie testen, ob Sie ändern können und die Eigenschaftswerte ändern.  
  
1.  In der **MyConsoleApplication Eigenschaftenseiten** ändern Sie im Dialogfeld die **DefaultNamespace** auf **MyApplication**.  
  
2.  Wählen Sie die **OutputType** \-Eigenschaft, und wählen Sie **Klassenbibliothek**.  
  
3.  Klicken Sie auf **Übernehmen**, und klicken Sie dann auf **OK**.  
  
4.  Öffnen Sie erneut die **Eigenschaftenseiten** Dialogfeld ein, und stellen Sie sicher, dass die Änderungen gespeichert wurden.  
  
5.  Schließen Sie die experimentelle Instanz von Visual Studio.  
  
6.  Öffnen Sie die experimentelle Instanz erneut.  
  
7.  Öffnen Sie erneut die **Eigenschaftenseiten** Dialogfeld ein, und stellen Sie sicher, dass die Änderungen gespeichert wurden.  
  
8.  Schließen Sie die experimentelle Instanz von Visual Studio.  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2\_PropPage2")