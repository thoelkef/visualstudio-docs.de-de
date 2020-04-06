---
title: Erstellen eines Software Development Kits | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739590"
---
# <a name="create-a-software-development-kit"></a>Erstellen eines Software-Entwicklungskits

Ein Software Development Kit (SDK) ist eine Sammlung von APIs, auf die Sie als einzelnes Element in Visual Studio verweisen können. Im Dialogfeld **Referenz-Manager** werden alle SDKs aufgelistet, die für das Projekt relevant sind. Wenn Sie einem Projekt ein SDK hinzufügen, sind die APIs in Visual Studio verfügbar.

Es gibt zwei Arten von SDKs:

- Plattform-SDKs sind obligatorische Komponenten für die Entwicklung von Apps für eine Plattform. Beispielsweise ist [!INCLUDE[win81](../debugger/includes/win81_md.md)] das SDK erforderlich, um Apps zu entwickeln. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]

- Erweiterungs-SDKs sind optionale Komponenten, die eine Plattform erweitern, aber nicht für die Entwicklung von Apps für diese Plattform obligatorisch sind.

In den folgenden Abschnitten wird die allgemeine Infrastruktur von SDKs beschrieben und beschrieben, wie ein Plattform-SDK und ein Erweiterungs-SDK erstellt werden.

## <a name="platform-sdks"></a>Plattform-SDKs

Plattform-SDKs sind erforderlich, um Apps für eine Plattform zu entwickeln. Das [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK ist z. B. [!INCLUDE[win81](../debugger/includes/win81_md.md)]erforderlich, um Apps für zu entwickeln.

### <a name="installation"></a>Installation

Alle Plattform-SDKs werden bei *HKLM-Software-Microsoft-Microsoft-SDKs\\[TPI]-v[TPV]\\ @InstallationFolder = [SDK-Stamm]* installiert. Dementsprechend [!INCLUDE[win81](../debugger/includes/win81_md.md)] wird das SDK unter *HKLM-Software-Microsoft-Microsoft-SDKs-Windows-V8.1*installiert.

### <a name="layout"></a>Layout

Plattform-SDKs haben das folgende Layout:

```
\[InstallationFolder root]
            SDKManifest.xml
            \References
                  \[config]
                        \[arch]
            \DesignTime
                  \[config]
                        \[arch]
```

| Node | BESCHREIBUNG |
|------------------------| - |
| *Referenzordner* | Enthält Binärdateien, die APIs enthalten, für die codiert werden kann. Dazu können Windows-Metadatendateien (WinMD) oder Assemblys gehören. |
| *DesignTime-Ordner* | Enthält Dateien, die nur zur Vorlaufzeit/Debugging-Zeit benötigt werden. Dazu können XML-Dokumente, Bibliotheken, Header, Toolbox-Entwurfs-Zeit-Binärdateien, MSBuild-Artefakte usw. gehören.<br /><br /> XML-Dokumente würden idealerweise im Ordner *"DesignTime"* abgelegt, aber XML-Dokumente für Verweise werden weiterhin neben der Referenzdatei in Visual Studio platziert. Das XML-Dokument für einen Verweis ist z. B. der Verweis<em>\\,,References [config]\\[arch]', "sample.dll"</em> *ist .References\\[config]\\[arch]'sample.xml*, und die lokalisierte Version dieses Dokuments ist *'References\\[config]\\[arch] [locale]'sample.xml\\*. |
| *Konfigurationsordner* | Es können nur drei Ordner vorhanden sein: *Debug ,* *Retail* und *CommonConfiguration*. SDK-Autoren können ihre Dateien unter *CommonConfiguration* platzieren, wenn derselbe Satz von SDK-Dateien verwendet werden soll, unabhängig von der Konfiguration, auf die der SDK-Consumer ausgerichtet ist. |
| *Architekturordner* | Jeder unterstützte *Architekturordner* kann vorhanden sein. Visual Studio unterstützt die folgenden Architekturen: x86, x64, ARM und neutral. Hinweis: Win32-Zuordnungen zu x86 und AnyCPU-Zuordnungen zu neutral.<br /><br /> MSBuild sieht nur unter *"CommonConfiguration"-neutral* für Plattform-SDKs aus. |
| *SDKManifest.xml* | Diese Datei beschreibt, wie Visual Studio das SDK verwenden soll. Das SDK-Manifest [!INCLUDE[win81](../debugger/includes/win81_md.md)]finden Sie im SDK-Manifest für:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Der Wert, den der Objektbrowser in der Liste Durchsuchen anzeigt.<br /><br /> **PlatformIdentity:** Das Vorhandensein dieses Attributs teilt Visual Studio und MSBuild mit, dass das SDK ein Plattform-SDK ist und dass die daraus hinzugefügten Verweise nicht lokal kopiert werden sollten.<br /><br /> **TargetFramework:** Dieses Attribut wird von Visual Studio verwendet, um sicherzustellen, dass nur Projekte, die auf dieselben Frameworks abzielen, wie im Wert dieses Attributs angegeben, das SDK verwenden können.<br /><br /> **MinVSVersion:** Dieses Attribut wird von Visual Studio verwendet, um nur die SDKs zu verwenden, die auf visual verwendet werden.<br /><br /> **Referenz:** Dieses Attribut muss nur für die Verweise angegeben werden, die Steuerelemente enthalten. Informationen zum Angeben, ob ein Verweis Steuerelemente enthält, finden Sie weiter unten. |

## <a name="extension-sdks"></a>Erweiterungs-SDKs

In den folgenden Abschnitten wird beschrieben, was Sie tun müssen, um ein Erweiterungs-SDK bereitzustellen.

### <a name="installation"></a>Installation

Erweiterungs-SDKs können für einen bestimmten Benutzer oder für alle Benutzer installiert werden, ohne einen Registrierungsschlüssel anzugeben. Um ein SDK für alle Benutzer zu installieren, verwenden Sie den folgenden Pfad:

*%Program Files%-Microsoft SDKs-Zielplattform\<\>,\><-Versionsnummer der Plattform*

Verwenden Sie für eine benutzerspezifische Installation den folgenden Pfad:

*%USERPROFILE%-AppData-Local-Microsoft-SDKs-Zielplattform\<\>,<-Versionsnummer\>der Plattform.*

Wenn Sie einen anderen Speicherort verwenden möchten, müssen Sie eines von zwei Dingen tun:

1. Geben Sie sie in einem Registrierungsschlüssel an:

     **HKLM-Software-Microsoft-SDKs-Zielplattform\<>-v-<-Plattform-Versionsnummer\>\<"ExtensionSDKs SDKName>\<SDKVersion>**\

     und fügen Sie einen Unterschlüssel (Standard) mit dem Wert `<path to SDK><SDKName><SDKVersion>`von hinzu.

2. Fügen Sie der `SDKReferenceDirectoryRoot` Projektdatei die MSBuild-Eigenschaft hinzu. Der Wert dieser Eigenschaft ist eine durch Semikolons getrennte Liste von Verzeichnissen, in denen sich die Erweiterungs-SDKs befinden, auf die Sie verweisen möchten.

### <a name="installation-layout"></a>Installationslayout

Erweiterungs-SDKs verfügen über das folgende Installationslayout:

```
\<ExtensionSDKs root>
           \<SDKName>
                 \<SDKVersion>
                        SDKManifest.xml
                        \References
                              \<config>
                                    \<arch>
                        \Redist
                              \<config>
                                    \<arch>
                        \DesignTime
                               \<config>
                                     \<arch>

```

1. \\<SDKName\> \\<\>SDKVersion : Der Name und die Version des Erweiterungs-SDK werden von den entsprechenden Ordnernamen im Pfad zum SDK-Stamm abgeleitet. MSBuild verwendet diese Identität, um das SDK auf dem Datenträger zu finden, und Visual Studio zeigt diese Identität im **Eigenschaftenfenster** und im **Dialogfeld Referenz-Manager** an.

2. *Referenzordner:* die Binärdateien, die die APIs enthalten. Dabei kann es sich um Windows-Metadatendateien (WinMD)-Dateien oder Assemblys erachten.

3. *Redist-Ordner:* Die Dateien, die für die Laufzeit/das Debuggen benötigt werden und als Teil der Anwendung des Benutzers verpackt werden sollen. Alle Binärdateien sollten unter\<dem *]* *\\<\> \\ \>-<-Konfiguration platziert*werden,<und die Binärnamen sollten das folgende Format haben, um die Eindeutigkeit sicherzustellen: ]>. \<Produkt>. \<Zweck>. \<Erweiterung><em>. Beispiel: *Microsoft.Cpp.Build.dll</em>. Alle Dateien mit Namen, die mit Dateinamen anderer SDKs kollidieren können (z. B. Javascript-, css-, pri-, xaml-, png- und jpg-Dateien), sollten unter dem <em>\\<---Bogen mit Ausnahme der Dateien, die XAML-Steuerelementen zugeordnet sind, unter dem<\> \\<<--Bogen\> \\ sdkname\> \* platziert werden. Diese Dateien sollten unter *-redist\\ \> \\<-Konfiguration\> \\<\>Bogen<Komponentenname platziert werden.</em>

4. *DesignTime-Ordner:* Die Dateien, die nur zur Vorlaufzeit/Debugging-Zeit benötigt werden und nicht als Teil der Anwendung des Benutzers gepackt werden sollten. Dabei kann es sich um XML-Dokumente, Bibliotheken, Header, Toolbox-Entwurfs-Zeit-Binärdateien, MSBuild-Artefakte usw. handeln. Jedes SDK, das für die Verwendung durch ein systemisches Projekt vorgesehen ist, muss über eine *SDKName.props-Datei* verfügen. Im Folgenden wird ein Beispiel für diesen Dateityp gezeigt.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>
       <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>
       <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>
       <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>
       <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>
       <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>
       <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>
     </PropertyGroup>
   </Project>

   ```

    XML-Referenzdokumente werden neben der Referenzdatei platziert. Das XML-Referenzdokument für die Assembly *"Referenzen\\<konfiguration\> \\<"arch"-Assembly\>* ist z. B. *"Referenzen\\<-referenzieren\> \\<-beispiel.xml\>*, und die lokalisierte Version dieses Dokuments ist *"References\\<config\> \\<arch\> \\<locale\>" .xml*" .

5. *Konfigurationsordner:* drei Unterordner: *Debuggen*, *Einzelhandel*und *CommonConfiguration*. SDK-Autoren können ihre Dateien unter *CommonConfiguration* platzieren, wenn derselbe Satz von SDK-Dateien verwendet werden soll, unabhängig von der Konfiguration, auf die der SDK-Consumer abzielt.

6. *Architekturordner:* Die folgenden Architekturen werden unterstützt: x86, x64, ARM, neutral. Win32-Zuordnungen zu x86 und AnyCPU-Zuordnungen zu neutral.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

Die Datei *SDKManifest.xml* beschreibt, wie Visual Studio das SDK verwenden soll. Es folgt ein Beispiel:

```
<FileList>
DisplayName = "My SDK"
ProductFamilyName = "My SDKs"
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"
MinVSVersion = "14.0"
MaxPlatformVersion = "8.1"
AppliesTo = "WindowsAppContainer + WindowsXAML"
SupportPrefer32Bit = "True"
SupportedArchitectures = "x86;x64;ARM"
SupportsMultipleVersions = "Error"
CopyRedistToSubDirectory = "."
DependsOn = "SDKB, version=2.0"
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

Die folgende Liste enthält die Elemente der Datei:

1. DisplayName: der Wert, der im Referenz-Manager, im Projektmappen-Explorer, im Objektbrowser und an anderen Speicherorten in der Benutzeroberfläche für Visual Studio angezeigt wird.

2. ProductFamilyName: Der allgemeine SDK-Produktname. Das [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK heißt beispielsweise "Microsoft.WinJS.1.0" und "Microsoft.WinJS.2.0", die zur gleichen SDK-Produktfamilie gehören, "Microsoft.WinJS". Mit diesem Attribut können Visual Studio und MSBuild diese Verbindung herstellen. Wenn dieses Attribut nicht vorhanden ist, wird der SDK-Name als Produktfamilienname verwendet.

3. FrameworkIdentity: Gibt eine Abhängigkeit von einer oder mehreren Windows-Komponentenbibliotheken an. Der Wert dieses Attributs wird in das Manifest der verbrauchenden App eingefügt. Dieses Attribut gilt nur für Windows-Komponentenbibliotheken.

4. TargetFramework: Gibt die SDKs an, die im Referenz-Manager und in der Toolbox verfügbar sind. Dies ist eine durch Semikolons getrennte Liste von Zielframeworkmonikern, z. B. ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1". Wenn mehrere Versionen desselben Zielframeworks angegeben werden, verwendet der Referenz-Manager die niedrigste angegebene Version für Filterzwecke. Wenn beispielsweise ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1" angegeben ist, verwendet Reference Manager ".NET Framework, version=v2.0". Wenn ein bestimmtes Zielframeworkprofil angegeben ist, wird nur dieses Profil vom Referenz-Manager zu Filterzwecken verwendet. Wenn z. B. "Silverlight, version=v4.0, profile=WindowsPhone" angegeben wird, filtert der Referenz-Manager nur das Windows Phone-Profil. Ein Projekt, das auf das vollständige Silverlight 4.0 Framework abzielt, sieht das SDK nicht im Referenz-Manager.

5. MinVSVersion: Die minimale Visual Studio-Version.

6. MaxPlatformVerson: Die maximale Zielplattformversion sollte verwendet werden, um die Plattformversionen anzugeben, auf denen Ihr Extension SDK nicht funktioniert. Beispielsweise sollte auf das Microsoft Visual C++ Runtime Package v11.0 nur von Windows 8-Projekten verwiesen werden. Somit ist die MaxPlatformVersion des Windows 8-Projekts 8.0. Dies bedeutet, dass der Referenz-Manager Microsoft Visual C++ Runtime Package für ein Windows [!INCLUDE[win81](../debugger/includes/win81_md.md)] 8.1-Projekt herausfiltert und MSBuild einen Fehler auslöst, wenn ein Projekt darauf verweist. Hinweis: Dieses Element wird [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]ab .

7. Gilt: Gibt die SDKs an, die im Referenz-Manager verfügbar sind, indem die entsprechenden Visual Studio-Projekttypen angegeben werden. Neun Werte werden erkannt: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed und Native. Der SDK-Autor kann verwenden und ("+') oder ("&#124;"), nicht ("!") , um den Genauen des Bereichs der Projekttypen anzugeben, die für das SDK gelten.

    WindowsAppContainer identifiziert [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Projekte für Apps.

8. SupportPrefer32Bit: Unterstützte Werte sind "True" und "False". Der Standardwert ist "True". Wenn der Wert auf "False" festgelegt ist, gibt MSBuild einen Fehler für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Projekte (oder eine Warnung für Desktopprojekte) zurück, wenn das Projekt, das auf das SDK verweist, Prefer32Bit aktiviert hat. Weitere Informationen zu Prefer32Bit finden Sie unter [Buildseite, Projekt-Designer (C-Seite)](../ide/reference/build-page-project-designer-csharp.md) oder [Kompilierungsseite, Projekt-Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. SupportedArchitectures: Eine durch Semikolons getrennte Liste von Architekturen, die vom SDK unterstützt werden. MSBuild zeigt eine Warnung an, wenn die zielgerichtete SDK-Architektur im verbrauchenden Projekt nicht unterstützt wird. Wenn dieses Attribut nicht angegeben ist, zeigt MSBuild diese Art von Warnung nie an.

10. UnterstütztMehrereVersionen: Wenn dieses Attribut auf **Fehler** oder **Warnung**festgelegt ist, gibt MSBuild an, dass dasselbe Projekt nicht auf mehrere Versionen derselben SDK-Familie verweisen kann. Wenn dieses Attribut nicht vorhanden ist oder auf **Zulassen**festgelegt ist, zeigt MSBuild diesen Fehler typoder diese Warnung nicht an.

11. AppX: Gibt den Pfad zu den App-Paketen für die Windows-Komponentenbibliothek auf dem Datenträger an. Dieser Wert wird während des lokalen Debuggens an die Registrierungskomponente der Windows-Komponentenbibliothek übergeben. Die Namenskonvention für den Dateinamen lautet * \<Company>.\< Produkt>. \<Architektur>. \<Konfiguration>. Version \<>.appx*. Konfiguration und Architektur sind im Attributnamen und im Attributwert optional, wenn sie nicht auf die Windows-Komponentenbibliothek angewendet werden. Dieser Wert gilt nur für Windows-Komponentenbibliotheken.

12. CopyRedistToSubDirectory: Gibt an, wo die Dateien unter dem Ordner *"redist"* relativ zum App-Paketstamm (d. h. **dem** im Assistenten zum Erstellen **von App-Paket** enk.) und Laufzeitlayoutstamm kopiert werden sollen. Der Standardspeicherort ist der Stamm **F5** des App-Pakets und des F5-Layouts.

13. DependsOn: Eine Liste von SDK-Identitäten, die die SDKs definieren, von denen dieses SDK abhängt. Dieses Attribut wird im Detailbereich des Referenz-Managers angezeigt.

14. MoreInfo: Die URL zur Webseite, die Hilfe und weitere Informationen bereitstellt. Dieser Wert wird im Link Weitere Informationen im rechten Bereich des Referenz-Managers verwendet.

15. Registrierungstyp: Gibt die WinMD-Registrierung im App-Manifest an und ist für native WinMD erforderlich, die über eine gegensäne Implementierungs-DLL verfügt.

16. Dateireferenz: Angegeben nur für Verweise, die Steuerelemente enthalten oder systemeigene WinMDs sind. Informationen zum Angeben, ob ein Verweis Steuerelemente enthält, finden Sie unter [Angeben des Speicherorts von Toolboxelementen](#ToolboxItems) unten.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Angeben des Speicherorts von Toolboxelementen

Das **ToolBoxItems-Element** des *SDKManifest.xml-Schemas* gibt die Kategorie und den Speicherort von Toolboxelementen in Plattform- und Erweiterungs-SDKs an. Die folgenden Beispiele zeigen, wie Sie verschiedene Speicherorte angeben. Dies gilt entweder für WinMD- oder DLL-Referenzen.

1. Platzieren Sie Steuerelemente in der Standardkategorie der Toolbox.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Platzieren Sie Steuerelemente unter einem bestimmten Kategorienamen.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Platzieren Sie Steuerelemente unter bestimmten Kategorienamen.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Platzieren Sie Steuerelemente unter verschiedenen Kategorienamen in Blend und Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Aufzählen bestimmter Steuerelemente in Blend und Visual Studio unterschiedlich.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Aufzählen bestimmter Steuerelemente, und platzieren Sie sie unter dem allgemeinen Visual Studio-Pfad oder nur in der Gruppe Alle Steuerelemente.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Auflisten bestimmter Steuerelemente, und zeigen Sie nur einen bestimmten Satz in ChooseItems an, ohne dass sie sich in der Toolbox befinden.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Weitere Informationen

- [Exemplarische Vorgehensweise: Erstellen eines SDK mit C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Exemplarische Vorgehensweise: Erstellen eines SDK mit C- oder Visual Basic-Code](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)
