---
title: Erstellen eine grundlegende Projektsystem, Teil 1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ceb7bb63caf3677c3758d88713308daa0c34fb4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108335"
---
# <a name="creating-a-basic-project-system-part-1"></a>Erstellen eine grundlegende Projektsystem, Teil 1
In Visual Studio sind Projekte die Container, mit denen Entwickler Quellcodedateien und anderen Ressourcen zu organisieren. Projekte angezeigt werden als untergeordnete Elemente von Lösungen in der **Projektmappen-Explorer**. Projekte können Sie die zu organisieren, erstellen, Debuggen, und Bereitstellen von Quellcode und Erstellen von Verweisen auf Web-Services, Datenbanken und andere Ressourcen.  
  
 Projekte werden in Projektdateien, z. B. eine CSPROJ-Datei für ein Visual C#-Projekt definiert. Sie können Ihren eigenen Projekttyp erstellen, der Ihre eigenen Projekt-Dateierweiterung aufweist. Weitere Informationen zu Projekttypen finden Sie unter [Projekttypen](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Wenn Sie Visual Studio mit einem benutzerdefinierten Projekttyps erweitern müssen, es wird dringend empfohlen Nutzung der [Visual Studio-Projektsystem](https://github.com/Microsoft/VSProjectSystem) (VSPS) die verfügt über eine Reihe von Vorteilen, die über ein Projektsystem von Grund auf neu erstellen:  
>   
>  -  Einfacher Onboarding.  Auch eine grundlegende Projektsystem erfordert Zehntausenden von Codezeilen.  Die Kosten für das Onboarding auf ein paar Mausklicks VSPS Nutzung reduziert werden, bevor Sie ihn an Ihre Bedürfnisse anpassen möchten.  
>  -  Einfachere Wartung.  Mittels VSPS müssen Sie nur Ihre eigenen Szenarien zu verwalten.  Wir behandeln die Wartung der aller dem Projekt Systeminfrastruktur.  
>   
>  Wenn Sie verschiedene Versionen von Visual Studio, die älter sind als Visual Studio 2013 müssen, werden Sie nicht VSPS in einer Visual Studio-Erweiterung nutzen sein.  Wenn dies der Fall ist, wird in dieser exemplarischen Vorgehensweise einen guten Ausgangspunkt für die ersten Schritte.  
  
 Diese exemplarische Vorgehensweise veranschaulicht die einen Projekttyp zu erstellen, der die Project-Datei Name Erweiterung .myproj verfügt. In dieser exemplarischen Vorgehensweise ist aus dem vorhandenen Visual C#-Projektsystem.  
  
> [!NOTE]
>  Weitere Beispiele für Erweiterungsprojekten, finden Sie unter [VSSDK-Beispiele](http://aka.ms/vs2015sdksamples).  
  
 In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie diese Aufgaben ausführen:  
  
-   Erstellen Sie einen grundlegenden Projekttyp.  
  
-   Erstellen einer basic-Projektvorlage.  
  
-   Registrieren Sie die Projektvorlage in Visual Studio.  
  
-   Erstellen Sie eine Projektinstanz durch Öffnen der **neues Projekt** (Dialogfeld), und klicken Sie dann mit der Vorlage.  
  
-   Erstellen Sie eine Projekt Factory für Ihr Projektsystem.  
  
-   Erstellen Sie einen Projektknoten für Ihr Projektsystem.  
  
-   Fügen Sie benutzerdefinierte Symbole für das Projektsystem.  
  
-   Ersetzung von Typparametern Basisvorlage zu implementieren.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Sie müssen auch den Quellcode für Herunterladen der [Managed Package Framework for Projects](http://mpfproj12.codeplex.com/). Extrahieren Sie die Datei an einem Speicherort, der für die Lösung zugänglich ist, die Sie erstellen möchten.  
  
## <a name="creating-a-basic-project-type"></a>Erstellen einen grundlegenden Projekttyp  
 Erstellen Sie ein C#-VSIX-Projekt namens **SimpleProject**. (**Datei "," Neu "," Projekt** und dann **VSIX-Projekt in Visual C#-, Erweiterbarkeit,**). Fügen Sie eine Visual Studio-Paket Projektelementvorlage hinzu (klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des Projektknotens, und wählen **hinzufügen / neues Element**, dann wechseln Sie zu **Erweiterbarkeit / Visual Studio-Paket**). Nennen Sie die Datei **SimpleProjectPackage**.  
  
## <a name="creating-a-basic-project-template"></a>Erstellen einer Basic-Projektvorlage  
 Jetzt können Sie diese grundlegende VSPackage zur Implementierung der neuen .myproj Projekttyp ändern. Um ein Projekt erstellen, die auf den Projekttyp .myproj basiert, muss Visual Studio wissen, welche Dateien, Ressourcen und Verweise auf dem neuen Projekt hinzugefügt. Um diese Informationen bereitzustellen, fügen Sie Projektdateien in einem Projektordner für die Vorlage aus. Wenn ein Benutzer das .myproj-Projekt zum Erstellen eines Projekts verwendet wird, werden die Dateien in das neue Projekt kopiert.  
  
#### <a name="to-create-a-basic-project-template"></a>Zum Erstellen einer basic-Projektvorlage  
  
1.  Das Projekt ein, unter der anderen drei Ordner hinzugefügt: **Templates\Projects\SimpleProject**. (In **Projektmappen-Explorer**, mit der rechten Maustaste die **SimpleProject** Projektknoten, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neuer Ordner**. Geben Sie dem Ordner den Namen `Templates`anmelden. In der **Vorlagen** Ordner, fügen Sie einen Ordner mit dem Namen `Projects`. In der **Projekte** Ordner, fügen Sie einen Ordner mit dem Namen `SimpleProject`.)  
  
2.  In der **Templates\Projects\SimpleProject** Ordner, fügen Sie eine Bitmap-Bild-Datei für die Verwendung als Symbol mit dem Namen `SimpleProject.ico`. Beim Klicken auf **hinzufügen**, Symbol-Editor wird geöffnet.  
  
3.  Stellen Sie das Symbol unterschiedliche. Dieses Symbol wird angezeigt, der **neues Projekt** Dialogfeld weiter unten in dieser exemplarischen Vorgehensweise.  
  
     ![Symbol Einfaches Projekt](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  Speichern Sie das Symbol "", und schließen Sie den Symbol-Editor.  
  
5.  In der **Templates\Projects\SimpleProject** Ordner Hinzufügen einer **Klasse** Bezeichnung "Item" `Program.cs`.  
  
6.  Ersetzen Sie den vorhandenen Code mit den folgenden Zeilen ein.  
  
    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
  
    namespace $nameSpace$
    {  
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```
  
    > [!IMPORTANT]
    >  Dies ist nicht die endgültige Form des Codes "Program.cs". die Austausch-Parameter werden in einem späteren Schritt behandelt werden. Möglicherweise Kompilierungsfehler, jedoch so lange, wie der Datei **BuildAction** ist **Content**, Sie sollten Lage zu erstellen und führen Sie das Projekt wie gewohnt.  
  
1.  Speichern Sie die Datei.  
  
2.  Kopieren Sie die Datei "AssemblyInfo.cs" aus der **Eigenschaften** Ordner, um die **Projects\SimpleProject** Ordner.  
  
3.  In der **Projects\SimpleProject** Ordner hinzuzufügen, eine XML-Datei mit dem Namen `SimpleProject.myproj`.  
  
    > [!NOTE]
    >  Die Dateinamenerweiterung für alle Projekte dieses Typs ist .myproj. Wenn Sie sie ändern möchten, müssen Sie es überall ändern, die sie in der exemplarischen Vorgehensweise genannt wird.  
  
4.  Ersetzen Sie den vorhandenen Inhalt mit den folgenden Zeilen ein.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid></ProjectGuid>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>MyRootNamespace</RootNamespace>  
        <AssemblyName>MyAssemblyName</AssemblyName>  
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        <DebugSymbols>true</DebugSymbols>  
        <OutputPath>bin\Debug\</OutputPath>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
        <DebugSymbols>false</DebugSymbols>  
        <OutputPath>bin\Release\</OutputPath>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="mscorlib" />  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="AssemblyInfo.cs">  
          <SubType>Code</SubType>  
        </Compile>  
        <Compile Include="Program.cs">  
          <SubType>Code</SubType>  
        </Compile>  
      </ItemGroup>  
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
    </Project>  
    ```  
  
5.  Speichern Sie die Datei.  
  
6.  In der **Eigenschaften** fest der **Buildvorgang** AssemblyInfo.cs, Datei "Program.cs", SimpleProject.ico und SimpleProject.myproj auf **Content**, und legen Sie deren  **In VSIX einbeziehen** Eigenschaften **"true"**.  
  
 Diese Projektvorlage beschreibt eine grundlegende Visual C#-Projekt, die eine Debug-Konfiguration und einer Releasekonfiguration aufweist. Das Projekt enthält zwei Quelldateien, Datei "AssemblyInfo.cs" und "Program.cs" und mehrere Assembly verweisen. Wenn ein Projekt aus der Vorlage erstellt wird, wird der ProjectGuid Wert automatisch durch eine neue GUID ersetzt.  
  
 In **Projektmappen-Explorer**, dem erweiterten **Vorlagen** Ordner sollte wie folgt aussehen:

```
Templates  
   Projects  
      SimpleProject  
         AssemblyInfo.cs  
         Program.cs  
         SimpleProject.ico  
         SimpleProject.myproj  
```

## <a name="creating-a-basic-project-factory"></a>Erstellen eine Factory für Basic-Projekts  
 Sie müssen Visual Studio den Speicherort des Projektordners Vorlage mitteilen. Fügen Sie ein Attribut zu diesem Zweck die VSPackage-Klasse hinzu, die die Projekt-Factory implementiert, sodass der Speicherort für die Vorlage in der systemregistrierung geschrieben wird, wenn das VSPackage erstellt wird. Zunächst erstellen eine einfaches Projekt-Factory, die von einem Projekt Factory GUID identifiziert wird. Verwenden der <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> Attribut zur Verbindung mit der Klasse SimpleProjectPackage der Projekt-Factory.  
  
#### <a name="to-create-a-basic-project-factory"></a>Zum Erstellen einer Factory basic-Projekts  
  
1.  Erstellen von GUIDs für Ihr Projekt Factory (auf der **Tools** Menü klicken Sie auf **GUID erstellen**), oder verwenden Sie das Schema im folgenden Beispiel. Fügen Sie die GUIDs der SimpleProjectPackage-Klasse in der Nähe der Abschnitt mit den bereits definierten `PackageGuidString`. Die GUIDs müssen im GUID-Format und in Form einer Zeichenfolge sein. Der resultierende Code sollte im folgende Beispiel ähneln.  
  
    ```csharp  
        public sealed class SimpleProjectPackage : Package
        {  
            ...
            public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
            public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
    
            public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);  
        }  
    ```  
  
3.  Fügen Sie eine Klasse, die oben **SimpleProject** Ordner mit dem Namen `SimpleProjectFactory.cs`.  
  
4.  Fügen Sie die folgenden using-Anweisungen:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Ein Guid-Attribut der SimpleProjectFactory-Klasse hinzufügen. Der Wert des Attributs ist der GUID der neuen Projekt Factory.  
  
    ```csharp  
    [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 Jetzt können Sie die Projektvorlage registrieren.  
  
#### <a name="to-register-the-project-template"></a>So registrieren die Projektvorlage  
  
1.  Fügen Sie in SimpleProjectPackage.cs, eine <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> -Attribut der Klasse SimpleProjectPackage wie folgt.  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectPackage.PackageGuidString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass es ohne Fehler erstellt.  
  
     Erneutes Erstellen, wird die Projektvorlage registriert.  
  
 Die Parameter `defaultProjectExtension` und `possibleProjectExtensions` auf die Dateierweiterung des Projekts (.myproj) festgelegt sind. Die `projectTemplatesDirectory` Parameter auf den relativen Pfad des Ordners Vorlagen festgelegt ist. Während des Builds wird dieser Pfad auf einen vollständigen Build konvertiert und an der Registrierung, registrieren Sie das Projektsystem hinzugefügt werden.  
  
## <a name="testing-the-template-registration"></a>Testen die Vorlagenregistrierung  
 Vorlagenregistrierung weist Visual Studio den Speicherort des Projektordners Vorlage, damit Visual Studio anzeigen können, der Vorlagenname und ein Symbol in der **neues Projekt** (Dialogfeld).  
  
#### <a name="to-test-the-template-registration"></a>So testen Sie die vorlagenregistrierung  
  
1.  Drücken Sie F5 zum Starten des Debuggings einer experimentellen Instanz von Visual Studio.  
  
2.  Erstellen Sie ein neues Projekt des Projekttyps neu erstellte, in der experimentellen Instanz. In der **neues Projekt** (Dialogfeld), sollten Sie sehen **SimpleProject** unter **installierte Vorlagen**.  
  
 Sie haben jetzt eine Projekt-Factory, die registriert wird. Es kann keine jedoch noch ein Projekt erstellen. Das Projektpaket und das Projekt Factory zusammenarbeiten, um das Erstellen und initialisieren Sie ein Projekt.  
  
## <a name="add-the-managed-package-framework-code"></a>Fügen Sie den Code des Managed Package Framework  
 Implementieren Sie die Verbindung zwischen der Projektpaket und die Projekt-Factory.  
  
-   Importieren Sie die Quellcodedateien für die Managed Package Framework.  
  
    1.  Entladen Sie das Projekt SimpleProject (in **Projektmappen-Explorer**, wählen Sie den Projektknoten, und klicken Sie im Kontextmenü auf **Projekt entladen**.), und öffnen Sie die Projektdatei im XML-Editor.  
  
    2.  Fügen Sie die folgenden Blöcken an der Projektdatei (direkt über die \<Import > Blöcke). Legen Sie ProjectBasePath auf den Speicherort der Datei ProjectBase.files in der Managed Package Framework-Code, den Sie soeben heruntergeladen haben. Möglicherweise müssen Sie den Pfadnamen einen umgekehrter Schrägstrich hinzufügt. Wenn nicht der Fall, kann das Projekt nicht das Managed Package Framework-Code zu suchen.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  Vergessen Sie nicht den umgekehrten Schrägstrich am Ende des Pfads.  
  
    3.  Laden Sie das Projekt erneut.  
  
    4.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
        -   Microsoft.VisualStudio.Designer.Interfaces (in \<VSSDK Install > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Die Projekt-Factory initialisiert werden.  
  
1.  Fügen Sie die folgenden, in der Datei SimpleProjectPackage.cs `using` Anweisung.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Leiten Sie die `SimpleProjectPackage` -Klasse aus `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Registrieren Sie den Projekt-Factory. Die folgende Zeile zum Hinzufügen der `SimpleProjectPackage.Initialize` -Methode, direkt nach `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Implementiert die abstrakte Eigenschaft `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  In SimpleProjectFactory.cs, fügen Sie die folgenden `using` Anweisung nach den vorhandenen `using` Anweisungen.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Leiten Sie die `SimpleProjectFactory` -Klasse aus `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Fügen Sie die folgenden dummy-Methode, die `SimpleProjectFactory` Klasse. Implementieren Sie diese Methode in einem späteren Abschnitt.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Fügen Sie die folgenden Feld und Konstruktor, um die `SimpleProjectFactory` Klasse. Dies `SimpleProjectPackage` Verweis wird in einem privaten Feld zwischengespeichert, sodass sie bei der Festlegung einer dienstanbieterstandort verwendet werden kann.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass es ohne Fehler erstellt.  
  
## <a name="testing-the-project-factory-implementation"></a>Testen der Projektfactoryimplementierung  
 Überprüfen Sie, ob der Konstruktor für Ihrer projektfactoryimplementierung aufgerufen wird.  
  
#### <a name="to-test-the-project-factory-implementation"></a>So testen Sie die projektfactoryimplementierung  
  
1.  In der Datei SimpleProjectFactory.cs legen Sie einen Haltepunkt in der folgenden Zeile in der `SimpleProjectFactory` Konstruktor.  
  
    ```  
    this.package = package;  
    ```  
  
2.  Drücken Sie F5, um eine experimentelle Instanz von Visual Studio starten.  
  
3.  Starten Sie zum Erstellen eines neuen Projekts in der experimentellen Instanz. In der **neues Projekt** wählen Sie im Dialogfeld die SimpleProject Projekttyp, und klicken Sie dann auf **OK**. Die Ausführung hält am Haltepunkt an.  
  
4.  Löschen Sie den Haltepunkt, und beenden Sie des Debuggens. Da wir einen Projektknoten noch nicht erstellt haben, löst die Erstellung Projektcode weiterhin Ausnahmen aus.  
  
## <a name="extending-the-project-node-class"></a>Erweitern Sie die Klasse des Knotens  
 Nächstes, Sie implementieren können die `SimpleProjectNode` -Klasse, abgeleitet von der `ProjectNode` Klasse. Die `ProjectNode` Basisklasse behandelt der projekterstellung die folgenden Aufgaben:  
  
-   Kopiert die Datei zum Projekt der Vorlage SimpleProject.myproj, auf dem neuen Projektordner. Die Kopie wird umbenannt, entsprechend den Namen, die in eingegeben haben, ist die **neues Projekt** (Dialogfeld). Die `ProjectGuid` Eigenschaftswert wird durch eine neue GUID ersetzt.  
  
-   Durchläuft die MSBuild-Elemente der Projekt-Vorlagendatei SimpleProject.myproj, und sucht nach `Compile` Elemente. Für jede `Compile` Zieldatei, die Datei auf dem neuen Projektordner kopiert.  
  
 Die abgeleitete `SimpleProjectNode` Klasse behandelt diese Aufgaben:  
  
-   Ermöglicht die Symbole für Projekt- und Knoten in **Projektmappen-Explorer** erstellt oder ausgewählt werden.  
  
-   Können zusätzliche Project Vorlage parameterersetzungen angegeben werden.  
  
#### <a name="to-extend-the-project-node-class"></a>So erweitern Sie den Projekt-Knoten-Klasse  
  
1.  
  
2.  Fügen Sie eine Klasse mit dem Namen `SimpleProjectNode.cs`.  
  
3.  Ersetzen Sie den vorhandenen Code durch folgenden Code:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Project;  
  
    namespace SimpleProject  
    {  
        public class SimpleProjectNode : ProjectNode  
        {  
            private SimpleProjectPackage package;  
  
            public SimpleProjectNode(SimpleProjectPackage package)  
            {  
                this.package = package;  
            }  
            public override Guid ProjectGuid  
            {  
                get { return SimpleProjectPackage.guidSimpleProjectFactory; }  
            }  
            public override string ProjectType  
            {  
                get { return "SimpleProjectType"; }  
            }  
  
            public override void AddFileFromTemplate(  
                string source, string target)  
            {  
                this.FileTemplateProcessor.UntokenFile(source, target);  
                this.FileTemplateProcessor.Reset();  
            }  
        }  
    }  
    ```  
  
 Dies `SimpleProjectNode` klassenimplementierung enthält diese überschriebenen Methoden:  
  
-   `ProjectGuid`, dem die Projekt-Factory GUID zurückgegeben.  
  
-   `ProjectType`, die den lokalisierten Namen des Project-Typs zurückgibt.  
  
-   `AddFileFromTemplate`, die ausgewählten Dateien aus dem Vorlagenordner um das Zielprojekt kopiert. Diese Methode wird in einem späteren Abschnitt Weitere implementiert.  
  
 Die `SimpleProjectNode` Konstruktor, z. B. die `SimpleProjectFactory` Konstruktor speichert eine `SimpleProjectPackage` Verweis in einem privaten Feld für die spätere Verwendung.  
  
 Die Verbindung der `SimpleProjectFactory` Klasse, um die `SimpleProjectNode` -Klasse, Sie müssen ein neues instanziieren `SimpleProjectNode` in der `SimpleProjectFactory.CreateProject` Methode und speichert sie in einem privaten Feld für die spätere Verwendung zwischen.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Die Verbindung der Factoryklasse Projekt und die Knotenklasse  
  
1.  Fügen Sie die folgenden, in der Datei SimpleProjectFactory.cs `using` Anweisung:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  Ersetzen Sie die `SimpleProjectFactory.CreateProject` Methode mit dem folgenden Code.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass es ohne Fehler erstellt.  
  
## <a name="testing-the-project-node-class"></a>Testen die Klasse des Knotens  
 Testen Sie Ihr Projekt-Factory, um festzustellen, ob es sich um eine Projekthierarchie erstellt.  
  
#### <a name="to-test-the-project-node-class"></a>So testen Sie die Klasse des Knotens  
  
1.  Drücken Sie die Taste F5, um mit dem Debuggen zu beginnen. Erstellen Sie eine neue SimpleProject, in der experimentellen Instanz.  
  
2.  Visual Studio sollte die Projekt-Factory zum Erstellen eines Projekts aufrufen.  
  
3.  Schließen Sie die experimentelle Instanz von Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Hinzufügen einer benutzerdefinierten Knoten Projektsymbol  
 Das Symbol "Knoten Projekt" im vorherigen Abschnitt wird ein Standardsymbol. Sie können es in ein benutzerdefiniertes Symbol ändern.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>So fügen Sie eine benutzerdefinierte Knoten Projektsymbol hinzu  
  
1.  In der **Ressourcen** Ordner eine Bitmapdatei mit dem Namen SimpleProjectNode.bmp hinzufügen.  
  
2.  In der **Eigenschaften** Windows, reduzieren Sie die Bitmap auf 16 x 16 Pixel. Stellen Sie die Bitmap unterschiedliche.  
  
     ![Einfaches Projekt-Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  In der **Eigenschaften** Ändern der **Buildvorgang** der Bitmap auf **eingebettete Ressource**.  
  
4.  In SimpleProjectNode.cs, fügen Sie die folgenden `using` Anweisungen:  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  Fügen Sie die folgenden statischen Felds und den Konstruktor, um die `SimpleProjectNode` Klasse.  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  Fügen Sie die folgende Eigenschaft auf den Anfang der `SimpleProjectNode` Klasse.  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  Ersetzen Sie den Instanzkonstruktor durch den folgenden Code ein.  
  
    ```  
    public SimpleProjectNode(SimpleProjectPackage package)  
    {  
        this.package = package;  
  
        imageIndex = this.ImageHandler.ImageList.Images.Count;  
  
        foreach (Image img in imageList.Images)  
        {  
            this.ImageHandler.AddImage(img);  
        }  
    }  
    ```  
  
 Während der statischen Konstruktion `SimpleProjectNode` Bitmap der Projekt-Knoten aus dem manifest Assemblyressourcen abgerufen und in ein privates Feld für die spätere Verwendung zwischengespeichert. Beachten Sie die Syntax der <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> Bildpfad. Um die Namen der in einer Assembly eingebettete Manifesten Ressourcen anzuzeigen, verwenden die <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> Methode. Wenn diese Methode angewendet wird, um die `SimpleProject` Assembly, die Ergebnisse sollten wie folgt lauten:  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 Während der Erstellung der Instanz die `ProjectNode` Basisklasse lädt Resources.imagelis.bmp, werden Sie in der eingebetteten häufig verwendete 16 x 16-Bitmaps aus Resources\imagelis.bmp. Diese Liste mithilfe einer Bitmap zur Verfügung gestellt wird `SimpleProjectNode` als ImageHandler.ImageList. `SimpleProjectNode` Fügt das Projekt Knoten mithilfe einer Bitmap zur Liste. Der Offset der Bitmap für die Projekt-Knoten in der Bildliste wird für die spätere Verwendung als Wert des öffentlichen zwischengespeichert `ImageIndex` Eigenschaft. Visual Studio verwendet diese Eigenschaft, um zu bestimmen, welche Bitmuster, das als das Symbol "Knoten" angezeigt.  
  
## <a name="testing-the-custom-project-node-icon"></a>Testen das Symbol "Benutzerdefinierte Projektvorlagen Knoten"  
 Testen Sie Ihr Projekt-Factory, um festzustellen, ob es eine Projekthierarchie erstellt, die Ihre benutzerdefinierte Knoten Projektsymbol verfügt.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>So testen Sie das Symbol "Benutzerdefinierte Projektvorlagen Knoten"  
  
1.  Mit dem beginnen Sie Debuggen, und erstellen Sie in der experimentellen Instanz eine neue SimpleProject.  
  
2.  Das neu erstellte Projekt bemerken Sie, dass SimpleProjectNode.bmp als das Symbol "Knoten" verwendet wird.  
  
     ![Einfaches Projekt neue Projektknoten](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Öffnen Sie "Program.cs" im Code-Editor. Daraufhin sollte Quellcode, die den folgenden Code ähnelt.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Beachten Sie, dass die Vorlagenparameter $nameSpace$ und $ $className keine neuen Werte ein. Sie erfahren, wie Vorlagen-Vorlagenparameter im nächsten Abschnitt implementiert.  
  
## <a name="substituting-template-parameters"></a>Ersetzen Vorlagenparameter  
 In einem früheren Abschnitt Sie die Projektvorlage in Visual Studio registriert mithilfe der `ProvideProjectFactory` Attribut. Registrieren den Pfad eines Vorlagenordners auf diese Weise ermöglicht eine Ersetzung von Typparametern Basisvorlage durch Überschreiben erweitern die `ProjectNode.AddFileFromTemplate` Klasse. Weitere Informationen finden Sie unter [neue Projekterstellung: Details, Teil 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Jetzt Ersatzcode zum Hinzufügen der `AddFileFromTemplate` Klasse.  
  
#### <a name="to-substitute-template-parameters"></a>Zum Ersetzen von Vorlagenparametern  
  
1.  Fügen Sie die folgenden, in der Datei SimpleProjectNode.cs `using` Anweisung.  
  
    ```  
    using System.IO;  
    ```  
  
2.  Ersetzen Sie die `AddFileFromTemplate` Methode mit dem folgenden Code.  
  
    ```  
    public override void AddFileFromTemplate(  
        string source, string target)  
    {  
        string nameSpace =   
            this.FileTemplateProcessor.GetFileNamespace(target, this);  
        string className = Path.GetFileNameWithoutExtension(target);  
  
        this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);  
        this.FileTemplateProcessor.AddReplace("$className$", className);  
  
        this.FileTemplateProcessor.UntokenFile(source, target);  
        this.FileTemplateProcessor.Reset();  
    }  
    ```  
  
3.  Legen Sie einen Haltepunkt in der Methode, direkt hinter der `className` zuweisungsanweisung.  
  
 Die zuweisungsanweisungen bestimmen die geeignete Werte für einen Namespace und einen neuen Klassennamen. Die beiden `ProjectNode.FileTemplateProcessor.AddReplace` Methodenaufrufe ersetzen die entsprechenden Parameterwerte für die Vorlage, indem Sie diese neuen Werte.  
  
## <a name="testing-the-template-parameter-substitution"></a>Testen die Vorlage Parameterersetzung  
 Sie können jetzt die Ersetzung von Typparametern Vorlage testen.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>So testen Sie die Vorlage parameterersetzung  
  
1.  Mit dem beginnen Sie Debuggen, und erstellen Sie in der experimentellen Instanz eine neue SimpleProject.  
  
2.  Die Ausführung hält am Haltepunkt in der `AddFileFromTemplate` Methode.  
  
3.  Überprüfen Sie die Werte für die `nameSpace` und `className` Parameter.  
  
    -   `nameSpace` erhält den Wert der \<RootNamespace >-Element in der Projektdatei Vorlage \Templates\Projects\SimpleProject\SimpleProject.myproj. In diesem Fall ist der Wert "MyRootNamespace".  
  
    -   `className` der Wert, der den Quelldateinamen der Klasse, ohne die Dateinamenerweiterung erhält. In diesem Fall wird die erste Datei in den Zielordner kopiert werden soll, AssemblyInfo.cs; Daher ist der Wert der Klassenname "AssemblyInfo".  
  
4.  Entfernen Sie den Breakpoint, und drücken Sie F5, um die Ausführung fortzusetzen.  
  
     Visual Studio enden soll, erstellen ein Projekt.  
  
5.  Öffnen Sie "Program.cs" im Code-Editor. Daraufhin sollte Quellcode, die den folgenden Code ähnelt.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace MyRootNamespace  
    {  
        public class Program  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Beachten Sie, dass der Namespace jetzt ist "MyRootNamespace" und der Klassenname jetzt ist "Program".  
  
6.  Starten Sie das Debuggen des Projekts. Das neue Projekt sollte kompilieren, ausführen und Anzeigen von "Hello VSX fehlerhaft sind." im Konsolenfenster anzuzeigen.  
  
     ![Befehl einfaches Projekt](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 Herzlichen Glückwunsch! Sie haben eine grundlegende verwalteten Projektsystem implementiert.