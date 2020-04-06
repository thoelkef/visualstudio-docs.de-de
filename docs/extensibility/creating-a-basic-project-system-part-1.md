---
title: Erstellen eines basisgegrundlegenden Projektsystems, Teil 1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739726"
---
# <a name="create-a-basic-project-system-part-1"></a>Erstellen eines basisgegrundlegenden Projektsystems, Teil 1
In Visual Studio sind Projekte die Container, die Entwickler zum Organisieren von Quellcodedateien und anderen Assets verwenden. Projekte werden als untergeordnete Projektmappen im **Projektmappen-Explorer**angezeigt. Mit Projekten können Sie Quellcode organisieren, erstellen, debuggen und bereitstellen und Verweise auf Webdienste, Datenbanken und andere Ressourcen erstellen.

 Projekte werden in Projektdateien definiert, z. B. in einer *.csproj-Datei* für ein Visual C-Projekt. Sie können einen eigenen Projekttyp mit einer eigenen Projektdateinamenerweiterung erstellen. Weitere Informationen zu Projekttypen finden Sie unter [Projekttypen](../extensibility/internals/project-types.md).

> [!NOTE]
> Wenn Sie Visual Studio um einen benutzerdefinierten Projekttyp erweitern müssen, wird dringend empfohlen, das [Visual Studio-Projektsystem](https://github.com/Microsoft/VSProjectSystem) (VSPS) zu nutzen, das eine Reihe von Vorteilen gegenüber dem Erstellen eines Projektsystems von Grund auf bietet:
>
> - Einfacheres Onboarding.  Selbst ein einfaches Projektsystem erfordert Zehntausende von Codezeilen.  Durch die Nutzung von VSPS werden die Onboarding-Kosten auf wenige Klicks reduziert, bevor Sie sie an Ihre Anforderungen anpassen können.
> - Einfachere Wartung.  Durch die Nutzung von VSPS müssen Sie nur Ihre eigenen Szenarien verwalten.  Wir kümmern uns um die Instandhaltung der gesamten Projektsysteminfrastruktur.
>
>   Wenn Sie Versionen von Visual Studio ab Visual Studio 2013 als Ziel haben müssen, können Sie VSPS in einer Visual Studio-Erweiterung nicht nutzen.  Wenn dies der Fall ist, ist diese exemplarische Vorgehensweise ein guter Ort, um loszulegen.

 In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie einen Projekttyp mit der Projektdateinamenerweiterung *.myproj*erstellen. In dieser exemplarischen Vorgehensweise wird das vorhandene Visual C-Projektsystem ausgeliehen.

> [!NOTE]
> Weitere Beispiele für Erweiterungsprojekte finden Sie unter [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie diese Aufgaben ausführen:

- Erstellen Sie einen grundlegenden Projekttyp.

- Erstellen Sie eine grundlegende Projektvorlage.

- Registrieren Sie die Projektvorlage bei Visual Studio.

- Erstellen Sie eine Projektinstanz, indem Sie das Dialogfeld **Neues Projekt** öffnen und dann Die Vorlage verwenden.

- Erstellen Sie eine Projektfactory für Ihr Projektsystem.

- Erstellen Sie einen Projektknoten für Ihr Projektsystem.

- Fügen Sie benutzerdefinierte Symbole für das Projektsystem hinzu.

- Implementieren Sie die Ersetzung grundlegender Vorlagenparameter.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

 Sie müssen auch den Quellcode für das [Managed Package Framework für Projekte](https://github.com/tunnelvisionlabs/MPFProj10)herunterladen. Extrahieren Sie die Datei an einen Speicherort, auf den die Lösung zugreifen kann, die Sie erstellen möchten.

## <a name="create-a-basic-project-type"></a>Erstellen eines grundlegenden Projekttyps
 Erstellen Sie ein Projekt mit dem Namen **SimpleProject**. (**Datei** > **Neues** > **Projekt** und dann Visual **C-Erweiterbarkeit** > **Extensibility** > **VSIX Project**). Fügen Sie eine Visual Studio Package-Projektelementvorlage hinzu (im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten klicken und**Neues Element** **hinzufügen** > auswählen , und wechseln Sie dann zu **Extensibility** > **Visual Studio Package**). Benennen Sie die Datei *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Erstellen einer grundlegenden Projektvorlage
 Jetzt können Sie dieses grundlegende VSPackage ändern, um den neuen *.myproj-Projekttyp* zu implementieren. Um ein Projekt zu erstellen, das auf dem *.myproj-Projekttyp* basiert, muss Visual Studio wissen, welche Dateien, Ressourcen und Verweise dem neuen Projekt hinzugefügt werden sollen. Um diese Informationen bereitzustellen, legen Sie Projektdateien in einen Projektvorlagenordner. Wenn ein Benutzer das *.myproj-Projekt* verwendet, um ein Projekt zu erstellen, werden die Dateien in das neue Projekt kopiert.

### <a name="to-create-a-basic-project-template"></a>So erstellen Sie eine grundlegende Projektvorlage

1. Fügen Sie dem Projekt drei Ordner hinzu, einen unter dem anderen: *Templates-Projects-SimpleProject*. (Im **Projektmappen-Explorer**klicken Sie mit der rechten Maustaste auf den **Projektknoten SimpleProject,** zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neuer Ordner**. Benennen Sie den Ordner *Vorlagen*. Fügen Sie im Ordner *Vorlagen* einen Ordner mit dem Namen *Projects*hinzu. Fügen Sie im Ordner *Projekte* einen Ordner mit dem Namen *SimpleProject*hinzu.)

2. Fügen Sie im Ordner *"Vorlagen- und Projekt-SimpleProject"* eine Bitmap-Bilddatei hinzu, die als Symbol mit dem Namen *SimpleProject.ico*verwendet werden soll. Wenn Sie auf **Hinzufügen**klicken, wird der Symboleditor geöffnet.

3. Machen Sie das Symbol unverwechselbar. Dieses Symbol wird später in der exemplarischen Vorgehensweise im Dialogfeld **Neues Projekt** angezeigt.

    ![Symbol Einfaches Projekt](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Speichern Sie das Symbol, und schließen Sie den Symboleditor.

5. Fügen Sie im Ordner *"Vorlagen- und Projekt-SimpleProject"* ein **Klassenelement** mit dem Namen *Program.cs*hinzu.

6. Ersetzen Sie den vorhandenen Code durch die folgenden Zeilen.

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
   > Dies ist nicht die endgültige Form des *Program.cs* Code; die Ersatzparameter werden in einem späteren Schritt behandelt. Es können Kompilierungsfehler angezeigt werden, aber solange **BuildAction** der Datei **Inhalt**ist, sollten Sie in der Lage sein, das Projekt wie gewohnt zu erstellen und auszuführen.

7. Speichern Sie die Datei .

8. Kopieren Sie die *AssemblyInfo.cs-Datei* aus dem *Ordner Eigenschaften* in den Ordner *"Projekte" .SimpleProject.*

9. Fügen Sie im Ordner *"Projekte"* eine XML-Datei mit dem Namen *SimpleProject.myproj*hinzu.

   > [!NOTE]
   > Die Dateinamenerweiterung für alle Projekte dieses Typs ist *.myproj*. Wenn Sie es ändern möchten, müssen Sie es überall dort ändern, wo es in der exemplarischen Vorgehensweise erwähnt wird.

10. Ersetzen Sie den vorhandenen Inhalt durch die folgenden Zeilen.

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

11. Speichern Sie die Datei .

12. Legen Sie im Fenster **Eigenschaften** die **Buildaktion** *von AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico*und *SimpleProject.myproj* auf **Content**fest, und legen Sie ihre Include **in VSIX-Eigenschaften** auf **True**fest.

    Diese Projektvorlage beschreibt ein grundlegendes Visual C-Projekt, das sowohl über eine Debugkonfiguration als auch über eine Releasekonfiguration verfügt. Das Projekt enthält zwei Quelldateien, *AssemblyInfo.cs* und *Program.cs*sowie mehrere Assemblyverweise. Wenn ein Projekt aus der Vorlage erstellt wird, wird der ProjectGuid-Wert automatisch durch eine neue GUID ersetzt.

    Im **Projektmappen-Explorer**sollte der erweiterte **Vorlagenordner** wie folgt angezeigt werden:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Erstellen einer grundlegenden Projektfactory
 Sie müssen Visual Studio den Speicherort des Projektvorlagenordners mitteilen. Fügen Sie dazu der VSPackage-Klasse ein Attribut hinzu, das die Projektfactory implementiert, sodass der Vorlagenspeicherort beim Erstellen des VSPackage in die Systemregistrierung geschrieben wird. Erstellen Sie zunächst eine grundlegende Projektfactory, die durch eine Projektfactory-GUID identifiziert wird. Verwenden <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> Sie das Attribut, um `SimpleProjectPackage` die Projektfactory mit der Klasse zu verbinden.

### <a name="to-create-a-basic-project-factory"></a>So erstellen Sie eine grundlegende Projektfactory

1. Erstellen Sie GUIDs für Ihre Projektfactory (im Menü **Extras** auf **GUID erstellen),** oder verwenden Sie die im folgenden Beispiel. Fügen Sie die GUIDs der `SimpleProjectPackage` Klasse in `PackageGuidString`der Nähe des Abschnitts mit der bereits definierten hinzu. Die GUIDs müssen sowohl GUID- als auch Zeichenfolgenform sein. Der resultierende Code sollte dem folgenden Beispiel ähneln.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Fügen Sie dem obersten *SimpleProject-Ordner* mit dem Namen *SimpleProjectFactory.cs*eine Klasse hinzu.

3. Fügen Sie die folgenden using-Direktiven hinzu:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Fügen Sie der `SimpleProjectFactory` Klasse ein GUID-Attribut hinzu. Der Wert des Attributs ist die neue Projektfactory-GUID.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Jetzt können Sie Ihre Projektvorlage registrieren.

### <a name="to-register-the-project-template"></a>So registrieren Sie die Projektvorlage

1. Fügen *Sie*der <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> Klasse `SimpleProjectPackage` in SimpleProjectPackage.cs wie folgt ein Attribut hinzu.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass sie fehlerfrei erstellt wird.

    Beim Neuaufbau wird die Projektvorlage neu registriert.

   Die `defaultProjectExtension` Parameter `possibleProjectExtensions` und sind auf die Projektdateinamenerweiterung (*.myproj*) eingestellt. Der `projectTemplatesDirectory` Parameter wird auf den relativen Pfad des *Ordners Vorlagen* festgelegt. Während des Builds wird dieser Pfad in einen vollständigen Build konvertiert und der Registrierung hinzugefügt, um das Projektsystem zu registrieren.

## <a name="test-the-template-registration"></a>Testen der Vorlagenregistrierung
 Die Vorlagenregistrierung teilt Visual Studio den Speicherort Des Projektvorlagenordner mit, sodass Visual Studio den Vorlagennamen und das Symbol im Dialogfeld **Neues Projekt** anzeigen kann.

### <a name="to-test-the-template-registration"></a>So testen Sie die Vorlagenregistrierung

1. Drücken Sie **F5,** um mit dem Debuggen einer experimentellen Instanz von Visual Studio zu beginnen.

2. Erstellen Sie in der experimentellen Instanz ein neues Projekt Ihres neu erstellten Projekttyps. Im Dialogfeld **Neues Projekt** sollte **SimpleProject** unter **Installierte Vorlagen**angezeigt werden.

   Jetzt haben Sie eine Projektfabrik, die registriert ist. Es kann jedoch noch kein Projekt erstellen. Das Projektpaket und die Projektfactory arbeiten zusammen, um ein Projekt zu erstellen und zu initialisieren.

## <a name="add-the-managed-package-framework-code"></a>Hinzufügen des Managed Package Framework-Codes
 Implementieren Sie die Verbindung zwischen dem Projektpaket und der Projektfactory.

- Importieren Sie die Quellcodedateien für das Managed Package Framework.

    1. Entladen Sie das SimpleProject-Projekt (im **Projektmappen-Explorer**den Projektknoten auswählen und klicken Sie im Kontextmenü auf **Projekt entladen**.) und öffnen Sie die Projektdatei im XML-Editor.

    2. Fügen Sie der Projektdatei die folgenden \<Blöcke hinzu (direkt über dem Import->-Blöcken). Legen `ProjectBasePath` Sie den Speicherort der *ProjectBase.files-Datei* im Managed Package Framework-Code fest, den Sie gerade heruntergeladen haben. Möglicherweise müssen Sie dem Pfadnamen einen umgekehrten Schrägstrich hinzufügen. Andernfalls kann das Projekt möglicherweise den Quellcode des Managed Package Framework nicht finden.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Vergessen Sie nicht den umgekehrten Schrägstrich am Ende des Pfads.

    3. Laden Sie das Projekt neu.

    4. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

        - `Microsoft.VisualStudio.Designer.Interfaces`(in * \<VSSDK installieren>-VisualStudioIntegration-Common-Assemblys, V2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>So initialisieren Sie die Projektfactory

1. Fügen Sie in der `using` Datei *SimpleProjectPackage.cs* die folgende Direktive hinzu.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Leiten Sie `SimpleProjectPackage` die `Microsoft.VisualStudio.Package.ProjectPackage`Klasse von ab.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Registrieren Sie die Projektfactory. Fügen Sie der `SimpleProjectPackage.Initialize` Methode kurz `base.Initialize`nach die folgende Zeile hinzu.

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implementieren Sie `ProductUserContext`die abstrakte Eigenschaft :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. Fügen *Sie in* `using` SimpleProjectFactory.cs die `using` folgende Richtlinie nach den bestehenden Richtlinien hinzu.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Leiten Sie `SimpleProjectFactory` die `ProjectFactory`Klasse von ab.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Fügen Sie der `SimpleProjectFactory` Klasse die folgende Dummy-Methode hinzu. Sie implementieren diese Methode in einem späteren Abschnitt.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Fügen Sie der Klasse das `SimpleProjectFactory` folgende Feld und den folgenden Konstruktor hinzu. Dieser `SimpleProjectPackage` Verweis wird in einem privaten Feld zwischengespeichert, sodass er zum Festlegen einer Dienstanbietersite verwendet werden kann.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass sie fehlerfrei erstellt wird.

## <a name="test-the-project-factory-implementation"></a>Testen der Projektfactoryimplementierung
 Testen Sie, ob der Konstruktor für die Projektfactoryimplementierung aufgerufen wird.

### <a name="to-test-the-project-factory-implementation"></a>So testen Sie die Projektfactoryimplementierung

1. Legen Sie in der *SimpleProjectFactory.cs* Datei einen Haltepunkt in der folgenden Zeile im `SimpleProjectFactory` Konstruktor fest.

    ```csharp
    this.package = package;
    ```

2. Drücken Sie **F5,** um eine experimentelle Instanz von Visual Studio zu starten.

3. Beginnen Sie in der experimentellen Instanz mit der Erstellung eines neuen Projekts. Wählen Sie im Dialogfeld **Neues Projekt** den **Projekttyp SimpleProject** aus, und klicken Sie dann auf **OK**. Die Ausführung hält am Haltepunkt an.

4. Löschen Sie den Haltepunkt, und beenden Sie das Debuggen. Da wir noch keinen Projektknoten erstellt haben, werden im Projekterstellungscode weiterhin Ausnahmen ausgelöst.

## <a name="extend-the-projectnode-class"></a>Erweitern der ProjectNode-Klasse
 Jetzt können Sie `SimpleProjectNode` die Klasse implementieren, `ProjectNode` die von der Klasse abstammt. Die `ProjectNode` Basisklasse übernimmt die folgenden Aufgaben der Projekterstellung:

- Kopiert die Projektvorlagendatei *SimpleProject.myproj*in den neuen Projektordner. Die Kopie wird entsprechend dem Namen umbenannt, der im Dialogfeld **Neues Projekt** eingegeben wird. Der `ProjectGuid` Eigenschaftswert wird durch eine neue GUID ersetzt.

- Durchläuft die MSBuild-Elemente der Projektvorlagendatei *SimpleProject.myproj*und sucht `Compile` nach Elementen. Kopiert `Compile` die Datei für jede Zieldatei in den neuen Projektordner.

  Die `SimpleProjectNode` abgeleitete Klasse verarbeitet die folgenden Aufgaben:

- Ermöglicht das Erstellen oder Auswählen von Symbolen für Projekt- und Dateiknoten im **Projektmappen-Explorer.**

- Ermöglicht die Angabe zusätzlicher Projektvorlagenparameterersetzungen.

### <a name="to-extend-the-projectnode-class"></a>So erweitern Sie die ProjectNode-Klasse

1. Fügen Sie eine Klasse namens `SimpleProjectNode.cs`hinzu.

2. Ersetzen Sie den vorhandenen Code durch folgenden Code:

   ```csharp
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

   Diese `SimpleProjectNode` Klassenimplementierung verfügt über die folgenden überschriebenen Methoden:

- `ProjectGuid`, die die Projektfactory-GUID zurückgibt.

- `ProjectType`, die den lokalisierten Namen des Projekttyps zurückgibt.

- `AddFileFromTemplate`, die ausgewählte Dateien aus dem Vorlagenordner in das Zielprojekt kopiert. Diese Methode wird in einem späteren Abschnitt weiter implementiert.

  Der `SimpleProjectNode` Konstruktor speichert `SimpleProjectFactory` wie der Konstruktor einen `SimpleProjectPackage` Verweis in einem privaten Feld für die spätere Verwendung zwischen.

  Um die `SimpleProjectFactory` Klasse `SimpleProjectNode` mit der Klasse zu verbinden, `SimpleProjectNode` müssen `SimpleProjectFactory.CreateProject` Sie eine neue Methode instanziieren und sie zur späteren Verwendung in einem privaten Feld zwischenspeichern.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>So verbinden Sie die Projektfactoryklasse mit der Knotenklasse

1. Fügen Sie in der `using` Datei *SimpleProjectFactory.cs* die folgende Direktive hinzu:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Ersetzen `SimpleProjectFactory.CreateProject` Sie die Methode durch den folgenden Code.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Erstellen Sie die Projektmappe neu, und stellen Sie sicher, dass sie fehlerfrei erstellt wird.

## <a name="test-the-projectnode-class"></a>Testen der ProjectNode-Klasse
 Testen Sie die Projektfactory, um festzustellen, ob eine Projekthierarchie erstellt wird.

### <a name="to-test-the-projectnode-class"></a>So testen Sie die ProjectNode-Klasse

1. Drücken Sie **F5**, um das Debuggen zu starten. Erstellen Sie in der experimentellen Instanz ein neues SimpleProject.

2. Visual Studio sollte Ihre Projektfactory aufrufen, um ein Projekt zu erstellen.

3. Schließen Sie die experimentelle Instanz von Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Hinzufügen eines benutzerdefinierten Projektknotensymbols
 Das Projektknotensymbol im vorherigen Abschnitt ist ein Standardsymbol. Sie können es in ein benutzerdefiniertes Symbol ändern.

### <a name="to-add-a-custom-project-node-icon"></a>So fügen Sie ein benutzerdefiniertes Projektknotensymbol hinzu

1. Fügen Sie im Ordner **Ressourcen** eine Bitmapdatei mit dem Namen *SimpleProjectNode.bmp*hinzu.

2. Reduzieren Sie in den **Eigenschaftenfenstern** die Bitmap auf 16 x 16 Pixel. Machen Sie die Bitmap unverwechselbar.

    ![Einfaches Projekt - Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. Ändern Sie im **Fenster Eigenschaften** die **Buildaktion** der Bitmap in **Eingebettete Ressource**.

4. Fügen *SimpleProjectNode.cs*Sie in `using` SimpleProjectNode.cs die folgenden Direktiven hinzu:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Fügen Sie der Klasse das `SimpleProjectNode` folgende statische Feld und den folgenden Konstruktor hinzu.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Fügen Sie die folgende Eigenschaft `SimpleProjectNode` am Anfang der Klasse hinzu.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Ersetzen Sie den Instanzkonstruktor durch den folgenden Code.

   ```csharp
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

   Ruft während `SimpleProjectNode` der statischen Konstruktion die Projektknoten-Bitmap aus den Assemblymanifestressourcen ab und speichert sie zur späteren Verwendung in einem privaten Feld zwischen. Beachten Sie die <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> Syntax des Bildpfads. Verwenden Sie die <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> Methode, um die Namen der in eine Assembly eingebetteten Manifestressourcen anzuzeigen. Wenn diese Methode auf `SimpleProject` die Baugruppe angewendet wird, sollten die Ergebnisse wie folgt lauten:

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Ressourcen.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Während der Instance-Erstellung lädt die `ProjectNode` Basisklasse *Resources.imagelis.bmp*, in die häufig 16 x 16 Bitmaps aus *Resources-imagelis.bmp*eingebettet werden. Diese Bitmapliste wird `SimpleProjectNode` als `ImageHandler.ImageList`zur Verfügung gestellt. `SimpleProjectNode`fügt die Projektknoten-Bitmap an die Liste an. Der Offset der Projektknoten-Bitmap in der Bildliste wird zur späteren `ImageIndex` Verwendung als Wert der öffentlichen Eigenschaft zwischengespeichert. Visual Studio verwendet diese Eigenschaft, um zu bestimmen, welche Bitmap als Projektknotensymbol angezeigt werden soll.

## <a name="test-the-custom-project-node-icon"></a>Testen des benutzerdefinierten Projektknotensymbols
 Testen Sie die Projektfactory, um festzustellen, ob eine Projekthierarchie mit dem benutzerdefinierten Projektknotensymbol erstellt wird.

### <a name="to-test-the-custom-project-node-icon"></a>So testen Sie das benutzerdefinierte Projektknotensymbol

1. Starten Sie das Debuggen, und erstellen Sie in der experimentellen Instanz ein neues SimpleProject.

2. Beachten Sie im neu erstellten Projekt, dass *SimpleProjectNode.bmp* als Projektknotensymbol verwendet wird.

     ![Einfaches Projekt - Knoten Neues Projekt](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Öffnen Sie *Program.cs* im Code-Editor. Es sollte Quellcode angezeigt werden, der dem folgenden Code ähnelt.

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

     Beachten Sie, dass die Vorlagenparameter $nameSpace und $className keine neuen Werte haben. Im nächsten Abschnitt erfahren Sie, wie Sie die Ersetzung von Vorlagenparametern implementieren.

## <a name="substitute-template-parameters"></a>Ersetzen von Vorlagenparametern
 In einem früheren Abschnitt haben Sie die Projektvorlage `ProvideProjectFactory` mithilfe des Attributs bei Visual Studio registriert. Wenn Sie den Pfad eines Vorlagenordners auf diese Weise registrieren, können `ProjectNode.AddFileFromTemplate` Sie die Ersetzung grundlegender Vorlagenparameter aktivieren, indem Sie die Klasse überschreiben und erweitern. Weitere Informationen finden Sie unter [Neue Projektgeneration: Unter der Haube, Teil 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Fügen Sie nun `AddFileFromTemplate` Ersatzcode zur Klasse hinzu.

### <a name="to-substitute-template-parameters"></a>So ersetzen Sie Vorlagenparameter

1. Fügen Sie in der `using` Datei *SimpleProjectNode.cs* die folgende Direktive hinzu.

   ```csharp
   using System.IO;
   ```

2. Ersetzen `AddFileFromTemplate` Sie die Methode durch den folgenden Code.

   ```csharp
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

3. Legen Sie einen Haltepunkt in `className` der Methode fest, direkt nach der Zuweisungsanweisung.

   Die Zuweisungsanweisungen bestimmen angemessene Werte für einen Namespace und einen neuen Klassennamen. Die `ProjectNode.FileTemplateProcessor.AddReplace` beiden Methodenaufrufe ersetzen die entsprechenden Vorlagenparameterwerte durch die Verwendung dieser neuen Werte.

## <a name="test-the-template-parameter-substitution"></a>Testen der Vorlagenparameterersetzung
 Jetzt können Sie die Ersetzung von Vorlagenparametern testen.

### <a name="to-test-the-template-parameter-substitution"></a>So testen Sie die Vorlagenparameterersetzung

1. Starten Sie das Debuggen, und erstellen Sie in der experimentellen Instanz ein neues SimpleProject.

2. Die Ausführung wird am `AddFileFromTemplate` Haltepunkt in der Methode beendet.

3. Untersuchen Sie die `nameSpace` `className` Werte für die und Parameter.

   - `nameSpace`wird der Wert \<des RootNamespace->-Elements in der Projektvorlagendatei *"Templates" angegeben.* In diesem Fall handelt es sich um den Wert `MyRootNamespace`.

   - `className`wird der Wert des Klassenquelldateinamens ohne die Dateinamenerweiterung angegeben. In diesem Fall wird die erste Datei, die in den Zielordner kopiert werden soll, *AssemblyInfo.cs*; Daher ist `AssemblyInfo`der Wert von className .

4. Entfernen Sie den Haltepunkt, und drücken Sie **F5,** um die Ausführung fortzusetzen.

    Visual Studio sollte die Erstellung eines Projekts beenden.

5. Öffnen Sie *Program.cs* im Code-Editor. Es sollte Quellcode angezeigt werden, der dem folgenden Code ähnelt.

   ```csharp
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

    Beachten Sie, dass `MyRootNamespace` der Namespace jetzt `Program`ist und der Klassenname jetzt ist.

6. Beginnen Sie mit dem Debuggen des Projekts. Das neue Projekt sollte "Hello VSX!!!" kompilieren, ausführen und anzeigen. im Konsolenfenster anzuzeigen.

    ![Befehl Einfaches Projekt](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Herzlichen Glückwunsch! Sie haben ein grundlegendes verwaltetes Projektsystem implementiert.
