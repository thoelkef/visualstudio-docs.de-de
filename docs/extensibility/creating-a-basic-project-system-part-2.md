---
title: Erstellen eines basisgegrundlegenden Projektsystems, Teil 2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739710"
---
# <a name="create-a-basic-project-system-part-2"></a>Erstellen eines basisgegrundlegenden Projektsystems, Teil 2
Die erste exemplarische Vorgehensweise in dieser Reihe, [Erstellen eines grundlegenden Projektsystems, Teil 1 ,](../extensibility/creating-a-basic-project-system-part-1.md)zeigt, wie ein grundlegendes Projektsystem erstellt wird. Diese exemplarische Vorgehensweise basiert auf dem grundlegenden Projektsystem, indem eine Visual Studio-Vorlage, eine Eigenschaftenseite und andere Features hinzugefügt werden. Sie müssen die erste exemplarische Vorgehensweise abschließen, bevor Sie diese exemplarische Vorgehensweise starten.

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie einen Projekttyp mit der Projektdateinamenerweiterung *.myproj*erstellen. Um die exemplarische Vorgehensweise abzuschließen, müssen Sie keine eigene Sprache erstellen, da die exemplarische Vorgehensweise aus dem vorhandenen Visual C-Projektsystem entlehnt ist.

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie diese Aufgaben ausführen:

- Erstellen Sie eine Visual Studio-Vorlage.

- Stellen Sie eine Visual Studio-Vorlage bereit.

- Erstellen Sie einen untergeordneten Projekttypknoten im Dialogfeld **Neues Projekt.**

- Aktivieren Sie die Parameterersetzung in der Visual Studio-Vorlage.

- Erstellen Sie eine Projekteigenschaftsseite.

> [!NOTE]
> Die Schritte in dieser exemplarischen Vorgehensweise basieren auf einem C-Projekt. Mit Ausnahme von Details wie Dateinamenerweiterungen und Code können Sie jedoch dieselben Schritte für ein Visual Basic-Projekt verwenden.

## <a name="create-a-visual-studio-template"></a>Erstellen einer Visual Studio-Vorlage
- [Erstellen Sie ein grundlegendes Projektsystem, Teil 1 zeigt,](../extensibility/creating-a-basic-project-system-part-1.md) wie Sie eine grundlegende Projektvorlage erstellen und dem Projektsystem hinzufügen. Außerdem wird gezeigt, wie diese Vorlage mithilfe <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> des Attributs bei Visual Studio registriert wird, das den vollständigen Pfad des * \\Ordners "Vorlagen- und Projekte- SimpleProject"\\ * in der Systemregistrierung schreibt.

Mithilfe einer Visual Studio-Vorlage *(.vstemplate-Datei)* anstelle einer grundlegenden Projektvorlage können Sie steuern, wie die Vorlage im Dialogfeld **Neues Projekt** angezeigt und Vorlagenparameter ersetzt werden. Eine *.vstemplate-Datei* ist eine XML-Datei, die beschreibt, wie Quelldateien eingeschlossen werden sollen, wenn ein Projekt mithilfe der Projektsystemvorlage erstellt wird. Das Projektsystem selbst wird durch Das Sammeln der *.vstemplate-Datei* und der Quelldateien in einer *ZIP-Datei* erstellt und durch Kopieren der *ZIP-Datei* an einen Speicherort bereitgestellt, der Visual Studio bekannt ist. Dieser Prozess wird später in dieser exemplarischen Vorgehensweise ausführlicher erläutert.

1. Öffnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Sie in die SimpleProject-Projektmappe, die Sie erstellt haben, indem Sie einem [grundlegenden Projektsystem, Teil 1,](../extensibility/creating-a-basic-project-system-part-1.md)folgen.

2. Suchen Sie in der *Datei SimpleProjectPackage.cs* das ProvideProjectFactory-Attribut. Ersetzen Sie den zweiten Parameter (den Projektnamen) durch null und den vierten Parameter (den Pfad zum Projektvorlagenordner) durch ". \\"NullPath", wie folgt.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Fügen Sie eine XML-Datei mit dem Namen *SimpleProject.vstemplate* zum Ordner * \\"Vorlagen- und Projekt-SimpleProject"\\ * hinzu.

4. Ersetzen Sie den Inhalt von *SimpleProject.vstemplate* durch den folgenden Code.

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

5. Wählen Sie im **Fenster Eigenschaften** alle fünf Dateien im Ordner * \\"Vorlagen- und Projekte" aus,\\ * und legen Sie die **Buildaktion** auf **ZipProject**fest.

    ![Einfacher Projektordner](../extensibility/media/simpproj2.png "SimpProj2")

    Der \<Abschnitt TemplateData> bestimmt den Speicherort und die Darstellung des SimpleProject-Projekttyps im Dialogfeld **Neues Projekt** wie folgt:

- Der \<Name>-Element benennt die Projektvorlage als SimpleProject-Anwendung.

- Das \<Element Beschreibung> enthält die Beschreibung, die im Dialogfeld **Neues Projekt** angezeigt wird, wenn die Projektvorlage ausgewählt ist.

- Das \<Element Icon> gibt das Symbol an, das zusammen mit dem SimpleProject-Projekttyp angezeigt wird.

- Das \<ProjectType->-Element benennt den Projekttyp im Dialogfeld **Neues Projekt.** Dieser Name ersetzt den Projektnamenparameter des ProvideProjectFactory-Attributs.

  > [!NOTE]
  > Das \<ProjectType>-Element `LanguageVsTemplate` muss `ProvideProjectFactory` mit dem Argument des Attributs in der SimpleProjectPackage.cs-Datei übereinstimmen.

  Im \<Abschnitt TemplateContent> werden die folgenden Dateien beschrieben, die beim Erstellen eines neuen Projekts generiert werden:

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Alle drei `ReplaceParameters` Dateien haben auf true gesetzt, was die Parameterersetzung ermöglicht. Die *Program.cs* `OpenInEditor` Datei auf true festgelegt hat, wodurch die Datei beim Erstellen eines Projekts im Code-Editor geöffnet wird.

  Weitere Informationen zu den Elementen im Visual Studio-Vorlagenschema finden Sie im [Visual Studio-Vorlagenschemaverweis](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Wenn ein Projekt über mehr als eine Visual Studio-Vorlage verfügt, befindet sich jede Vorlage in einem separaten Ordner. Für jede Datei in diesem Ordner muss die **Buildaktion** auf **ZipProject**festgelegt sein.

## <a name="adding-a-minimal-vsct-file"></a>Hinzufügen einer minimalen .vsct-Datei
 Visual Studio muss im Setupmodus ausgeführt werden, um eine neue oder geänderte Visual Studio-Vorlage zu erkennen. Im Setup-Modus muss eine *.vsct-Datei* vorhanden sein. Daher müssen Sie dem Projekt eine minimale *.vsct-Datei* hinzufügen.

1. Fügen Sie dem SimpleProject-Projekt eine XML-Datei mit dem Namen *SimpleProject.vsct* hinzu.

2. Ersetzen Sie den Inhalt der *Datei SimpleProject.vsct* durch den folgenden Code.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Legen Sie die **Buildaktion** dieser Datei auf **VSCTCompile**fest. Sie können dies nur in der *.csproj-Datei* tun, nicht im **Eigenschaftenfenster.** Stellen Sie sicher, dass die **Buildaktion** dieser Datei zu diesem Zeitpunkt auf **Keine** festgelegt ist.

    1. Klicken Sie mit der rechten Maustaste auf den SimpleProject-Knoten, und klicken Sie dann auf **SimpleProject.csproj bearbeiten**.

    2. Suchen Sie in der *.csproj-Datei* das *Element SimpleProject.vsct.*

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Ändern Sie die Buildaktion in **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. Projektdatei und schließen Sie den Editor.

    5. Speichern Sie den SimpleProject-Knoten, und klicken Sie dann im **Projektmappen-Explorer** auf **Projekt neu laden**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Untersuchen der Erstellungsschritte der Visual Studio-Vorlage
 Das VSPackage-Projektbuildsystem führt Visual Studio in der Regel im Setupmodus aus, wenn die *.vstemplate-Datei* geändert oder das Projekt, das die *.vstemplate-Datei* enthält, neu erstellt wird. Sie können die ausführlichen Ebenen von MSBuild auf Normal oder höher festlegen.

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Erweitern Sie den Knoten **Projekte und Lösungen,** und wählen Sie dann **Build and Run**aus.

3. Legen Sie **MSBuild-Projektbuildausgabeausführlichität** auf **Normal**fest. Klicken Sie auf **OK**.

4. Erstellen Sie das SimpleProject-Projekt neu.

    Der Buildschritt zum *.zip* Erstellen der ZIP-Projektdatei sollte dem folgenden Beispiel ähneln.

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
Visual Studio-Vorlagen enthalten keine Pfadinformationen. Daher muss *.zip* die ZIP-Vorlagedatei an einem Speicherort bereitgestellt werden, der Visual Studio bekannt ist. Der Speicherort des ProjectTemplates-Ordners ist in der Regel *<%LOCALAPPDATA%>.*

Um Ihre Projektfactory bereitzustellen, muss das Installationsprogramm über Administratorrechte verfügen. Es stellt Vorlagen unter dem Visual Studio-Installationsknoten bereit: ... . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . *. . . . . . . . . . . . . . . . . . . .*. . . . . . . .

## <a name="test-a-visual-studio-template"></a>Testen einer Visual Studio-Vorlage
Testen Sie die Projektfactory, um mithilfe der Visual Studio-Vorlage festzustellen, ob eine Projekthierarchie erstellt wird.

1. Setzen Sie die experimentelle Instanz des Visual Studio SDK zurück.

    Unter [!INCLUDE[win7](../debugger/includes/win7_md.md)]: Suchen Sie im **Startmenü** den Ordner **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools,** und wählen Sie dann **Microsoft Visual Studio Experimental-Instanz zurücksetzen**aus.

    Bei späteren Versionen von Windows: Geben Sie auf dem **Startbildschirm** **die Microsoft Visual Studio-Version \<> Experimental Instance**zurück.

2. Ein Eingabeaufforderungsfenster wird angezeigt. Wenn die Wörter **Drücken Sie eine beliebige Taste drücken, um fortzufahren,** klicken Sie auf **ENTER**. Öffnen Sie Visual Studio, nachdem das Fenster geschlossen wurde.

3. Erstellen Sie das SimpleProject-Projekt neu, und starten Sie das Debuggen. Die experimentelle Instanz wird angezeigt.

4. Erstellen Sie in der experimentellen Instanz ein SimpleProject-Projekt. Wählen Sie im Dialogfeld **Neues Projekt** **SimpleProject**aus.

5. Es sollte eine neue Instanz von SimpleProject angezeigt werden.

    ![Einfache projektneue Instanz](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Meine neue Projektinstanz](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Erstellen eines untergeordneten Projekttypknotens
Sie können einem Projekttypknoten im Dialogfeld **Neues Projekt** einen untergeordneten Knoten hinzufügen. Für den SimpleProject-Projekttyp können Sie beispielsweise untergeordnete Knoten für Konsolenanwendungen, Fensteranwendungen, Webanwendungen usw. verwenden.

Untergeordnete Knoten werden erstellt, indem die \<Projektdatei geändert und \<der ZipProject> Elementen von OutputSubPath> untergeordneteElemente hinzugefügt werden. Wenn eine Vorlage während des Builds oder der Bereitstellung kopiert wird, wird jeder untergeordnete Knoten zu einem Unterordner des Projektvorlagenordners.

In diesem Abschnitt wird gezeigt, wie Sie einen untergeordneten Konsolenknoten für den SimpleProject-Projekttyp erstellen.

1. Benennen Sie den * \\Ordner "Vorlagen" ,,Projekte" und "SimpleProject"\\ * in * \\"Vorlagen" und "Projekte" um.\\*

2. Wählen Sie im **Eigenschaftenfenster** alle fünf Dateien im Ordner * \\Vorlagen-Projekte-KonsoleApp\\ * aus, und stellen Sie sicher, dass die **Buildaktion** auf **ZipProject**festgelegt ist.

3. Fügen Sie in der Datei SimpleProject.vstemplate die \<folgende Zeile am Ende des Abschnitts TemplateData> kurz vor dem schließenden Tag hinzu.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Dadurch wird die Konsolenanwendungsvorlage sowohl im untergeordneten Knoten Konsole als auch im übergeordneten Knoten SimpleProject angezeigt, der eine Ebene über dem untergeordneten Knoten liegt.

4. Speichern Sie die Datei *SimpleProject.vstemplate.*

5. Fügen Sie \<in der *.csproj-Datei* OutputSubPath-> zu jedem ZipProject-Element hinzu. Entladen Sie das Projekt wie zuvor, und bearbeiten Sie die Projektdatei.

6. Suchen \<Sie die ZipProject-> Elemente. Fügen \<Sie jedem ZipProject->-Element ein \<OutputSubPath->-Element hinzu, und geben Sie ihm den Wert Console. Das ZipProject

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

7. Fügen \<Sie der Projektdatei diese PropertyGroup-> hinzu:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Speichern Sie die Projektdatei, und laden Sie das Projekt neu.

## <a name="test-the-project-type-child-node"></a>Testen des untergeordneten Projekttypknotens
Testen Sie die geänderte Projektdatei, um festzustellen, ob der untergeordnete **Knoten Konsole** im Dialogfeld **Neues Projekt** angezeigt wird.

1. Führen Sie das Tool **"Zurücksetzen" des Microsoft Visual Studio Experimental Instance-Tools** aus.

2. Erstellen Sie das SimpleProject-Projekt neu, und starten Sie das Debuggen. Die experimentelle Instanz sollte angezeigt werden

3. Klicken Sie im Dialogfeld **Neues Projekt** auf den **SimpleProject-Knoten.** Die **Vorlage für Konsolenanwendungen** sollte im Bereich **Vorlagen** angezeigt werden.

4. Erweitern Sie den **SimpleProject-Knoten.** Der untergeordnete **Konsolenknoten** sollte angezeigt werden. Die **SimpleProject-Anwendungsvorlage** wird weiterhin im Bereich **Vorlagen** angezeigt.

5. Klicken Sie auf **Abbrechen** und beenden Sie das Debuggen.

    ![Einfaches ProjektRollup](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Einfacher Projektkonsolenknoten](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Ersetzen von Projektvorlagenparametern
- [Bei der Erstellung eines grundlegenden Projektsystems](../extensibility/creating-a-basic-project-system-part-1.md) wurde `ProjectNode.AddFileFromTemplate` in Teil 1 gezeigt, wie die Methode überschrieben wird, um eine grundlegende Art der Vorlagenparameterersetzung zu erstellen. In diesem Abschnitt wird erläutert, wie Sie die anspruchsvolleren Visual Studio-Vorlagenparameter verwenden.

Wenn Sie ein Projekt mithilfe einer Visual Studio-Vorlage im Dialogfeld **Neues Projekt** erstellen, werden Vorlagenparameter durch Zeichenfolgen ersetzt, um das Projekt anzupassen. Ein Vorlagenparameter ist ein spezielles Token, das mit einem Dollarzeichen beginnt und endet, z. B. $time. Die folgenden beiden Parameter sind besonders nützlich, um die Anpassung in Projekten zu aktivieren, die auf der Vorlage basieren:

- $GUID[1-10]" wird durch eine neue Guid ersetzt. Sie können bis zu 10 eindeutige GUIDs angeben, z. B. $guid1.

- $safeprojectname b ist der Name, der von einem Benutzer im Dialogfeld **Neues Projekt** angegeben wird, der so geändert wird, dass alle unsicheren Zeichen und Leerzeichen entfernt werden.

  Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>So ersetzen Sie Projektvorlagenparameter

1. Entfernen *Sie* die `AddFileFromTemplate` Methode in der Datei SimpleProjectNode.cs.

2. Suchen Sie in der \< * \\Datei Templates-Projects-ConsoleApp-SimpleProject.myproj* die RootNamespace-Eigenschaft> und ändern Sie ihren Wert in $safeprojectname.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. Ersetzen Sie in der * \\Datei Templates-Projects-SimpleProject-Program.cs* den Inhalt der Datei durch den folgenden Code:

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

4. Erstellen Sie das SimpleProject-Projekt neu, und starten Sie das Debuggen. Die experimentelle Instanz sollte angezeigt werden.

5. Erstellen Sie eine neue SimpleProject Console-Anwendung. (Wählen Sie im Bereich **Projekttypen** **SimpleProject**aus. Wählen Sie unter **Visual Studio installierte Vorlagen** **Konsolenanwendung**aus.)

6. Öffnen Sie im neu erstellten Projekt *Program.cs*. Es sollte etwa wie folgt aussehen (GUID-Werte in Ihrer Datei unterscheiden sich.):

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

## <a name="create-a-project-property-page"></a>Erstellen einer Projekteigenschaftsseite
Sie können eine Eigenschaftenseite für Ihren Projekttyp erstellen, damit Benutzer Eigenschaften in Projekten anzeigen und ändern können, die auf Ihrer Vorlage basieren. In diesem Abschnitt erfahren Sie, wie Sie eine konfigurationsunabhängige Eigenschaftenseite erstellen. Diese grundlegende Eigenschaftenseite verwendet ein Eigenschaftenraster, um die öffentlichen Eigenschaften anzuzeigen, die Sie in Ihrer Eigenschaftenseitenklasse verfügbar machen.

Leiten Sie ihre Eigenschaftenseitenklasse von der `SettingsPage` Basisklasse ab. Das von der `SettingsPage` Klasse bereitgestellte Eigenschaftenraster kennt die meisten primitiven Datentypen und weiß, wie sie angezeigt werden. Darüber hinaus `SettingsPage` weiß die Klasse, wie Eigenschaftswerte in der Projektdatei beibehalten werden.

Auf der Eigenschaftenseite, die Sie in diesem Abschnitt erstellen, können Sie die folgenden Projekteigenschaften ändern und speichern:

- AssemblyName

- OutputType

- Rootnamespace.

1. Fügen Sie in der `ProvideObject` datei `SimpleProjectPackage` *SimpleProjectPackage.cs* dieses Attribut der Klasse hinzu:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Dadurch wird die Eigenschaftenseitenklasse `GeneralPropertyPage` bei COM registriert.

2. Fügen *SimpleProjectNode.cs* Sie in `SimpleProjectNode` der datei SimpleProjectNode.cs der Klasse die beiden überschriebenen Methoden hinzu:

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

    Beide Methoden geben ein Array von Eigenschaftenseiten-GUIDs zurück. Die GeneralPropertyPage-GUID ist das einzige Element im Array, sodass im Dialogfeld **Eigenschaftenseiten** nur eine Seite angezeigt wird.

3. Fügen Sie dem SimpleProject-Projekt eine Klassendatei mit dem Namen *GeneralPropertyPage.cs* hinzu.

4. Ersetzen Sie den Inhalt dieser Datei durch den folgenden Code:

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
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    Die `GeneralPropertyPage` Klasse macht die drei öffentlichen Eigenschaften AssemblyName, OutputType und RootNamespace verfügbar. Da AssemblyName über keine set-Methode verfügt, wird sie als schreibgeschützte Eigenschaft angezeigt. OutputType ist eine aufgezählte Konstante, daher wird sie als Dropdownliste angezeigt.

    Die `SettingsPage` Basisklasse `ProjectMgr` bietet, dass die Eigenschaften beibehalten werden. Die `BindProperties` Methode `ProjectMgr` verwendet, um die persistenten Eigenschaftswerte abzurufen und die entsprechenden Eigenschaften festzulegen. Die `ApplyChanges` Methode `ProjectMgr` verwendet, um die Werte der Eigenschaften abzuspeichern und sie in der Projektdatei beizubehalten. Die Eigenschaftssatzmethode legt `IsDirty` auf true fest, um anzugeben, dass die Eigenschaften beibehalten werden müssen. Persistenz tritt auf, wenn Sie das Projekt oder die Projektmappe speichern.

5. Erstellen Sie die SimpleProject-Lösung neu, und beginnen Sie mit dem Debuggen. Die experimentelle Instanz sollte angezeigt werden.

6. Erstellen Sie in der experimentellen Instanz eine neue SimpleProject-Anwendung.

7. Visual Studio ruft Ihre Projektfactory auf, um ein Projekt mithilfe der Visual Studio-Vorlage zu erstellen. Die neue *Program.cs* Datei wird im Code-Editor geöffnet.

8. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten , und klicken Sie dann auf **Eigenschaften**. Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.

    ![Einfache Projekteigenschaftsseite](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Testen der Projekteigenschaftsseite
Jetzt können Sie testen, ob Sie Eigenschaftswerte ändern und ändern können.

1. Ändern Sie im Dialogfeld **MyConsoleApplication-Eigenschaftenseiten** den **DefaultNamespace** in **MyApplication**.

2. Wählen Sie die **OutputType-Eigenschaft** aus, und wählen Sie dann **Klassenbibliothek**aus.

3. Klicken Sie auf **Übernehmen**, und klicken Sie anschließend auf **OK**.

4. Öffnen Sie das Dialogfeld **Eigenschaftenseiten erneut,** und stellen Sie sicher, dass Ihre Änderungen beibehalten wurden.

5. Schließen Sie die experimentelle Instanz von Visual Studio.

6. Öffnen Sie die experimentelle Instanz erneut.

7. Öffnen Sie das Dialogfeld **Eigenschaftenseiten erneut,** und stellen Sie sicher, dass Ihre Änderungen beibehalten wurden.

8. Schließen Sie die experimentelle Instanz von Visual Studio.
    ![Schließen der experimentellen Instanz](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
