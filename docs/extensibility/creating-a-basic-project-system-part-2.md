---
title: Erstellen eines grundlegenden Projektsystems, Teil 2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fb99c1b07fd2627f9dab6baed12bce60c79dd9a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988284"
---
# <a name="create-a-basic-project-system-part-2"></a>Erstellen eines grundlegenden Projektsystems, Teil 2
Der ersten exemplarischen Vorgehensweise in dieser Serie [erstellen ein grundlegenden Projektsystems, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md), wird das Erstellen eines grundlegenden Projektsystems veranschaulicht. In dieser exemplarischen Vorgehensweise baut auf dem Projektsystem für die basic-eine Visual Studio-Vorlage auf einer Eigenschaftenseite und andere Funktionen. Sie müssen die erste exemplarischen Vorgehensweise abschließen, bevor Sie mit dieser beginnen.  
  
 In dieser exemplarischen Vorgehensweise erfahren, wie Sie ein Projekt zu erstellen, die die Projekt-Dateinamenerweiterung *.myproj*. Um die exemplarische Vorgehensweise abzuschließen, müssen Sie nicht Ihre eigene Sprache erstellt werden, weil die exemplarischen Vorgehensweise aus dem vorhandenen Visual C#-Projektsystem nutzt Teile.  
  
 In dieser exemplarischen Vorgehensweise erfahren, wie diese Aufgaben auszuführen:  
  
-   Erstellen Sie eine Visual Studio-Vorlage.  
  
-   Bereitstellen einer Visual Studio-Vorlage.  
  
-   Erstellen Sie eine untergeordnete Projekttypknoten in der **neues Projekt** Dialogfeld.  
  
-   Aktivieren Sie die parameterersetzung in der Visual Studio-Vorlage.  
  
-   Erstellen Sie eine Eigenschaftenseite des Projekts.  
  
> [!NOTE]
>  Die Schritte in dieser exemplarischen Vorgehensweise basiert auf einem C#-Projekt. Jedoch mit Ausnahme von Details wie z. B. Dateinamenerweiterungen und Code können die gleichen Schritte für ein Visual Basic-Projekt Sie.  
  
## <a name="create-a-visual-studio-template"></a>Erstellen Sie eine Visual Studio-Vorlage  
 [Erstellen ein grundlegenden Projektsystems, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md) veranschaulicht das Erstellen einer grundlegenden Projektvorlage und an das Projektsystem hinzufügen. Darüber hinaus erfahren Sie, wie diese Vorlage mit Visual Studio registrieren mit dem <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> -Attribut, das den vollständigen Pfad der schreibt die *\\Templates\Projects\SimpleProject\\* Ordner im System die Registrierung.  
  
 Mithilfe von Visual Studio-Vorlage (*VSTEMPLATE* Datei) statt einer basic-Projektvorlage, können Sie steuern, wie die Vorlage wird die **neues Projekt** Dialogfeld und wie bei Vorlagenparametern wird ersetzt.  Ein *VSTEMPLATE* Datei ist eine XML-Datei, die beschreibt, wie Quelldateien enthalten sein, wenn ein Projekt mithilfe der Projektvorlage für das System erstellt wird. Das Projektsystem selbst wird erstellt, indem Sie das Sammeln von der *VSTEMPLATE* -Datei und die Quelldateien in eine *ZIP* Datei, und die Bereitstellung durch Kopieren der *ZIP* Datei an einem Speicherort, der Visual Studio bekannt. Dieser Prozess wird weiter unten in dieser exemplarischen Vorgehensweise ausführlicher erläutert.  
  
1. In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], öffnen Sie die SimpleProject-Projektmappe, die Sie, indem Sie die folgenden erstellt [erstellen ein grundlegenden Projektsystems, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2. In der *SimpleProjectPackage.cs* Datei, suchen Sie das ProvideProjectFactory-Attribut. Ersetzen Sie durch den zweiten Parameter (Projektname) mit Null, und der vierte Parameter (der Pfad des Vorlagenordners Projekt) ". \\\NullPath "wie folgt.  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. Fügen Sie eine XML-Datei mit dem Namen *SimpleProject.vstemplate* auf die *\\Templates\Projects\SimpleProject\\* Ordner.  
  
4. Ersetzen Sie den Inhalt der *SimpleProject.vstemplate* durch den folgenden Code.  
  
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
  
5. In der **Eigenschaften** wählen Sie im Fenster alle fünf Dateien in die *\\Templates\Projects\SimpleProject\\* Ordner und legen die **Buildvorgang** um **ZipProject**.  
  
   ![Einfachen-Projektordner](../extensibility/media/simpproj2.png "SimpProj2")  
  
   Die \<TemplateData > Abschnitt bestimmt den Speicherort und die Darstellung des Projekttyps SimpleProject in die **neues Projekt** Dialogfeld wie folgt:  
  
- Die \<Name >-Element benennt die Projektvorlage SimpleProject Anwendung sein.  
  
- Die \<Beschreibung >-Element enthält die Beschreibung, die in angezeigt wird der **neues Projekt** im Dialogfeld, wenn die Projektvorlage ausgewählt ist.  
  
- Die \<Symbol >-Element gibt an, das Symbol, das zusammen mit den Projekttyp SimpleProject angezeigt wird.  
  
- Die \<ProjectType >-Element benennt den Projekttyp in der **neues Projekt** Dialogfeld. Dieser Name wird den Projekt-Name-Parameter des Attributs ProvideProjectFactory ersetzt.  
  
  > [!NOTE]
  >  Die \<ProjectType > Element muss übereinstimmen der `LanguageVsTemplate` Argument der `ProvideProjectFactory` Attribut in der Datei SimpleProjectPackage.cs.  
  
  Die \<TemplateContent > Abschnitt wird beschrieben, diese Dateien, die generiert werden, wenn ein neues Projekt erstellt wird:  
  
- *SimpleProject.myproj*  
  
- *Program.cs*  
  
- *AssemblyInfo.cs*  
  
  Alle drei Dateien `ReplaceParameters` auf True festgelegt, die parameterersetzung ermöglicht.  Die *"Program.cs"* Datei `OpenInEditor` auf True festgelegt, wodurch die Datei im Code-Editor geöffnet werden, wenn ein Projekt erstellt wird.  
  
  Weitere Informationen zu den Elementen im Visual Studio-Vorlage Schema finden Sie unter den [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Wenn ein Projekt mehrere Visual Studio-Vorlagen enthält, ist jede Vorlage, in einem separaten Ordner. Jede Datei in diesem Ordner müssen die **Buildvorgang** festgelegt **ZipProject**.  
  
## <a name="adding-a-minimal-vsct-file"></a>Hinzufügen einer minimalen VSCT-Datei  
 Visual Studio muss im Modus der Installation eine neue oder geänderte Visual Studio-Vorlage erkennt ausgeführt werden. Setupmodus erfordert, dass eine *VSCT* Datei vorhanden sein. Aus diesem Grund müssen Sie eine minimale hinzufügen *VSCT* Datei zum Projekt.  
  
1.  Fügen Sie eine XML-Datei mit dem Namen *SimpleProject.vsct* dem SimpleProject-Projekt.  
  
2.  Ersetzen Sie den Inhalt von der *SimpleProject.vsct* -Datei mit den folgenden Code.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  Legen Sie die **Buildvorgang** dieser Datei auf **VSCTCompile**. Hierzu können Sie nur in der *csproj* Datei nicht in der **Eigenschaften** Fenster. Stellen Sie sicher, dass die **Buildvorgang** dieser Datei nastaven NA hodnotu **keine** an diesem Punkt.  
  
    1.  Mit der rechten Maustaste des SimpleProject-Knotens, und klicken Sie dann auf **bearbeiten SimpleProject.csproj**.  
  
    2.  In der *csproj* Datei, suchen Sie nach der *SimpleProject.vsct* Element.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Ändern Sie den Buildvorgang auf **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  die Projektdatei und schließen Sie den Editor.  
  
    5.  Speichern Sie den Knoten SimpleProject und dann in der **Projektmappen-Explorer** klicken Sie auf **Projekt erneut laden**.  
  
## <a name="examine-the-visual-studio-template-build-steps"></a>Überprüfen Sie die Schritte im Buildprozess Visual Studio-Vorlage  
 Das Buildsystem für VSPackage-Projekt wird Visual Studio in der Regel im Setupmodus ausgeführt bei der *VSTEMPLATE* Datei geändert wird, oder das Projekt, enthält die *VSTEMPLATE* neu erstellt wird. Sie können durch Festlegen den Ausführlichkeitsgrad der MSBuild, Normal oder höher folgen.  
  
1. Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2. Erweitern Sie die **Projekte und Projektmappen** Knoten, und wählen Sie dann **erstellen und ausführen**.  
  
3. Legen Sie **MSBuild Projektbuildausgabe** zu **Normal**. Klicken Sie auf **OK**.  
  
4. Erstellen Sie das SimpleProject-Projekt neu.  
  
   Vom Schritt zum Erstellen der *ZIP* Projektdatei sollte im folgende Beispiel ähneln.  
  
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
  
## <a name="deploy-a-visual-studio-template"></a>Bereitstellen einer Visual Studio-Vorlage  
 Visual Studio-Vorlagen enthalten keine Pfadinformationen. Aus diesem Grund die Vorlage *ZIP* Datei muss bereitgestellt werden, an einem Speicherort an, das Visual Studio bekannt ist. Der Speicherort des Ordners ProjectTemplates ist in der Regel *< % LocalAppData% > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates*.  
  
 Zum Bereitstellen Ihrer Projektfactory muss das Installationsprogramm über Administratorrechte verfügen. Vorlagen unter dem Knoten für Visual Studio-Installation bereitgestellt: *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*.  
  
## <a name="test-a-visual-studio-template"></a>Testen Sie Visual Studio-Vorlage  
 Testen Sie Ihr Projekt-Factory, um festzustellen, ob es sich bei eine Projekthierarchie mithilfe der Visual Studio-Vorlage erstellt.  
  
1. Zurücksetzen der experimentellen Instanz von Visual Studio SDK.  
  
    Auf [!INCLUDE[win7](../debugger/includes/win7_md.md)]: Auf der **starten** Menü finden Sie die **Microsoft Visual Studio und Microsoft Visual Studio SDK/Tools** Ordner, und wählen Sie dann **Microsoft Visual Studio-experimentelle Instanz vonZurücksetzen**.  
  
    In höheren Versionen von Windows: Auf der **starten** geben **Microsoft Visual Studio zurücksetzen \<Version > experimentelle Instanz**.  
  
2. Ein Eingabeaufforderungsfenster wird angezeigt. Wenn Sie sehen, die Wörter **drücken Sie eine beliebige Taste, um den Vorgang fortzusetzen**, klicken Sie auf **EINGABETASTE**. Wenn das Fenster geschlossen wurde, öffnen Sie Visual Studio.  
  
3. Das SimpleProject-Projekt neu erstellen und mit dem Debuggen beginnen. Die experimentelle Instanz angezeigt wird.  
  
4. Erstellen Sie in der experimentellen Instanz ein SimpleProject-Projekt ein. In der **neues Projekt** wählen Sie im Dialogfeld **SimpleProject**.  
  
5. Eine neue Instanz der SimpleProject sollte angezeigt werden.  
  
   ![Einfaches Projekt neue Instanz](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")  
  
   ![Meine neuen Projektinstanz](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")  
  
## <a name="create-a-project-type-child-node"></a>Erstellen Sie einen Projekt Typ untergeordneter Knoten  
 Sie können eine Projekttypknoten in einen untergeordneten Knoten hinzufügen der **neues Projekt** Dialogfeld.  Für den Projekttyp SimpleProject, könnten Sie z. B. untergeordneten Knoten für konsolenanwendungen, Fenster-Anwendungen, Webanwendungen und So weiter verfügen.  
  
 Untergeordnete Knoten werden erstellt, indem Sie die Projektdatei ändern und hinzufügen \<OutputSubPath > untergeordneten Elemente für die \<ZipProject > Elemente. Wenn während der Erstellung oder Bereitstellung eine Vorlage kopiert wird, wird jedem untergeordneten Knoten einen Unterordner des Projektordners Vorlagen.  
  
 In diesem Abschnitt zeigt, wie mit einen Konsole untergeordneter Knoten für den Projekttyp SimpleProject erstellt wird.  
  
1.  Benennen Sie die *\\Templates\Projects\SimpleProject\\* Ordner  *\\Templates\Projects\ConsoleApp\\*.  
  
2.  In der **Eigenschaften** wählen Sie im Fenster alle fünf Dateien in die *\\Templates\Projects\ConsoleApp\\* Ordner, und stellen Sie sicher, dass die **Buildvorgang**nastaven NA hodnotu **ZipProject**.  
  
3.  Fügen Sie in der Datei SimpleProject.vstemplate die folgende Zeile am Ende der \<TemplateData > Abschnitt unmittelbar vor dem schließenden Tag.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Dies bewirkt, dass die Konsolenanwendung Vorlage angezeigt werden, sowohl in der Konsole untergeordnete Knoten als auch im SimpleProject übergeordneten Knoten, der eine Ebene über den untergeordneten Knoten ist.  
  
4.  Speichern Sie die *SimpleProject.vstemplate* Datei.  
  
5.  In der *csproj* hinzufügen \<OutputSubPath > auf die einzelnen Elemente der ZipProject. Entladen Sie das Projekt, wie zuvor, und Bearbeiten der Projektdatei.  
  
6.  Suchen Sie die \<ZipProject > Elemente. Auf die einzelnen \<ZipProject >-Element hinzufügen einer \<OutputSubPath > Element und weisen Sie ihm den Wert-Konsole. Die ZipProject  
  
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
  
7.  Fügen Sie Folgendes \<PropertyGroup > an der Projektdatei:  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  Speichern Sie die Projektdatei, und Laden Sie das Projekt.  
  
## <a name="test-the-project-type-child-node"></a>Testen Sie den untergeordneten Projekttypknoten  
 Testen Sie die geänderte Projektdatei, um festzustellen, ob die **Konsole** untergeordneten Knoten befindet sich im die **neues Projekt** Dialogfeld.  
  
1. Führen Sie die **Zurücksetzen der Microsoft Visual Studio experimentelle Instanz** Tool.  
  
2. Das SimpleProject-Projekt neu erstellen und mit dem Debuggen beginnen. Die experimentelle Instanz sollten angezeigt werden.  
  
3. In der **neues Projekt** Dialogfeld klicken Sie auf die **SimpleProject** Knoten. Die **Konsolenanwendung** Vorlage sollte angezeigt werden, der **Vorlagen** Bereich.  
  
4. Erweitern Sie die **SimpleProject** Knoten. Die **Konsole** untergeordneter Knoten sollte angezeigt werden. Die **SimpleProject Anwendung** Vorlage wird weiterhin angezeigt, in der **Vorlagen** Bereich.  
  
5. Klicken Sie auf **Abbrechen** und das Debuggen beendet.  
  
   ![Einfaches Projekt Rollup](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")  
  
   ![Einfaches Projekt-Konsolenknoten](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substitute-project-template-parameters"></a>Projekt-Vorlagenparameter ersetzen  
 [Erstellen eines grundlegenden Projektsystems, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md) wurde gezeigt, wie Sie überschreiben die `ProjectNode.AddFileFromTemplate` Methode, um eine einfache Art von Vorlage Parameter ersetzt werden. In diesem Abschnitt erfahren, wie Sie die Parameter der höher entwickelten Visual Studio-Vorlage zu verwenden.  
  
 Bei der Erstellung eines Projekts mit Visual Studio-Vorlage in der **neues Projekt** Dialogfeld Vorlage, die durch Parameter ersetzt werden Zeichenfolgen, um das Projekt anpassen. Ein Template-Parameter ist ein spezieller Token, das beginnt und endet mit einem Dollarzeichen, z. B. $time$. Die folgenden beiden Parameter sind besonders nützlich zum Aktivieren der Anpassung in Projekten, die in der Vorlage basieren:  
  
- $GUID [1-10] $ wird durch eine neue Guid ersetzt. Sie können bis zu 10 eindeutige GUIDs, z. B. $guid1$ angeben.  
  
- $safeprojectname$ wird von einem Benutzer in der bereitgestellte Name der **neues Projekt** Dialogfeld geändert, um alle unsicheren Zeichen sowie Leerzeichen zu entfernen.  
  
  Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
### <a name="to-substitute-project-template-parameters"></a>Projekt-Vorlagenparameter ersetzen  
  
1.  In der *SimpleProjectNode.cs* Datei, entfernen Sie die `AddFileFromTemplate` Methode.  
  
2.  In der  *\\Templates\Projects\ConsoleApp\SimpleProject.myproj* Datei, suchen Sie nach der \<RootNamespace >-Eigenschaft und ändern Sie seinen Wert $safeprojectname $.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  In der  *\\Templates\Projects\SimpleProject\Program.cs* Datei, ersetzen Sie den Inhalt der Datei mit dem folgenden Code:  
  
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
  
4.  Das SimpleProject-Projekt neu erstellen und mit dem Debuggen beginnen. Die experimentelle Instanz sollten angezeigt werden.  
  
5.  Erstellen Sie eine neue SimpleProject-Konsolenanwendung. (In der **Projekttypen** wählen Sie im Bereich **SimpleProject**. Unter **Visual Studio installierte Vorlagen**Option **Konsolenanwendung**.)  
  
6.  Öffnen Sie in das neu erstellte Projekt, *"Program.cs"*. Es sollte in etwa wie folgt aussehen (GUID-Werte in der Datei variieren.):  
  
    ```csharp  
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
  
## <a name="create-a-project-property-page"></a>Erstellen Sie eine Projekt-Eigenschaftenseite  
 Sie können eine Eigenschaftenseite für den Projekttyp erstellen, sodass Benutzer anzeigen und Ändern der Eigenschaften in Projekten, die basierend auf der Vorlage basieren können. In diesem Abschnitt erfahren Sie, wie Sie eine Konfiguration unabhängig Eigenschaftenseite zu erstellen. Diese grundlegende Eigenschaft verwendet ein Eigenschaftenraster zum Anzeigen der öffentlichen Eigenschaften, die Sie in der Eigenschaft Page-Klasse verfügbar machen.  
  
 Leiten Sie die Eigenschaft-Seite-Klasse aus der `SettingsPage` Basisklasse. Das Eigenschaftenraster bereitgestellt, die von der `SettingsPage` Klasse kennt den meisten primitiven Datentypen und weiß, wie sie angezeigt.  Darüber hinaus die `SettingsPage` Klasse weiß, wie Eigenschaftswerte, zu der Projektdatei beibehalten werden.  
  
 Die Eigenschaftenseite, die Sie in diesem Abschnitt erstellen, können Sie die ändern und speichern diese Eigenschaften des Projekts:  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace.  
  
1. In der *SimpleProjectPackage.cs* hinzufügen. dies `ProvideObject` -Attribut auf die `SimpleProjectPackage` Klasse:  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    Auf diese Weise die Eigenschaftenseitenklasse registriert `GeneralPropertyPage` mit COM.  
  
2. In der *SimpleProjectNode.cs* hinzufügen. diese beiden überschriebenen Methoden, die `SimpleProjectNode` Klasse:  
  
   ```csharp  
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
  
    Beide Methoden geben ein Array von GUIDs (Eigenschaftenseite) zurück.  Die GeneralPropertyPage-GUID ist das einzige Element im Array, sodass die **Eigenschaftenseiten** Dialogfeld wird nur eine Seite angezeigt.  
  
3. Fügen Sie eine Klassendatei mit dem Namen *GeneralPropertyPage.cs* dem SimpleProject-Projekt.  
  
4. Ersetzen Sie den Inhalt dieser Datei, mit dem folgenden Code:  
  
   ```csharp  
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
  
    Die `GeneralPropertyPage` Klasse verfügbar macht, die drei öffentlichen Eigenschaften OutputType, AssemblyName und RootNamespace. Da der AssemblyName keine Set-Methode besitzt, wird er als nur-Lese Eigenschaft angezeigt. OutputType ist eine Enumerationskonstante, damit es als Dropdownliste angezeigt wird.  
  
    Die `SettingsPage` -Basisklasse stellt `ProjectMgr` Eigenschaften beibehalten werden. Die `BindProperties` -Methode verwendet `ProjectMgr` persistenten Werte abgerufen und die entsprechenden Eigenschaften festgelegt.  Die `ApplyChanges` -Methode verwendet `ProjectMgr` rufen Sie die Werte der Eigenschaften, und speichern sie an der Projektdatei. Die Methode wird der Eigenschaftensatz `IsDirty` auf true festlegen, um anzugeben, dass die Eigenschaften beibehalten werden müssen.  Dauerhaftigkeit tritt auf, wenn Sie das Projekt oder Projektmappe speichern.  
  
5. Erstellen Sie die Projektmappe SimpleProject neu, und mit dem Debuggen beginnen. Die experimentelle Instanz sollten angezeigt werden.  
  
6. Erstellen Sie eine neue SimpleProject-Anwendung, in der experimentellen Instanz.  
  
7. Visual Studio ruft die Projekt-Factory zum Erstellen eines Projekts mit Visual Studio-Vorlage. Die neue *"Program.cs"* Datei wird im Code-Editor geöffnet.  
  
8. Mit der rechten Maustaste des Projektknoten im **Projektmappen-Explorer**, und klicken Sie dann auf **Eigenschaften**. Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.  
  
   ![Einfaches Projekt-Eigenschaftenseite](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")  
  
## <a name="test-the-project-property-page"></a>Testen Sie die Eigenschaftenseite des Projekts
 Sie können nun testen, ob Sie ändern und Eigenschaftswerte ändern können.  
  
1. In der **MyConsoleApplication Eigenschaftenseiten** im Dialogfeld die **DefaultNamespace** zu **MyApplication**.  
  
2. Wählen Sie die **OutputType** -Eigenschaft, und wählen Sie dann **Klassenbibliothek**.  
  
3. Klicken Sie auf **übernehmen**, und klicken Sie dann auf **OK**.  
  
4. Öffnen Sie erneut die **Eigenschaftenseiten** Dialogfeld ein, und stellen Sie sicher, dass Ihre Änderungen erhalten geblieben sind.  
  
5. Schließen Sie die experimentelle Instanz von Visual Studio.  
  
6. Öffnen Sie die experimentelle Instanz erneut.  
  
7. Öffnen Sie erneut die **Eigenschaftenseiten** Dialogfeld ein, und stellen Sie sicher, dass Ihre Änderungen erhalten geblieben sind.  
  
8. Schließen Sie die experimentelle Instanz von Visual Studio.  
  
   ![Schließen Sie die experimentelle Instanz](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
