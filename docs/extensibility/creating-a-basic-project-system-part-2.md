---
title: Erstellen eine grundlegende Projektsystem, Teil 2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f39150f02481e18997035a8027518648fa410f48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-basic-project-system-part-2"></a>Erstellen eine grundlegende Projektsystem, Teil 2
Der ersten exemplarischen Vorgehensweise in dieser Serie [erstellen eine grundlegende Projektsystem, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md), zeigt, wie eine grundlegende Projektsystem zu erstellen. In dieser exemplarischen Vorgehensweise baut auf das grundlegende Projektsystem eine Visual Studio-Vorlage, einer Eigenschaftenseite und andere Funktionen. Bevor Sie dieses Objekt starten, müssen Sie die erste exemplarischen Vorgehensweise ausführen.  
  
 In dieser exemplarischen Vorgehensweise erfahren, wie ein Projekt zu erstellen, die Projekt-Datei Name Erweiterung .myproj verfügt. Um die exemplarische Vorgehensweise abgeschlossen haben, müssen Sie keinen eigenen Sprache erstellt werden, da die exemplarischen Vorgehensweise aus dem vorhandenen Visual C#-Projektsystem Grunde verwendet.  
  
 In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie diese Aufgaben ausführen:  
  
-   Erstellen Sie eine Visual Studio-Vorlage.  
  
-   Bereitstellen einer Visual Studio-Vorlage.  
  
-   Erstellen Sie einen Projekt Typ untergeordneten Knoten in der **neues Projekt** (Dialogfeld).  
  
-   Ersetzung von Typparametern in der Visual Studio-Vorlage zu aktivieren.  
  
-   Erstellen einer Projekteigenschaftsseite.  
  
> [!NOTE]
>  Die Schritte in dieser exemplarischen Vorgehensweise basiert auf einem C#-Projekt. Jedoch können Sie außer Besonderheiten wie Dateinamenerweiterungen und Code, dieselben Schritte für ein Visual Basic-Projekt verwenden.  
  
## <a name="creating-a-visual-studio-template"></a>Erstellen einer Visual Studio-Vorlage  
 [Erstellen eine grundlegende Projektsystem, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md) wird gezeigt, wie eine grundlegende Projektvorlage erstellen und mit dem Projektsystem hinzuzufügen. Außerdem wird gezeigt, wie zum Registrieren von dieser Vorlage mit Visual Studio mithilfe der <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> -Attribut, das den vollständigen Pfad des Ordners \Templates\Projects\SimpleProject\ in der Registrierung schreibt.  
  
 Visual Studio-Vorlage (VSTEMPLATE-Datei) als eine grundlegende-Projektvorlage verwenden, können Sie steuern, wie in die Vorlage angezeigt wird der **neues Projekt** (Dialogfeld), und wie Vorlagenparameter ersetzt werden.  Eine VSTEMPLATE-Datei ist eine XML-Datei, die beschreibt, wie Quelldateien eingeschlossen werden sollen, wenn ein Projekt mithilfe der Projektvorlage für das System erstellt wurde. Das Projektsystem selbst wird durch das Erfassen der VSTEMPLATE-Datei und die Quelldateien in einer ZIP-Datei erstellt und bereitgestellt durch Kopieren die ZIP-Datei an einem Speicherort, der Visual Studio bekannt ist. Dieser Vorgang wird weiter unten in dieser exemplarischen Vorgehensweise ausführlich erläutert.  
  
1.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], öffnen Sie die SimpleProject-Projektmappe, die Sie, indem Sie die folgenden erstellt [erstellen eine grundlegende Projektsystem, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2.  Suchen Sie in der Datei SimpleProjectPackage.cs die ProvideProjectFactory-Attribut. Ersetzen Sie durch den zweiten Parameter (den Projektnamen) mit dem Wert Null, und der vierte Parameter (der Pfad in den Projektordner für die Vorlage) ". \\\NullPath "wie folgt.  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
        ".\\NullPath",  
    LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  Fügen Sie eine XML-Datei namens SimpleProject.vstemplate zum \Templates\Projects\SimpleProject\ Ordner hinzu.  
  
4.  Ersetzen Sie den Inhalt der SimpleProject.vstemplate durch den folgenden Code ein.  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
      <TemplateData>  
        <Name>SimpleProject Application</Name>  
        <Description>  
            A project for creating a SimpleProject application  
         </Description>  
         <Icon>SimpleProject.ico</Icon>  
         <ProjectType>SimpleProject</ProjectType>  
      </TemplateData>  
      <TemplateContent>  
        <Project File="SimpleProject.myproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
              Program.cs  
          </ProjectItem>  
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">  
             AssemblyInfo.cs  
          </ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
5.  In der **Eigenschaften** Fenster, wählen Sie alle fünf Dateien in den Ordner \Templates\Projects\SimpleProject\ und legen die **Buildvorgang** auf **ZipProject**.  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 Die \<TemplateData > Abschnitt bestimmt den Speicherort und die Darstellung des Projekttyps SimpleProject in der **neues Projekt** Dialogfeld wie folgt:  
  
-   Die \<Name > Element benennt die Projektvorlage SimpleProject Anwendung sein.  
  
-   Die \<Beschreibung >-Element enthält die Beschreibung, die in der **neues Projekt** (Dialogfeld), wenn die Projektvorlage ausgewählt ist.  
  
-   Die \<Symbol ">-Element gibt an, das Symbol, das zusammen mit den Projekttyp SimpleProject angezeigt wird.  
  
-   Die \<ProjectType >-Element benennt den Projekttyp in der **neues Projekt** (Dialogfeld). Dieser Name wird die Projektparameter-Name des Attributs ProvideProjectFactory ersetzt.  
  
    > [!NOTE]
    >  Die \<ProjectType > Element übereinstimmen muss die `LanguageVsTemplate` Argument der `ProvideProjectFactory` Attribut in der Datei SimpleProjectPackage.cs.  
  
 Die \<TemplateContent > Abschnitt wird beschrieben, diese Dateien, die generiert werden, wenn ein neues Projekt erstellt wird:  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   AssemblyInfo.cs  
  
 Alle drei Dateien haben `ReplaceParameters` auf True festgelegt, wodurch Ersetzung von Typparametern.  Wurde die Datei "Program.cs" `OpenInEditor` auf True festgelegt, die bewirkt, dass die Datei im Code-Editor geöffnet werden, wenn ein Projekt erstellt wird.  
  
 Weitere Informationen zu den Elementen in der Visual Studio-Vorlage Schema finden Sie unter der [Schemareferenz zu Visual Studio-Vorlage](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Wenn ein Projekt mehrere Visual Studio-Vorlagen enthält, wird jede Vorlage in einem separaten Ordner. Jede Datei in diesem Ordner benötigen die **Buildvorgang** festgelegt **ZipProject**.  
  
## <a name="adding-a-minimal-vsct-file"></a>Hinzufügen einer minimalen VSCT-Datei  
 Im Modus der Installation eine neue oder geänderte Visual Studio-Vorlage erkennen muss Visual Studio ausgeführt werden. Setupmodus erfordert eine VSCT-Datei vorhanden sein. Aus diesem Grund müssen Sie eine minimale VSCT-Datei zum Projekt hinzufügen.  
  
1.  Fügen Sie eine XML-Datei mit dem Namen SimpleProject.vsct SimpleProject-Projekt hinzu.  
  
2.  Ersetzen Sie den Inhalt der Datei SimpleProject.vsct durch den folgenden Code ein.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  Legen Sie die **Buildvorgang** dieser Datei auf **VSCTCompile**. Hierzu können Sie nur in der CSPROJ-Datei nicht in der **Eigenschaften** Fenster. Stellen Sie sicher, dass die **Buildvorgang** dieser Datei wird festgelegt **keine** an diesem Punkt.  
  
    1.  Mit der rechten Maustaste des SimpleProject-Knotens, und klicken Sie dann auf **SimpleProject.csproj bearbeiten**.  
  
    2.  Suchen Sie in der CSPROJ-Datei das SimpleProject.vsct-Element.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Ändern Sie den Buildvorgang, **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  die Projektdatei und schließen Sie Editor.  
  
    5.  Speichern Sie den Knoten SimpleProject und dann in der **Projektmappen-Explorer** klicken Sie auf **Projekt erneut laden**.  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Untersuchen der Visual Studio-Vorlage Buildschritte  
 VSPackage-Projekterstellungssystems führt Visual Studio in der Regel im Setupmodus, wenn die VSTEMPLATE-Datei geändert, oder das Projekt mit der VSTEMPLATE-Datei wird neu erstellt. Sie können durch Festlegen von MSBuild den Ausführlichkeitsgrad auf Normal oder höher nachvollziehen.  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie die **Projekte und Projektmappen** Knoten, und wählen Sie dann **erstellen und führen Sie**.  
  
3.  Legen Sie **MSBuild-Projektbuilds Ausgabe Ausführlichkeit** auf **Normal**. Klicken Sie auf **OK**.  
  
4.  Das SimpleProject-Projekt neu.  
  
 Der Schritt der Erstellung die ZIP-Projektdatei erstellen, sollte im folgende Beispiel entsprechen.  
  
```  
ZipProjects:  
1>  Zipping ProjectTemplates  
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".  
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip  
1>ZipItems:  
1>  Zipping ItemTemplates  
1>  SimpleProject ->  
```  
  
## <a name="deploying-a-visual-studio-template"></a>Bereitstellen einer Visual Studio-Vorlage  
 Visual Studio-Vorlagen enthalten keine Pfadinformationen. Aus diesem Grund muss die ZIP-Vorlagendatei an einem Speicherort bereitgestellt werden, das Visual Studio bekannt ist. Der Speicherort des Ordners ProjectTemplates ist in der Regel  **\<%LocalAppData% > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**.  
  
 Um Ihr Projekt Factory bereitstellen zu können, muss das Installationsprogramm über Administratorrechte verfügen. Vorlagen unter dem Knoten der Visual Studio-Installation bereitgestellt: **...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates**.  
  
## <a name="testing-a-visual-studio-template"></a>Testen eine Visual Studio-Vorlage  
 Testen Sie Ihr Projekt-Factory, um festzustellen, ob es eine Projekthierarchie mithilfe der Visual Studio-Vorlage erstellt.  
  
1.  Zurücksetzen der experimentellen Instanz von Visual Studio SDK.  
  
     Auf [!INCLUDE[win7](../debugger/includes/win7_md.md)]: finden Sie im Menü Start den **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** Ordner, und wählen Sie dann **Zurücksetzen die Microsoft Visual Studio experimentellen Instanz**.  
  
     In höheren Versionen von Windows: Geben Sie auf der Startbildschirm **Zurücksetzen von Microsoft Visual Studio \<Version > experimentelle Instanz**.  
  
2.  Ein Eingabeaufforderungsfenster wird angezeigt. Wenn Sie sehen die Wörter `Press any key to continue`, drücken die EINGABETASTE. Wenn das Fenster geschlossen wurde, öffnen Sie Visual Studio.  
  
3.  Das SimpleProject-Projekt neu, und starten Sie das Debuggen. Die experimentelle Instanz angezeigt wird.  
  
4.  Erstellen Sie in der experimentellen Instanz ein SimpleProject-Projekt ein. In der **neues Projekt** wählen Sie im Dialogfeld **SimpleProject**.  
  
5.  Eine neue Instanz der SimpleProject sollte angezeigt werden.  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>Erstellen einen Projekt Typ untergeordneter Knoten  
 Sie können einen Projektknoten-Typ in einen untergeordneten Knoten hinzufügen der **neues Projekt** (Dialogfeld).  Für den Projekttyp SimpleProject haben Sie z. B. untergeordnete Knoten für konsolenanwendungen, Fenster-Anwendungen, Webanwendungen und usw.  
  
 Untergeordnete Knoten werden erstellt, indem Sie die Projektdatei ändern und hinzufügen \<OutputSubPath > untergeordnete Elemente mit dem \<ZipProject > Elemente. Wenn eine Vorlage, die während der Erstellung oder Bereitstellung kopiert wird, wird jeder untergeordnete Knoten einen Unterordner des Projektordners Vorlagen an.  
  
 In diesem Abschnitt wird gezeigt, wie einen Konsole untergeordneten Knoten für den Projekttyp SimpleProject erstellt wird.  
  
1.  Benennen Sie den Ordner \Templates\Projects\SimpleProject\ in \Templates\Projects\ConsoleApp\\.  
  
2.  In der **Eigenschaften** Fenster, wählen Sie alle fünf Dateien im Ordner "\Templates\Projects\ConsoleApp\", und stellen Sie sicher, dass die **Buildvorgang** festgelegt ist, um **ZipProject**.  
  
3.  Fügen Sie in der Datei SimpleProject.vstemplate die folgende Zeile am Ende der \<TemplateData > Abschnitt unmittelbar vor dem Endtag.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Dies bewirkt, dass die Vorlage für Konsolenanwendungen aus angezeigt werden, in der Konsole untergeordnete Knoten und in der SimpleProject übergeordneten Knoten, eine Ebene oberhalb des untergeordneten Knotens ist.  
  
4.  Speichern Sie die SimpleProject.vstemplate-Datei.  
  
5.  Fügen Sie in der CSPROJ-Datei \<OutputSubPath > auf jedes Element ZipProject. Entladen Sie das Projekt als vorher, und bearbeiten Sie die Projektdatei.  
  
6.  Suchen Sie die \<ZipProject > Elemente. Zu jedem \<ZipProject >-Element, Hinzufügen einer \<OutputSubPath > Element, und geben Sie ihm den Wert Konsole. Die ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>  
    ```  
  
7.  Fügen Sie der \<PropertyGroup > in der Projektdatei:  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  Speichern Sie die Projektdatei, und Laden Sie das Projekt erneut.  
  
## <a name="testing-the-project-type-child-node"></a>Testen das Projekt Typ untergeordneter Knoten  
 Testen Sie die geänderte Projektdatei, finden, ob die **Konsole** untergeordneten Knoten befindet sich im die **neues Projekt** (Dialogfeld).  
  
1.  Führen Sie die **Zurücksetzen der Microsoft Visual Studio experimentellen Instanz** Tool.  
  
2.  Das SimpleProject-Projekt neu, und starten Sie das Debuggen. Die experimentelle Instanz sollte angezeigt werden.  
  
3.  In der **neues Projekt** Dialogfeld klicken Sie auf die **SimpleProject** Knoten. Die **Konsolenanwendung** Vorlage sollte angezeigt werden, der **Vorlagen** Bereich.  
  
4.  Erweitern Sie die **SimpleProject** Knoten. Die **Konsole** untergeordneter Knoten sollte angezeigt werden. Die **SimpleProject Anwendung** Vorlage wird weiterhin angezeigt, in der **Vorlagen** Bereich.  
  
5.  sein. Klicken Sie auf **"Abbrechen"** und Beenden des Debuggens  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>Ersetzen der Projekt-Vorlagenparameter  
 [Erstellen eine grundlegende Projektsystem, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md) wurde gezeigt, wie zum Überschreiben der `ProjectNode.AddFileFromTemplate` Methode, um eine grundlegende Art der Ersetzung von Typparametern Vorlage auszuführen. In diesem Abschnitt erfahren, wie die komplexere Vorlagenparameter in Visual Studio verwenden.  
  
 Beim Erstellen eines Projekts mit Visual Studio-Vorlage in der **neues Projekt** Dialogfeld Vorlage durch Parameter ersetzt werden Zeichenfolgen, die zum Anpassen des Projekts. Ein Template-Parameter ist ein spezielles Token, das beginnt und endet mit einem Dollarzeichen, z. B. $time$. Die folgenden beiden Parameter sind besonders nützlich zum Aktivieren der Anpassung in Projekten, die auf der Vorlage basieren:  
  
-   $GUID [1-10] $ wird durch eine neue Guid ersetzt. Sie können bis zu 10 eindeutige GUIDs, z. B. $guid1$ angeben.  
  
-   $safeprojectname$ wird durch den Benutzer in der angegebene Name der **neues Projekt** (Dialogfeld), alle unsicheren Zeichen sowie Leerzeichen entfernt.  
  
 Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
#### <a name="to-substitute-project-template-parameters"></a>Zum Ersetzen der Projekt-Vorlagenparameter  
  
1.  Entfernen Sie in der Datei SimpleProjectNode.cs die `AddFileFromTemplate` Methode.  
  
2.  Suchen Sie in der Datei \Templates\Projects\ConsoleApp\SimpleProject.myproj die \<RootNamespace > Eigenschaft, und ändern Sie den Wert in $safeprojectname$.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  Ersetzen Sie in der Datei \Templates\Projects\SimpleProject\Program.cs den Inhalt der Datei durch den folgenden Code ein:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace $safeprojectname$  
    {  
        [Guid("$guid1$")]  
        public class $safeprojectname$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
4.  Das SimpleProject-Projekt neu, und starten Sie das Debuggen. Die experimentelle Instanz sollte angezeigt werden.  
  
5.  Erstellen Sie eine neue SimpleProject-Konsolenanwendung. (In der **-Projekttypen** klicken Sie im Bereich **SimpleProject**. Unter **Visual Studio installierte Vorlagen**Option **Konsolenanwendung**.)  
  
6.  Öffnen Sie "Program.cs", in das Projekt neu erstellt. Es sollte etwa wie folgt aussehen (GUID-Werte in der Datei variieren.):  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace Console_Application1  
    {  
        [Guid("00000000-0000-0000-00000000-00000000)"]  
        public class Console_Application1  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
## <a name="creating-a-project-property-page"></a>Erstellen einer Projekteigenschaftsseite  
 Sie können eine Eigenschaftenseite für den Projekttyp erstellen, sodass Benutzer anzeigen und Ändern von Eigenschaften in Projekten, die basierend auf der Vorlage basieren können. In diesem Abschnitt wird gezeigt, wie eine Eigenschaftenseite Konfiguration unabhängig zu erstellen. Diese grundlegenden Eigenschaftenseite verwendet eine Eigenschaftenraster, um die öffentlichen Eigenschaften anzuzeigen, die Sie in der Eigenschaft Page-Klasse verfügbar machen.  
  
 Leiten Sie eine Eigenschaft Seitenklasse aus der `SettingsPage` Basisklasse. Das Eigenschaftenraster gebotenen der `SettingsPage` Klasse erkennt die meisten primitiven Datentypen und weiß, wie sie anzuzeigen.  Darüber hinaus die `SettingsPage` Klasse weiß, wie Eigenschaftswerte in der Projektdatei beibehalten werden.  
  
 Die Eigenschaftenseite, die Sie in diesem Abschnitt erstellen können Sie die alter und speichern Sie diese Projekteigenschaften:  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace.  
  
1.  Fügen Sie in der Datei SimpleProjectPackage.cs Folgendes `ProvideObject` -Attribut auf die `SimpleProjectPackage` Klasse:  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))]  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     Dadurch wird die Eigenschaft Page-Klasse registriert `GeneralPropertyPage` mit COM.  
  
2.  Fügen Sie in der Datei SimpleProjectNode.cs beiden überschriebenen Methoden die `SimpleProjectNode` Klasse:  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
        return result;  
    }  
    protected override Guid[] GetPriorityProjectDesignerPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
         return result;  
    }  
    ```  
  
     Beide Methoden geben ein Array von GUIDs "Eigenschaftenseite" zurück.  Die GeneralPropertyPage-GUID ist das einzige Element im Array, sodass der **Eigenschaftenseiten** (Dialogfeld), wird nur eine Seite angezeigt.  
  
3.  Fügen Sie eine Klassendatei namens GeneralPropertyPage.cs SimpleProject-Projekt hinzu.  
  
4.  Ersetzen Sie den Inhalt dieser Datei mithilfe des folgenden Codes:  
  
    ```  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Project;  
    using System.ComponentModel;  
  
    namespace SimpleProject  
    {  
        [ComVisible(true)]  
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]  
        public class GeneralPropertyPage : SettingsPage  
        {  
            private string assemblyName;  
            private OutputType outputType;  
            private string defaultNamespace;  
  
            public GeneralPropertyPage()  
            {  
                this.Name = "General";  
            }  
  
            [Category("AssemblyName")]  
            [DisplayName("AssemblyName")]  
            [Description("The output file holding assembly metadata.")]  
            public string AssemblyName  
            {  
                get { return this.assemblyName; }  
            }  
            [Category("Application")]  
            [DisplayName("OutputType")]  
            [Description("The type of application to build.")]  
            public OutputType OutputType  
            {  
                get { return this.outputType; }  
                set { this.outputType = value; this.IsDirty = true; }  
            }  
            [Category("Application")]  
            [DisplayName("DefaultNamespace")]  
            [Description("Specifies the default namespace for added items.")]  
            public string DefaultNamespace  
            {  
                get { return this.defaultNamespace; }  
                set { this.defaultNamespace = value; this.IsDirty = true; }  
            }  
  
            protected override void BindProperties()  
            {  
                this.assemblyName = this.ProjectMgr.GetProjectProperty(  
    "AssemblyName", true);  
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
    "RootNamespace", false);  
  
                string outputType = this.ProjectMgr.GetProjectProperty(  
    "OutputType", false);  
                this.outputType =   
    (OutputType)Enum.Parse(typeof(OutputType), outputType);  
            }  
  
            protected override int ApplyChanges()  
            {  
                this.ProjectMgr.SetProjectProperty(  
    "AssemblyName", this.assemblyName);  
                this.ProjectMgr.SetProjectProperty(  
    "OutputType", this.outputType.ToString());  
                this.ProjectMgr.SetProjectProperty(  
    "RootNamespace", this.defaultNamespace);  
                this.IsDirty = false;  
  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    ```  
  
     Die `GeneralPropertyPage` Klasse bereitstellt, die drei öffentlichen Eigenschaften AssemblyName OutputType und RootNamespace. Da der AssemblyName keine Set-Methode besitzt, wird er als schreibgeschützte Eigenschaft angezeigt. OutputType ist eine Enumerationskonstante, damit es als Dropdownliste angezeigt wird.  
  
     Die `SettingsPage` Basisklasse stellt `ProjectMgr` um die Eigenschaften persistent zu speichern. Die `BindProperties` -Methode verwendet `ProjectMgr` der permanenten Eigenschaftswerte abrufen und die entsprechenden Eigenschaften festlegen.  Die `ApplyChanges` -Methode verwendet `ProjectMgr` rufen Sie die Werte der Eigenschaften und der Projektdatei beibehalten werden. Die Eigenschaftensatz-Methode legt `IsDirty` auf true festlegen, um anzugeben, dass die Eigenschaften beibehalten werden müssen.  Persistenz tritt auf, wenn Sie das Projekt oder die Projektmappe speichern.  
  
5.  Die SimpleProject-Projektmappe neu erstellen und mit dem Debuggen beginnen. Die experimentelle Instanz sollte angezeigt werden.  
  
6.  Erstellen Sie eine neue SimpleProject-Anwendung, in der experimentellen Instanz.  
  
7.  Visual Studio ruft die Projekt-Factory zum Erstellen eines Projekts mithilfe der Visual Studio-Vorlage. Die neue Datei "Program.cs" wird im Code-Editor geöffnet.  
  
8.  Mit der rechten Maustaste des Projektknoten im **Projektmappen-Explorer**, und klicken Sie dann auf **Eigenschaften**. Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>Testen die Eigenschaftenseite des Projekts  
 Sie können jetzt testen, ob Sie ändern können, und Ändern von Eigenschaftenwerten.  
  
1.  In der **MyConsoleApplication Eigenschaftenseiten** ändern Sie im Dialogfeld die **DefaultNamespace** auf **"MyApplication"**.  
  
2.  Wählen Sie die **OutputType** -Eigenschaft, und wählen Sie dann **-Klassenbibliothek**.  
  
3.  Klicken Sie auf **übernehmen**, und klicken Sie dann auf **OK**.  
  
4.  Öffnen Sie erneut die **Eigenschaftenseiten** Dialogfeld Feld, und stellen Sie sicher, dass die Änderungen persistent gespeichert wurden.  
  
5.  Schließen Sie die experimentelle Instanz von Visual Studio.  
  
6.  Öffnen Sie die experimentelle Instanz erneut.  
  
7.  Öffnen Sie erneut die **Eigenschaftenseiten** Dialogfeld Feld, und stellen Sie sicher, dass die Änderungen persistent gespeichert wurden.  
  
8.  Schließen Sie die experimentelle Instanz von Visual Studio.  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")