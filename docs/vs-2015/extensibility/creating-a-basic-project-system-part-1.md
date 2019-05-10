---
title: Erstellen eines grundlegenden Projektsystems, Teil 1 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8304719a4b15b5f23957c99244796999d7b3f55c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439399"
---
# <a name="creating-a-basic-project-system-part-1"></a>Erstellen eines grundlegenden Projektsystems, Teil 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio sind Projekte die Container, die Entwickler verwenden, um Quellcodedateien und anderen Ressourcen zu organisieren. Projekte werden als untergeordnete Elemente von Lösungen in der **Projektmappen-Explorer**. Projekte können Sie die zu organisieren, erstellen, Debuggen, und Quellcode bereitstellen und Verweise auf die Web Services, Datenbanken und andere Ressourcen erstellen.  
  
 Projekte werden in Projektdateien, z. B. einer CSPROJ-Datei für ein Visual C#-Projekt definiert. Sie können Ihren eigenen Projekttyp erstellen, die Ihre eigenen Projekt-Dateierweiterung aufweist. Weitere Informationen zu Projekttypen, finden Sie unter [Projekttypen](../extensibility/internals/project-types.md).  
  
> [!NOTE]
> Wenn Sie Visual Studio mit einem benutzerdefinierten Projekttyp erweitern müssen, sollten Sie dringend nutzen die [Visual Studio-Projektsystem](https://github.com/Microsoft/VSProjectSystem) der hat einer Reihe von Vorteilen, die über ein Projektsystem von Grund auf neu erstellen:  
> 
> - Einfacher integrieren.  Sogar ein grundlegenden Projektsystems erfordert Tausende von Codezeilen erforderlich.  Die Onboarding-Kosten auf ein paar Klicks CPS Nutzung reduziert werden, bevor Sie es an Ihre Bedürfnisse anpassen möchten.  
>   - Einfachere Verwaltung.  Durch die Nutzung CPS, müssen Sie nur Ihren eigenen Szenarios zu verwalten.  Wir kümmern uns um die Wartung der alle von der Project-System-Infrastruktur.  
> 
>   Wenn die Ausrichtung auf Versionen von Visual Studio, die älter als Visual Studio 2013 erforderlich, werden Sie nicht CPS in Visual Studio-Erweiterung nutzen können.  Wenn dies der Fall ist, ist in dieser exemplarischen Vorgehensweise ein guter Ausgangspunkt, um zu beginnen.  
  
 Diese exemplarische Vorgehensweise veranschaulicht die ein Projekt zu erstellen, die Project-Datei Name Erweiterung .myproj verfügt. In dieser exemplarischen Vorgehensweise, die aus dem vorhandenen Visual C#-Projektsystem nutzt Teile.  
  
> [!NOTE]
> Ein End-to-End-Beispiel von ein Projektsystem vollständige Sprache finden Sie ausführliche Erläuterungen der IronPython-Beispiel in [VSSDK-Beispiele](../misc/vssdk-samples.md).  
  
 In dieser exemplarischen Vorgehensweise erfahren, wie diese Aufgaben auszuführen:  
  
- Erstellen Sie ein einfaches Projekt.  
  
- Erstellen Sie eine basic-Projektvorlage aus.  
  
- Registrieren Sie die Projektvorlage in Visual Studio.  
  
- Erstellen Sie eine Projektinstanz durch Öffnen der **neues Projekt** Dialogfeld und klicken Sie dann mithilfe Ihrer Vorlage.  
  
- Erstellen Sie eine Projektzuordnungsinstanz für Ihr Projektsystem.  
  
- Erstellen Sie einen Projektknoten aus, für Ihr Projektsystem.  
  
- Fügen Sie benutzerdefinierte Symbole für das Projektsystem hinzu.  
  
- Implementieren Sie die parameterersetzung Basisvorlage.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Sie müssen auch herunterladen, den Quellcode für die [Managed Package Framework for Projects](http://mpfproj12.codeplex.com/). Extrahieren Sie die Datei an einem Speicherort, der mit der Lösung zugänglich ist, die zu erstellen.  
  
## <a name="creating-a-basic-project-type"></a>Erstellen ein einfaches Projekt  
 Erstellen Sie ein C#-VSIX-Projekt mit dem Namen **SimpleProject**. (**Datei, neu, Projekt** und dann **C#-Erweiterbarkeit von Visual Studio-Paket**). Fügen Sie eine Visual Studio-Paket-Projektelementvorlage hinzu (klicken Sie auf im Projektmappen-Explorer mit der rechten Maustaste des Projektknotens, und wählen **hinzufügen / neues Element**, navigieren Sie zu **Erweiterbarkeit / Visual Studio-Paket**). Nennen Sie die Datei **SimpleProjectPackage**.  
  
## <a name="creating-a-basic-project-template"></a>Erstellen einer Basic-Projektvorlage  
 Jetzt können Sie diese grundlegende VSPackage zum Implementieren des neue Projekttyps für .myproj ändern. Um ein Projekt erstellen, die auf den Projekttyp .myproj basiert, muss Visual Studio wissen, welche Dateien, Ressourcen und Verweise auf das neue Projekt hinzugefügt. Um diese Informationen bereitzustellen, platzieren Sie Projektdateien in einem Projektordner für die Vorlage ein. Wenn ein Benutzer das .myproj-Projekt zum Erstellen eines Projekts verwendet wird, werden die Dateien in das neue Projekt kopiert.  
  
#### <a name="to-create-a-basic-project-template"></a>Zum Erstellen einer Vorlage für die basic-Projekts  
  
1. Fügen Sie dem Projekt eine der anderen drei Ordner hinzu: **Templates\Projects\SimpleProject**. (In **Projektmappen-Explorer**, mit der rechten Maustaste die **SimpleProject** Projekt, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neuer Ordner**. Geben Sie dem Ordner den Namen `Templates`anmelden. In der **Vorlagen** Ordner, fügen Sie einen Ordner mit dem Namen `Projects`. In der **Projekte** Ordner, fügen Sie einen Ordner mit dem Namen `SimpleProject`.)  
  
2. In der **Projects\SimpleProject** Ordner hinzufügen, eine Symboldatei, die mit dem Namen `SimpleProject.ico`. Beim Klicken auf **hinzufügen**, Symbol-Editor wird geöffnet.  
  
3. Stellen Sie das Symbol unterschiedliche. Dieses Symbol wird angezeigt, der **neues Projekt** Dialogfeld weiter unten in dieser exemplarischen Vorgehensweise.  
  
    ![Symbol Einfaches Projekt](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4. Speichern Sie das Symbol "", und schließen Sie die Symbol-Editor.  
  
5. In der **Projects\SimpleProject** Ordner Hinzufügen einer **Klasse** Element mit dem Namen `Program.cs`.  
  
6. Ersetzen Sie den vorhandenen Code durch die folgenden Zeilen ein.  
  
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
   > Dies ist nicht das endgültige Format des Codes "Program.cs". die Ersetzungsparameter werden in einem späteren Schritt hostrichtlinieninformationen werden. Möglicherweise Kompilierungsfehler, jedoch so lange, wie der Datei **BuildAction** ist **Content**, Sie sollten in der Lage zu erstellen, und führen das Projekt wie gewohnt.  
  
7. Speichern Sie die Datei.  
  
8. Kopieren Sie die Datei "AssemblyInfo.cs" aus der **Eigenschaften** Ordner, um die **Projects\SimpleProject** Ordner.  
  
9. In der **Projects\SimpleProject** Ordner hinzufügen, eine XML-Datei mit dem Namen `SimpleProject.myproj`.  
  
   > [!NOTE]
   > Die Dateinamenerweiterung für alle Projekte dieses Typs ist .myproj. Wenn Sie sie ändern möchten, müssen Sie es überall ändern, die sie in der exemplarischen Vorgehensweise erwähnt wird.  
  
10. Ersetzen Sie den vorhandenen Inhalt durch die folgenden Zeilen ein.  
  
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
  
11. Speichern Sie die Datei.  
  
12. In der **Eigenschaften** legen die **Buildvorgang** der Datei "AssemblyInfo.cs", "Program.cs", SimpleProject.ico und SimpleProject.myproj zu **Content**, und legen Sie deren  **In VSIX einbeziehen** Eigenschaften **"true"**.  
  
    Diese Projektvorlage beschreibt ein einfaches Visual C#-Projekt, das sowohl eine Debug-Konfiguration und einer Releasekonfiguration aufweist. Das Projekt enthält zwei Quelldateien, Datei "AssemblyInfo.cs" und "Program.cs", und mehrere Assembly verweisen. Wenn ein Projekt aus der Vorlage erstellt wird, wird der ProjectGuid Wert automatisch durch eine neue GUID ersetzt.  
  
    In **Projektmappen-Explorer**, dem erweiterten **Vorlagen** Ordner sollte wie folgt aussehen:  
  
    Vorlagen  
  
    Projekte  
  
    SimpleProject  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    SimpleProject.ico  
  
    SimpleProject.myproj  
  
## <a name="creating-a-basic-project-factory"></a>Erstellen einer Basic Projektfactory  
 Sie müssen Visual Studio den Speicherort Ihres Projektordners für die Vorlage mitteilen. Zu diesem Zweck fügen Sie ein Attribut hinzu, der VSPackage-Klasse, die die Projektfactory implementiert, sodass der Speicherort der Vorlage in der systemregistrierung geschrieben wird, wenn das VSPackage erstellt wird. Zunächst erstellen eine einfaches Projekt-Factory, die durch eine Projektzuordnungsinstanz GUID identifiziert wird. Verwenden der <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> Attribut zur Verbindung der SimpleProjectPackage-Klasse mit der Projektfactory.  
  
#### <a name="to-create-a-basic-project-factory"></a>Zum Erstellen einer basic Projektfactory  
  
1. SimpleProjectPackageGuids.cs im Code-Editor zu öffnen.  
  
2. Erstellen von GUIDs für die Projektfactory (auf der **Tools** Menü klicken Sie auf **GUID erstellen**), oder verwenden Sie die im folgenden Beispiel. Die GUIDs der SimpleProjectPackageGuids-Klasse hinzufügen. Die GUIDs müssen in Form einer Zeichenfolge und GUID-Format sein. Der resultierende Code sollte im folgende Beispiel ähneln.  
  
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
  
3. Fügen Sie eine Klasse an den Anfang **SimpleProject** Ordner mit dem Namen `SimpleProjectFactory.cs`.  
  
4. Fügen Sie die folgenden using-Anweisungen:  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. Ein Guid-Attribut der SimpleProjectFactory-Klasse hinzufügen. Der Wert des Attributs ist das neue Projektzuordnungsinstanz-GUID.  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   Jetzt können Sie Ihre Projektvorlage registrieren.  
  
#### <a name="to-register-the-project-template"></a>Registrieren Sie die Projektvorlage  
  
1. Fügen Sie in SimpleProjectPackage.cs, eine <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> -Attribut der Klasse SimpleProjectPackage wie folgt.  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass es fehlerfrei erstellt.  
  
    Neuerstellen von registriert die Projektvorlage aus.  
  
   Die Parameter `defaultProjectExtension` und `possibleProjectExtensions` auf die Projekt-Dateinamenerweiterung (.myproj) festgelegt sind. Die `projectTemplatesDirectory` -Parameter auf den relativen Pfad der Ordner "Templates" festgelegt ist. Während des Builds wird dieser Pfad konvertiert werden, um eine vollständige Erstellung und der Registrierung, um das Projektsystem registrieren hinzugefügt werden.  
  
## <a name="testing-the-template-registration"></a>Testen die Registrierung der Vorlage  
 Vorlagenregistrierung teilt Visual Studio den Speicherort Ihres Projektordners für die Vorlage, damit Visual Studio anzeigen können, den Vorlagennamen und ein Symbol in der **neues Projekt** Dialogfeld.  
  
#### <a name="to-test-the-template-registration"></a>So testen Sie die Registrierung der Vorlage  
  
1. Drücken Sie F5, um eine experimentelle Instanz von Visual Studio debuggen zu starten.  
  
2. Erstellen Sie in der experimentellen Instanz ein neues Projekt des Typs neu erstelltes Projekt. In der **neues Projekt** Dialogfeld sollte **SimpleProject** unter **installierte Vorlagen**.  
  
   Sie haben jetzt eine Projektfactory, die registriert wird. Allerdings kann nicht es noch ein Projekt erstellen. Das Projektpaket und das Projekt-Factory zusammenarbeiten, um das Erstellen und initialisieren ein Projekt.  
  
## <a name="add-the-managed-package-framework-code"></a>Fügen Sie den Code des Managed Package Framework  
 Implementieren Sie die Verbindung zwischen dem Projektpaket und die Projektzuordnungsinstanz.  
  
- Importieren Sie die Quellcodedateien für Managed Package Framework an.  
  
    1. Entladen Sie das Projekt SimpleProject (in **Projektmappen-Explorer**, wählen Sie den Projektknoten, und klicken Sie im Kontextmenü auf **Projekt entladen**.), und öffnen Sie die Projektdatei im XML-Editor.  
  
    2. Fügen Sie die folgenden Blöcke in die Projektdatei (direkt über die \<Import > Blöcke). Legen Sie ProjectBasePath, auf den Speicherort der Datei ProjectBase.files in der Managed Package Framework-Code, den Sie gerade heruntergeladen haben. Möglicherweise müssen einen umgekehrten Schrägstrich den Pfadnamen hinzu. Wenn Sie nicht, kann das Projekt möglicherweise den Managed Package Framework-Code zu finden.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        > Vergessen Sie nicht den umgekehrten Schrägstrich am Ende des Pfads.  
  
    3. Laden Sie das Projekt ein.  
  
    4. Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
        - Microsoft.VisualStudio.Designer.Interfaces (in \<VSSDK-Installation > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        - WindowsBase  
  
        - Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Um den Projekt-Factory initialisieren  
  
1. Fügen Sie die folgenden, in der Datei SimpleProjectPackage.cs `using` Anweisung.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2. Leiten Sie die `SimpleProjectPackage` -Klasse aus `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3. Registrieren der Projektzuordnungsinstanz. Die folgende Zeile zum Hinzufügen der `SimpleProjectPackage.Initialize` -Methode, direkt nach `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4. Implementiert die abstrakte Eigenschaft `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5. Fügen Sie die folgende SimpleProjectFactory.cs, `using` Anweisung nach den vorhandenen `using` Anweisungen.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6. Leiten Sie die `SimpleProjectFactory` -Klasse aus `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7. Fügen Sie die folgende dummy-Methode, die `SimpleProjectFactory` Klasse. Sie implementieren diese Methode in einem späteren Abschnitt.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8. Fügen Sie das folgende Feld und der Konstruktor, um die `SimpleProjectFactory` Klasse. Dies `SimpleProjectPackage` Verweis wird in einem privaten Feld zwischengespeichert, sodass sie beim Festlegen von einer Dienstanbieter-Website verwendet werden kann.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass es fehlerfrei erstellt.  
  
## <a name="testing-the-project-factory-implementation"></a>Testen die Projekt-Factory-Implementierung  
 Testet, ob der Konstruktor für die Implementierung des Projekt-Factory aufgerufen wird.  
  
#### <a name="to-test-the-project-factory-implementation"></a>So testen Sie die Projekt-Factory-Implementierung  
  
1. Legen Sie in der Datei SimpleProjectFactory.cs einen Haltepunkt in der folgenden Zeile in der `SimpleProjectFactory` Konstruktor.  
  
    ```  
    this.package = package;  
    ```  
  
2. Drücken Sie F5, um eine experimentelle Instanz von Visual Studio zu starten.  
  
3. Starten Sie in der experimentellen Instanz ein um ein neues Projekt zu erstellen. In der **neues Projekt** wählen Sie im Dialogfeld die SimpleProject Projekttyp, und klicken Sie dann auf **OK**. Die Ausführung hält am Haltepunkt an.  
  
4. Löschen Sie den Haltepunkt, und beenden Sie des Debuggens. Da wir einen Projektknoten aus noch nicht erstellt haben, löst die Erstellung Projektcode weiterhin Ausnahmen aus.  
  
## <a name="extending-the-project-node-class"></a>Erweitern Sie die Projekt-Node-Klasse  
 Nachdem Sie implementieren können, die `SimpleProjectNode` -Klasse, die von abgeleitet ist die `ProjectNode` Klasse. Die `ProjectNode` Basisklasse behandelt der projekterstellung die folgenden Aufgaben:  
  
- Kopiert die Projekt-Vorlagendatei SimpleProject.myproj, in den neuen Projektordner. Die Kopie wird umbenannt, entsprechend den Namen, den eingegebenen der **neues Projekt** Dialogfeld. Die `ProjectGuid` Eigenschaftswert wird durch eine neue GUID ersetzt.  
  
- Durchläuft die MSBuild-Elemente von der Vorlage Projektdatei SimpleProject.myproj, und sucht nach `Compile` Elemente. Für jede `Compile` Zieldatei, die Datei in den neuen Projektordner kopiert.  
  
  Die abgeleitete `SimpleProjectNode` Klasse übernimmt diese Aufgaben:  
  
- Symbole für Projekt- und Knoten in ermöglicht **Projektmappen-Explorer** erstellt oder ausgewählt werden.  
  
- Können zusätzliche Project-Vorlage parameterersetzungen angegeben werden.  
  
#### <a name="to-extend-the-project-node-class"></a>Erweitern Sie die Projekt-Node-Klasse  
  
1. 
  
2. Fügen Sie eine Klasse, die mit dem Namen `SimpleProjectNode.cs`.  
  
3. Ersetzen Sie den vorhandenen Code durch folgenden Code:  
  
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
  
   Dies `SimpleProjectNode` Implementierung hat diese überschriebenen Methoden:  
  
- `ProjectGuid`, die die GUID des Projekt-Factory zurückgibt.  
  
- `ProjectType`, die den lokalisierten Namen des Projekttyps zurückgibt.  
  
- `AddFileFromTemplate`, die ausgewählten Dateien aus dem Vorlagenordner auf das Zielprojekt kopiert. Diese Methode wird weiter in einem späteren Abschnitt implementiert.  
  
  Die `SimpleProjectNode` Konstruktor, z. B. die `SimpleProjectFactory` Konstruktor speichert einen `SimpleProjectPackage` Verweis in einem privaten Feld für die spätere Verwendung.  
  
  Die Verbindung der `SimpleProjectFactory` -Klasse der `SimpleProjectNode` -Klasse, Sie müssen ein neues instanziieren `SimpleProjectNode` in der `SimpleProjectFactory.CreateProject` Methode, und in einem privaten Feld für die spätere Verwendung zwischengespeichert.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Die Verbindung der Projekt-Factory-Klasse und die Node-Klasse  
  
1. Fügen Sie die folgenden, in der Datei SimpleProjectFactory.cs `using` Anweisung:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2. Ersetzen Sie die `SimpleProjectFactory.CreateProject` Methode, indem Sie mit dem folgenden Code.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3. Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass es fehlerfrei erstellt.  
  
## <a name="testing-the-project-node-class"></a>Testen die Projekt-Node-Klasse  
 Testen Sie Ihr Projekt-Factory, um festzustellen, ob es sich bei der Erstellung einer Projekthierarchie.  
  
#### <a name="to-test-the-project-node-class"></a>So testen Sie die Projekt-Node-Klasse  
  
1. Drücken Sie die Taste F5, um mit dem Debuggen zu beginnen. Erstellen Sie eine neue SimpleProject, in der experimentellen Instanz.  
  
2. Visual Studio sollte Ihr Projekt-Factory zum Erstellen eines Projekts aufrufen.  
  
3. Schließen Sie die experimentelle Instanz von Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Hinzufügen einer benutzerdefinierten Projekts-Symbol "Knoten"  
 Das Symbol des Projekt-Knoten im vorherigen Abschnitt wird ein Standardsymbol. Sie können es in ein benutzerdefiniertes Symbol ändern.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Eine benutzerdefinierte Projekt-Symbol "Knoten" hinzufügen  
  
1. In der **Ressourcen** Ordner, fügen Sie eine Bitmapdatei mit dem Namen SimpleProjectNode.bmp.  
  
2. In der **Eigenschaften** Windows, reduzieren Sie die Bitmap auf 16 x 16 Pixel. Stellen Sie die Bitmap unterschiedliche.  
  
    ![Einfaches Projekt-Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3. In der **Eigenschaften** Ändern der **Buildvorgang** der Bitmap auf **eingebettete Ressource**.  
  
4. Fügen Sie die folgende SimpleProjectNode.cs, `using` Anweisungen:  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. Fügen Sie die folgenden statischen Feld und einen Konstruktor, um die `SimpleProjectNode` Klasse.  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. Fügen Sie die folgende Eigenschaft auf den Anfang der `SimpleProjectNode` Klasse.  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. Ersetzen Sie den Instanzkonstruktor, mit dem folgenden Code.  
  
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
  
   Während der statischen Konstruktion `SimpleProjectNode` Ruft die Projekt-Knoten-Bitmap aus der Assemblymanifestressourcen ab und speichert es in ein privates Feld für die spätere Verwendung. Beachten Sie, dass die Syntax der <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> Bildpfad. Um die Namen der Manifestdateien Ressourcen in eine Assembly eingebettet anzuzeigen, verwenden die <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> Methode. Wenn diese Methode angewendet wird, um die `SimpleProject` Assembly, die Ergebnisse sollten wie folgt lauten:  
  
- SimpleProject.Resources.resources  
  
- VisualStudio.Project.resources  
  
- SimpleProject.VSPackage.resources  
  
- Resources.imagelis.bmp  
  
- Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
- Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
- SimpleProject.Resources.SimpleProjectNode.bmp  
  
  Während der instanzerstellung die `ProjectNode` Basisklasse lädt Resources.imagelis.bmp, werden Sie in der eingebetteten häufig verwendete 16 x 16-Bitmaps aus Resources\imagelis.bmp. Diese Bitmap-Liste zur Verfügung gestellt wird `SimpleProjectNode` als ImageHandler.ImageList. `SimpleProjectNode` Fügt die Projekt-Knoten-Bitmap an die Liste an. Der Offset der Bitmap für die Projekt-Knoten in der Bildliste wird zwischengespeichert, für die spätere Verwendung als Wert für die Öffentlichkeit `ImageIndex` Eigenschaft. Visual Studio verwendet diese Eigenschaft, um zu bestimmen, welche Bitmap als Symbol für den Projekt-Knoten angezeigt.  
  
## <a name="testing-the-custom-project-node-icon"></a>Testen das benutzerdefinierte Projekt-Knoten-Symbol  
 Testen Sie Ihr Projekt-Factory, um festzustellen, ob es sich bei eine Projekthierarchie erstellt, die Ihre benutzerdefinierte Projekt-Symbol "Knoten".  
  
#### <a name="to-test-the-custom-project-node-icon"></a>So testen Sie das benutzerdefinierte Projekt-Knoten-Symbol  
  
1. Mit dem beginnen Sie Debuggen, und erstellen Sie in der experimentellen Instanz ein neues SimpleProject.  
  
2. Das neu erstellte Projekt bemerken Sie, dass SimpleProjectNode.bmp als Symbol für den Projekt-Knoten verwendet wird.  
  
     ![Einfaches Projekt "Neues Projekt" Knoten](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3. Öffnen Sie "Program.cs" im Code-Editor ein. Quellcode, die den folgenden Code ähnelt, sollte angezeigt werden.  
  
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
  
     Beachten Sie, dass die Vorlagenparameter $nameSpace$ und $ von $className keine neuen Werte ein. Sie erfahren, wie Vorlagen-Vorlagenparameter im nächsten Abschnitt implementiert.  
  
## <a name="substituting-template-parameters"></a>Ersetzen von Vorlagenparametern  
 In einem vorherigen Abschnitt, Sie die Projektvorlage in Visual Studio registriert unter Verwendung der `ProvideProjectFactory` Attribut. Registrieren den Pfad eines Ordners für die Vorlage auf diese Weise können Sie die parameterersetzung Basisvorlage zu aktivieren, indem Sie überschreiben und Erweitern der `ProjectNode.AddFileFromTemplate` Klasse. Weitere Informationen finden Sie unter [Generieren neuer Projekte: In die Hintergründe, Teil 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Fügen Sie jetzt Ersetzungscode die `AddFileFromTemplate` Klasse.  
  
#### <a name="to-substitute-template-parameters"></a>Vorlagenparameter ersetzen  
  
1. Fügen Sie die folgenden, in der Datei SimpleProjectNode.cs `using` Anweisung.  
  
   ```  
   using System.IO;  
   ```  
  
2. Ersetzen Sie die `AddFileFromTemplate` Methode, indem Sie mit dem folgenden Code.  
  
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
  
3. Legen Sie einen Haltepunkt in der Methode, direkt nach der `className` zuweisungsanweisung.  
  
   Die zuweisungsanweisungen bestimmen die angemessenen Werte für einen Namespace und einen neuen Klassennamen. Die beiden `ProjectNode.FileTemplateProcessor.AddReplace` Methodenaufrufe ersetzen die entsprechenden Parameterwerte für die Vorlage mit diesen neuen Werten.  
  
## <a name="testing-the-template-parameter-substitution"></a>Testen die Parameterersetzung Vorlage  
 Jetzt können Sie die parameterersetzung für die Vorlage testen.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>So testen Sie die parameterersetzung Vorlage  
  
1. Mit dem beginnen Sie Debuggen, und erstellen Sie in der experimentellen Instanz ein neues SimpleProject.  
  
2. Beendet die Ausführung am Haltepunkt in der `AddFileFromTemplate` Methode.  
  
3. Überprüfen Sie die Werte für die `nameSpace` und `className` Parameter.  
  
   - `nameSpace` erhält den Wert des der \<RootNamespace >-Element in der Vorlage \Templates\Projects\SimpleProject\SimpleProject.myproj Projektdatei. In diesem Fall ist der Wert "MyRootNamespace".  
  
   - `className` ist der Wert der Quelldateiname der Klasse, ohne die Dateinamenerweiterung angegeben werden. In diesem Fall ist die erste Datei in den Zielordner kopiert werden sollen, Datei "AssemblyInfo.cs". Daher ist der Wert der Klassenname "AssemblyInfo".  
  
4. Entfernen Sie den Haltepunkt, und drücken Sie F5, um die Ausführung fortzusetzen.  
  
    Visual Studio sollte die Erstellung eines Projekts abgeschlossen.  
  
5. Öffnen Sie "Program.cs" im Code-Editor ein. Quellcode, die den folgenden Code ähnelt, sollte angezeigt werden.  
  
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
  
6. Starten Sie das Debuggen des Projekts. Das neue Projekt sollte zu kompilieren, ausführen und Anzeigen von "Hello VSX!!!" im Konsolenfenster anzuzeigen.  
  
    ![Befehl einfaches Projekt](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
   Herzlichen Glückwunsch! Sie haben eine einfache verwaltete Projektsystem implementiert.
