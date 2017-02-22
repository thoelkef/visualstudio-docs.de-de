---
title: "Erstellen eine grundlegende Projektsystem, Teil 1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 47
caps.handback.revision: 47
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen eine grundlegende Projektsystem, Teil 1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visual Studio sind Projekte die Container, mit denen Entwickler Quellcodedateien und anderen Ressourcen zu organisieren. Projekte werden als untergeordnete Elemente von Projektmappen in der **Projektmappen\-Explorer**. Projekte können Sie organisieren, erstellen, Debuggen und Bereitstellen von Quellcode und Erstellen von Verweisen auf Web Services, Datenbanken und andere Ressourcen.  
  
 Projekte werden in Projektdateien, z. B. eine CSPROJ\-Datei für ein Visual C\#\-Projekt definiert. Sie können Ihren eigenen Projekttyp erstellen, der Ihre eigenen projekterweiterung verfügt. Weitere Informationen zu Projekttypen finden Sie unter [Projekttypen](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Wenn Sie Visual Studio mit einem benutzerdefinierten Typ erweitern müssen, empfiehlt sich durch die Nutzung der [Visual Studio\-Projektsystem](https://github.com/Microsoft/VSProjectSystem) die hat einer Reihe von Vorteilen, die über ein Projektsystem von Grund auf neu erstellen:  
>   
>  -   Einfacher integrieren.  Selbst ein einfaches Projekt\-System ist Tausende von Codezeilen erforderlich.  Die Kosten für das Onboarding nutzen CPS auf ein paar Klicks reduziert werden, bevor Sie ihn an Ihre Bedürfnisse anpassen möchten.  
> -   Einfachere Wartung.  Durch die Nutzung von CPS, müssen Sie nur Ihren eigenen Szenarios zu verwalten.  Wir behandeln die Instandhaltung aller Projekt Systeminfrastruktur.  
>   
>  Wenn Sie verschiedene Versionen von Visual Studio, die älter sind als Visual Studio 2013 müssen, ist eine CPS in Visual Studio\-Erweiterung nutzen nicht möglich.  Wenn dies der Fall ist, wird in dieser exemplarischen Vorgehensweise ein guter Einstieg.  
  
 In dieser exemplarischen Vorgehensweise erfahren Sie, wie ein Projekt zu erstellen, die Project\-Datei namens Erweiterung .myproj verfügt. In dieser exemplarischen Vorgehensweise ist aus vorhandenen Visual C\#\-Projektsystem.  
  
> [!NOTE]
>  Ein End\-to\-End\-Beispiel für eine vollständige Sprache\-Projektsystem, finden Sie unter Beispiel IronPython Deep Dive in [VSSDK\-Beispiele](../misc/vssdk-samples.md).  
  
 Diese exemplarische Vorgehensweise zeigt, wie Sie diese Aufgaben ausführen:  
  
-   Erstellen Sie einen einfaches Projekt\-Typ.  
  
-   Erstellen einer grundlegenden Projektvorlage.  
  
-   Registrieren Sie die Projektvorlage in Visual Studio.  
  
-   Erstellen Sie eine Projektinstanz durch Öffnen der **Neues Projekt** \(Dialogfeld\), und klicken Sie dann mit der Vorlage.  
  
-   Erstellen Sie eine Projekt\-Factory für Ihr Projektsystem.  
  
-   Erstellen Sie einen Projektknoten für Ihr Projektsystem.  
  
-   Fügen Sie benutzerdefinierte Symbole für das Projektsystem.  
  
-   Implementieren Sie die Standardvorlage Parameter ersetzt.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Außerdem müssen Sie den Quellcode Herunterladen der [Managed Package Framework für Projekte](http://mpfproj12.codeplex.com/). Extrahieren Sie die Datei an einem Speicherort, der für die Lösung verfügbar ist, die Sie erstellen möchten.  
  
## Erstellen ein einfaches Projekt  
 Erstellen Sie ein C\#\-VSIX\-Projekt namens **SimpleProject**. \(**Datei, neu, Projekt** und **C\#\-Erweiterbarkeit von Visual Studio\-Paket**\). Fügen Sie eine Visual Studio\-Paket Projektelementvorlage hinzu \(klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste des Projektknotens, und wählen Sie **Hinzufügen \/ neues Element**, wechseln Sie zu **Erweiterbarkeit \/ Visual Studio\-Paket**\). Nennen Sie die Datei **SimpleProjectPackage**.  
  
## Erstellen einer grundlegenden Projektvorlage  
 Nun können Sie diese grundlegende VSPackage zum Implementieren der neue Projekttyp .myproj ändern. Um ein Projekt zu erstellen, die auf den Projekttyp .myproj basiert, muss Visual Studio wissen, welche Dateien, Ressourcen und Verweise auf das neue Projekt hinzufügen. Um diese Informationen bereitzustellen, setzen Sie Projektdateien in einem Projektordner für die Vorlage ein. Wenn ein Benutzer das .myproj\-Projekt zum Erstellen eines Projekts verwendet wird, werden die Dateien in das neue Projekt kopiert.  
  
#### Zum Erstellen einer grundlegenden Projektvorlage  
  
1.  Das Projekt unter den anderen drei Ordner hinzugefügt: **Templates\\Projects\\SimpleProject**. \(In **Projektmappen\-Explorer**, mit der rechten Maustaste die **SimpleProject** Projektknoten, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **neuen Ordner**. Nennen Sie den Ordner `Templates`. In der **Vorlagen** Ordner, fügen Sie einen Ordner mit dem Namen `Projects`. In der **Projekte** Ordner, fügen Sie einen Ordner mit dem Namen `SimpleProject`.\)  
  
2.  In der **Projects\\SimpleProject** Ordner hinzufügen eine Symboldatei mit dem Namen `SimpleProject.ico`. Beim Klicken auf **Hinzufügen**, Symbol\-Editor wird geöffnet.  
  
3.  Stellen Sie das Symbol charakteristische. Dieses Symbol wird angezeigt, der **Neues Projekt** später in dieser exemplarischen Vorgehensweise im Dialogfeld.  
  
     ![Symbol Einfaches Projekt](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  Speichern Sie das Symbol, und schließen Sie den Symbol\-Editor.  
  
5.  In der **Projects\\SimpleProject** Ordner Hinzufügen einer **Klasse** Element mit dem Namen `Program.cs`.  
  
6.  Ersetzen Sie den vorhandenen Code durch den folgenden Zeilen.  
  
    ```c#  
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
    >  Dies ist nicht der endgültigen Form der Datei "Program.cs" Code. Der Ersetzungsparameter werden in einem späteren Schritt gelöst werden. Möglicherweise Kompilierungsfehler, aber so lange, wie der Datei **BuildAction** ist **Content**, Sie sollten in der Lage zu erstellen, und führen Sie das Projekt wie gewohnt.  
  
1.  Speichern Sie die Datei.  
  
2.  Kopieren Sie die Datei "AssemblyInfo.cs" aus der **Eigenschaften** Ordner für die **Projects\\SimpleProject** Ordner.  
  
3.  In der **Projects\\SimpleProject** Ordner hinzuzufügen, eine XML\-Datei mit dem Namen `SimpleProject.myproj`.  
  
    > [!NOTE]
    >  Die Erweiterung für alle Projekte dieser Art ist .myproj. Wenn Sie ändern möchten, müssen Sie es überall ändern, die sie in der exemplarischen Vorgehensweise erwähnt wird.  
  
4.  Ersetzen Sie den Inhalt mit den folgenden Zeilen.  
  
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
  
6.  In der **Eigenschaften** legen die **Buildvorgang** der Datei "AssemblyInfo.cs", "Program.cs", SimpleProject.ico und SimpleProject.myproj auf **Content**, und legen Sie ihre **Include in VSIX** Eigenschaften **True**.  
  
 Diese Projektvorlage beschreibt ein grundlegende Visual C\#\-Projekt, das eine Debug\-Konfiguration und einer Release\-Konfiguration hat. Das Projekt enthält zwei Quelldateien, "AssemblyInfo.cs" und "Program.cs" und mehrere Assembly verweisen. Wenn ein Projekt aus der Vorlage erstellt wird, wird der ProjectGuid Wert automatisch durch eine neue GUID ersetzt.  
  
 In **Projektmappen\-Explorer**, der erweiterten **Vorlagen** Ordner sollte wie folgt aussehen:  
  
 Vorlagen  
  
 Projekte  
  
 SimpleProject  
  
 Datei "AssemblyInfo.cs"  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## Erstellen eine einfaches Projekt\-Factory  
 Sie müssen Visual Studio den Speicherort des Projektordners Vorlage mitteilen. Zu diesem Zweck fügen Sie ein Attribut der VSPackage\-Klasse, die die Projekt\-Factory implementiert, sodass Speicherort der Vorlage an der Registrierung geschrieben wird, wenn das VSPackage erstellt wird. Zunächst erstellen eine einfaches Projekt\-Factory, die durch eine Projekt\-Factory GUID identifiziert wird. Verwenden der <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> Attribut für die Verbindung die Projekt\-Factory auf die SimpleProjectPackage\-Klasse.  
  
#### Erstellen Sie eine einfaches Projekt\-factory  
  
1.  Öffnen Sie SimpleProjectPackageGuids.cs im Code\-Editor.  
  
2.  Erstellen von GUIDs für die Projekt\-Factory \(auf der **Tools** Menü klicken Sie auf **GUID erstellen**\), oder verwenden Sie den im folgenden Beispiel. Die GUIDs der SimpleProjectPackageGuids\-Klasse hinzufügen. Die GUIDs müssen im GUID\-Format und in Form einer Zeichenfolge sein. Der resultierende Code sollte dem folgenden Beispiel entsprechen.  
  
    ```  
    static class SimpleProjectPackageGuids  
    {  
        public const string guidSimpleProjectPkgString =   
            "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
        public const string guidSimpleProjectCmdSetString =   
            "72c23e1d-f389-410a-b5f1-c938303f1391";  
        public const string guidSimpleProjectFactoryString =   
            "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
        public static readonly Guid guidSimpleProjectCmdSet =   
            new Guid(guidSimpleProjectCmdSetString);  
        public static readonly Guid guidSimpleProjectFactory =   
            new Guid(guidSimpleProjectFactoryString);  
    }  
    ```  
  
3.  Fügen Sie am Anfang eine Klasse **SimpleProject** Ordner mit dem Namen `SimpleProjectFactory.cs`.  
  
4.  Fügen Sie die folgende using\-Anweisungen:  
  
    ```  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Ein Guid\-Attribut der SimpleProjectFactory\-Klasse hinzufügen. Der Wert des Attributs ist der neuen Projekt\-Factory GUID.  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 Jetzt können Sie Ihre Projektvorlage registrieren.  
  
#### Registrieren Sie die Projektvorlage  
  
1.  Fügen Sie in SimpleProjectPackage.cs, ein <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> \-Attribut auf die Klasse SimpleProjectPackage wie folgt.  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass es fehlerfrei erstellt.  
  
     Neu erstellen, wird die Projektvorlage registriert.  
  
 Die Parameter `defaultProjectExtension` und `possibleProjectExtensions` auf das projektdateierweiterung \(.myproj\) festgelegt sind. Die `projectTemplatesDirectory` Parameter auf den relativen Pfad des Ordners Vorlagen festgelegt ist. Während des Builds wird dieser Pfad auf einen vollständigen Build konvertiert und in der Registrierung registriert das Projektsystem hinzugefügt werden.  
  
## Testen die Vorlagenregistrierung  
 Vorlagenregistrierung teilt Visual Studio den Speicherort des Projektordners Vorlage, damit Visual Studio anzeigen können, den Vorlagennamen und das Symbol in der **Neues Projekt** \(Dialogfeld\).  
  
#### So testen Sie die vorlagenregistrierung  
  
1.  Drücken Sie F5, um eine experimentelle Instanz von Visual Studio debuggen.  
  
2.  Erstellen Sie ein neues Projekt des Typs neu erstelltes Projekt in der experimentellen Instanz. In der **Neues Projekt** Dialogfeld sollte **SimpleProject** unter **Installierte Vorlagen**.  
  
 Sie haben jetzt eine Projekt\-Factory, die registriert wird. Es kann keine jedoch noch ein Projekt erstellen. Das Projektpaket und das Projekt\-Factory zusammenarbeiten, um das Erstellen und initialisieren ein Projekt.  
  
## Fügen Sie den Managed Package Framework\-code  
 Implementieren Sie die Verbindung zwischen dem Projektpaket und der Projekt\-Factory.  
  
-   Importieren Sie die Dateien der Quellcode für die Managed Package Framework.  
  
    1.  Entladen Sie das Projekt SimpleProject \(in **Projektmappen\-Explorer**, wählen Sie den Projektknoten, und klicken Sie im Kontextmenü auf **Projekt entladen**.\) und öffnen Sie die Projektdatei im XML\-Editor.  
  
    2.  Fügen Sie die folgenden Datenblöcke in die Projektdatei \(direkt über die Blöcke \< Import \>\). Legen Sie ProjectBasePath auf den Speicherort der Datei ProjectBase.files in der Managed Package Framework\-Code, den Sie gerade heruntergeladen haben. Sie müssen möglicherweise einen umgekehrten Schrägstrich auf den Pfadnamen hinzufügen. Wenn dies nicht der Fall kann das Projekt möglicherweise den Managed Package Framework\-Code zu suchen.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  Vergessen Sie nicht den umgekehrten Schrägstrich am Ende des Pfads.  
  
    3.  Laden Sie das Projekt neu.  
  
    4.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
        -   Microsoft.VisualStudio.Designer.Interfaces \(in \< VSSDK installieren \> \\VisualStudioIntegration\\Common\\Assemblies\\v2.0\)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### Die Projekt\-Factory initialisiert werden.  
  
1.  Fügen Sie in der Datei SimpleProjectPackage.cs die folgenden `using` Anweisung.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Leiten Sie die `SimpleProjectPackage` \-Klasse von `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Registrieren Sie die Projekt\-Factory. Fügen Sie die folgende Zeile in der `SimpleProjectPackage.Initialize` \-Methode direkt nach `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Implementieren Sie die abstrakte Eigenschaft `ProductUserContext`:  
  
    ```c#  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  Fügen Sie folgende SimpleProjectFactory.cs, `using` Anweisung nach dem vorhandenen `using` Anweisungen.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Leiten Sie die `SimpleProjectFactory` \-Klasse von `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Fügen Sie die folgenden dummy\-Methode, um die `SimpleProjectFactory` Klasse. Diese Methode wird in einem späteren Abschnitt implementiert.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Fügen Sie die folgenden Feld und Konstruktor, um die `SimpleProjectFactory` Klasse. Diese `SimpleProjectPackage` Verweis wird in einem privaten Feld zwischengespeichert, sodass sie bei der Festlegung einer dienstanbieterstandort verwendet werden kann.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass es fehlerfrei erstellt.  
  
## Testen die Projekt\-Factory\-Implementierung  
 Testen Sie, ob der Konstruktor für die Implementierung des Projekt\-Factory aufgerufen wird.  
  
#### So testen Sie die Projekt\-Factory\-Implementierung  
  
1.  Legen Sie einen Haltepunkt in der Datei SimpleProjectFactory.cs in der folgenden Zeile in der `SimpleProjectFactory` Konstruktor.  
  
    ```  
    this.package = package;  
    ```  
  
2.  Drücken Sie F5, um eine experimentelle Instanz von Visual Studio zu starten.  
  
3.  Starten Sie in der experimentellen Instanz ein neues Projekt zu erstellen. In der **Neues Projekt** wählen Sie im Dialogfeld die SimpleProject Projekttyp, und klicken Sie dann auf **OK**. Die Ausführung hält am Haltepunkt an.  
  
4.  Löschen Sie den Haltepunkt, und das Debuggen beendet. Da wir noch einen Projektknoten erstellt haben, löst die Erstellung Projektcode weiterhin Ausnahmen aus.  
  
## Erweitern Sie die Projekt\-Knoten\-Klasse  
 Nachdem Sie implementieren können, die `SimpleProjectNode` \-Klasse, die von abgeleitet ist die `ProjectNode` Klasse. Die `ProjectNode` Basisklasse behandelt die folgenden Aufgaben der Erstellung:  
  
-   Kopiert die Datei zum Projekt der Vorlage SimpleProject.myproj, auf dem neuen Projektordner. Die Kopie wird umbenannt, entsprechend den Namen, die eingegeben werden in der **Neues Projekt** \(Dialogfeld\). Die `ProjectGuid` Eigenschaftswert wird durch eine neue GUID ersetzt.  
  
-   Durchläuft die MSBuild\-Elemente für die Vorlage Projektdatei SimpleProject.myproj, und sucht nach `Compile` Elemente. Für jede `Compile` Zieldatei, die Datei auf dem neuen Projektordner kopiert.  
  
 Die abgeleitete `SimpleProjectNode` Klasse behandelt diese Aufgaben:  
  
-   Symbole für Projekt\- und Knoten können **Projektmappen\-Explorer** erstellt oder ausgewählt werden.  
  
-   Ermöglicht zusätzliche Vorlage parameterersetzungen angegeben werden.  
  
#### So erweitern Sie die Projekt\-Knoten\-Klasse  
  
1.  
  
2.  Fügen Sie eine Klasse mit dem Namen `SimpleProjectNode.cs`.  
  
3.  Ersetzen Sie den vorhandenen Code durch den folgenden Code ein.  
  
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
                get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
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
  
 Diese `SimpleProjectNode` Implementierung hat diese überschriebenen Methoden:  
  
-   `ProjectGuid`, die die GUID des Projekt\-Factory zurückgibt.  
  
-   `ProjectType`, die den lokalisierten Namen des Projekttyps zurückgibt.  
  
-   `AddFileFromTemplate`, die ausgewählten Dateien aus dem Vorlagenordner auf das Zielprojekt kopiert. Diese Methode wird weiter in einem späteren Abschnitt implementiert.  
  
 Die `SimpleProjectNode` Konstruktor, z. B. die `SimpleProjectFactory` Konstruktor speichert einen `SimpleProjectPackage` Verweis in einem privaten Feld für die spätere Verwendung.  
  
 Die Verbindung der `SimpleProjectFactory` \-Klasse auf die `SimpleProjectNode` \-Klasse, Sie müssen ein neues instanziieren `SimpleProjectNode` in die `SimpleProjectFactory.CreateProject` Methode und in einem privaten Feld für die spätere Verwendung zwischengespeichert werden.  
  
#### Die Verbindung der Projekt\-Factory\-Klasse und die Knotenklasse  
  
1.  Fügen Sie in der Datei SimpleProjectFactory.cs die folgenden `using` Anweisung:  
  
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
  
3.  Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass es fehlerfrei erstellt.  
  
## Testen der Projekt\-Knoten\-Klasse  
 Testen Sie Ihrer Projekt\-Factory, um festzustellen, ob es eine Projekthierarchie erstellt.  
  
#### So testen Sie die Projekt\-Knoten\-Klasse  
  
1.  Drücken Sie die Taste F5, um mit dem Debuggen zu beginnen. Erstellen Sie eine neue SimpleProject, in der experimentellen Instanz.  
  
2.  Visual Studio sollte die Projekt\-Factory zum Erstellen eines Projekts aufrufen.  
  
3.  Schließen Sie die experimentelle Instanz von Visual Studio.  
  
## Hinzufügen von benutzerdefinierten Projektsymbol Knoten  
 Das Symbol des Projekt\-Knoten aus dem vorherigen Abschnitt wird ein Standardsymbol. Sie können es in ein benutzerdefiniertes Symbol ändern.  
  
#### Benutzerdefinierte Projektsymbol Knoten hinzufügen  
  
1.  In der **Ressourcen** Ordner, fügen Sie eine Bitmapdatei mit dem Namen SimpleProjectNode.bmp.  
  
2.  In der **Eigenschaften** Windows, reduzieren Sie die Bitmap auf 16 x 16 Pixel. Stellen Sie die Bitmap charakteristische.  
  
     ![Einfaches Projekt &#45; Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  In der **Eigenschaften** ändern die **Buildvorgang** der Bitmap auf **eingebettete Ressource**.  
  
4.  Fügen Sie folgende SimpleProjectNode.cs, `using` Anweisungen:  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  Fügen Sie die folgende statische Feld und einen Konstruktor, um die `SimpleProjectNode` Klasse.  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  Fügen Sie die folgende Eigenschaft am Anfang der `SimpleProjectNode` Klasse.  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  Ersetzen Sie den Instanzkonstruktor, durch den folgenden Code.  
  
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
  
 Während der Erstellung statischer `SimpleProjectNode` Bitmap für die Projekt\-Knoten aus der Assemblymanifestressourcen abgerufen und in einem privaten Feld für die spätere Verwendung zwischengespeichert. Beachten Sie die Syntax der <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> Bildpfad. Um die Namen der in einer Assembly eingebettete Manifesten Ressourcen anzuzeigen, verwenden die <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> Methode. Wenn diese Methode angewendet wird, um die `SimpleProject` \-Assembly, die Ergebnisse sollten wie folgt lauten:  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 Während der Erstellung der Instanz die `ProjectNode` Basisklasse Resources.imagelis.bmp, werden Sie in der eingebetteten häufig verwendete 16 x 16\-Bitmaps aus Resources\\imagelis.bmp lädt. Diese Bitmap\-Liste zur Verfügung gestellt wird `SimpleProjectNode` als ImageHandler.ImageList.`SimpleProjectNode` Fügt die Bitmap für die Projekt\-Knoten in der Liste. Der Offset der Bitmap für die Projekt\-Knoten in der Bildliste wird für die spätere Verwendung als Wert für die Öffentlichkeit zwischengespeichert `ImageIndex` Eigenschaft. Visual Studio verwendet diese Eigenschaft bestimmt die Bitmap als Symbol für den Projekt\-Knoten angezeigt.  
  
## Testen das Symbol für den benutzerdefinierten Projekt\-Knoten  
 Testen Sie die Projekt\-Factory um festzustellen, ob eine Projekthierarchie erstellt, die Ihre benutzerdefinierten Knoten Projektsymbol verfügt.  
  
#### So testen Sie das Symbol für den benutzerdefinierten Projekt\-Knoten  
  
1.  Starten Sie das Debuggen, und erstellen Sie in der experimentellen Instanz eine neue SimpleProject.  
  
2.  Beachten Sie, dass SimpleProjectNode.bmp als Symbol für den Projekt\-Knoten, in das Projekt neu erstellt.  
  
     ![Einfaches Projekt &#45; Knoten Neues Projekt](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Öffnen Sie die Datei "Program.cs" im Code\-Editor. Quellcode, die dem folgenden Code ähnelt, sollte angezeigt werden.  
  
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
  
     Beachten Sie, dass die Vorlagenparameter $nameSpace$ und $ $className keine neuen Werte. Sie erfahren, wie Vorlage Parameter ersetzt im nächsten Abschnitt implementiert.  
  
## Vorlagenparameter ersetzen  
 In einem Abschnitt weiter oben Sie registriert die Projektvorlage mit Visual Studio mithilfe der `ProvideProjectFactory` Attribut. Registrieren den Pfad eines Ordners Vorlage auf diese Weise können Sie einfache Vorlage Parameter ersetzt zu aktivieren, indem überschreiben und Erweitern der `ProjectNode.AddFileFromTemplate` Klasse. Weitere Informationen finden Sie unter [Neue Project\-Generierung: Hinter den Kulissen, Teil 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Nun fügen Sie Ersetzungscode die `AddFileFromTemplate` Klasse.  
  
#### Vorlagenparameter ersetzen  
  
1.  Fügen Sie in der Datei SimpleProjectNode.cs die folgenden `using` Anweisung.  
  
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
  
3.  Legen Sie einen Haltepunkt in der Methode direkt nach der `className` Zuweisung.  
  
 Die zuweisungsanweisungen bestimmen die geeignete Werte für einen Namespace und einen neuen Klassennamen. Die beiden `ProjectNode.FileTemplateProcessor.AddReplace` Methodenaufrufe ersetzen die entsprechenden Parameterwerte der Vorlage mit diesen neuen Werten.  
  
## Testen die Vorlage Parameterersetzung  
 Jetzt können Sie die parameterersetzung Vorlage testen.  
  
#### So testen Sie die Vorlage parameterersetzung  
  
1.  Starten Sie das Debuggen, und erstellen Sie in der experimentellen Instanz eine neue SimpleProject.  
  
2.  Die Ausführung hält am Haltepunkt in der `AddFileFromTemplate` Methode.  
  
3.  Überprüfen Sie die Werte für die `nameSpace` und `className` Parameter.  
  
    -   `nameSpace` wird der Wert des Namespace \< Root \>\-Elements in der Datei \\Templates\\Projects\\SimpleProject\\SimpleProject.myproj Vorlage zugewiesen werden. In diesem Fall ist der Wert "MyRootNamespace".  
  
    -   `className` erhält den Wert der Klasse der Name der Quelldatei, ohne die Erweiterung. In diesem Fall ist die erste Datei in den Zielordner kopiert werden "AssemblyInfo.cs". Daher ist der Wert der ClassName "AssemblyInfo".  
  
4.  Entfernen Sie den Haltepunkt, und drücken Sie F5, um die Ausführung fortzusetzen.  
  
     Visual Studio sollte ein Projekt fertigzustellen.  
  
5.  Öffnen Sie die Datei "Program.cs" im Code\-Editor. Quellcode, die dem folgenden Code ähnelt, sollte angezeigt werden.  
  
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
  
     Beachten Sie, dass der Namespace jetzt ist "MyRootNamespace" und der Klassenname nun ist "Program".  
  
6.  Starten Sie das Projekt debuggen. Das neue Projekt sollten kompilieren, ausführen und Anzeigen von "Hello VSX\!\!\!" im Konsolenfenster angezeigt.  
  
     ![Befehl Einfaches Projekt](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 Herzlichen Glückwunsch\! Sie haben eine grundlegende verwalteten Projektsystem implementiert.