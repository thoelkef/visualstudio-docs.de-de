---
title: Erstellen eines Software Development Kits | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc04de6de270053e20e05a30312a298e9e6e2f0f
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177345"
---
# <a name="create-a-software-development-kit"></a>Erstellen eines Software Development Kits
Ein Software Development Kit (SDK) ist eine Sammlung von APIs, die Sie als ein einzelnes Element in Visual Studio verweisen können. Die **Verweis-Manager** Dialogfeld listet alle SDKs, die für das Projekt relevant sind. Wenn Sie ein Projekt eine SDK hinzufügen, sind die APIs in Visual Studio verfügbar.

 Es gibt zwei Arten von SDKs:

- Plattform-SDKs handelt es sich um erforderliche Komponenten für die Entwicklung von apps für eine Plattform. Z. B. die [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK ist erforderlich, um die Entwicklung [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] apps.

- Erweiterungs-SDKs sind optionale Komponenten, die eine Plattform zu erweitern, aber nicht obligatorisch für die Entwicklung von apps für die betreffende Plattform.

  Die folgenden Abschnitte beschreiben die allgemeine Infrastruktur von SDKs und erstellen Sie eine Plattform-SDK und einer Erweiterungs-SDK.

- [Plattform-SDKs](#PlatformSDKs)

- [Erweiterungs-SDKs](#ExtensionSDKs)

## <a name="PlatformSDKs"></a> Plattform-SDKs
 Plattform-SDKs sind erforderlich, um apps für eine Plattform zu entwickeln. Z. B. die [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK ist erforderlich, um das Entwickeln von apps für [!INCLUDE[win81](../debugger/includes/win81_md.md)].

### <a name="installation"></a>Installation
 Auf alle Plattform-SDKs installiert werden *HKLM\Software\Microsoft\Microsoft SDKs\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK-Stamm]* . Entsprechend der [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK installiert ist, auf *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*.

### <a name="layout"></a>Layout
 Plattform-SDKs wurde das folgende Layout:

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

| Knoten | Beschreibung |
|------------------------| - |
| *Verweise* Ordner | Enthält die Binärdateien, die APIs enthalten, die für codiert werden können. Diese können es sich um Windows-Metadatendateien (WinMD) oder Assemblys enthalten. |
| *DesignTime* Ordner | Enthält Dateien, die nur zum Zeitpunkt der pre-ausführen/Debuggen erforderlich sind. Diese können XML-Dokumente, Bibliotheken, Header, Toolbox während der Entwurfszeit-Binärdateien, MSBuild-Elementen usw. enthalten.<br /><br /> XML-Dokumente würde, im Idealfall platziert werden, der *\DesignTime* Ordner, sondern XML-Dokumente nach verweisen weiterhin zusammen mit der Referenzdatei in Visual Studio platziert werden. Z. B. das XML-Dokument für einen Verweis<em>\References\\[Config]\\[arch]\sample.dll</em> werden *\References\\[Config]\\[arch]\sample.xml*, die lokalisierte Version von diesem Dokument werden *\References\\[Config]\\[Arch]\\[locale]\sample.xml*. |
| *Konfiguration* Ordner | Dafür kann es nur drei Ordnern: *Debuggen von*, *Retail* und *CommonConfiguration*. SDK-Autoren können ihre Dateien unterhalb platzieren *CommonConfiguration* Wenn der gleiche Satz von SDK-Dateien, unabhängig von der Konfiguration genutzt werden sollen, die SDK-Consumers ausgerichtet wird. |
| *Architektur* Ordner | Ein unterstütztes *Architektur* Ordner kann vorhanden sein. Visual Studio unterstützt die folgenden Architekturen: X86, X64, ARM "und" Neutral. Hinweis: Win32 X86 zugeordnet, und "anycpu" neutrale zugeordnet.<br /><br /> MSBuild sucht nur unter *\CommonConfiguration\neutral* für die Plattform-SDKs. |
| *SDKManifest.xml* | Diese Datei beschreibt, wie das SDK von Visual Studio reserviert werden soll. Betrachten Sie das SDK-Manifest für [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Der Wert, den die Objekt-Browser in der Suchliste angezeigt.<br /><br /> **PlatformIdentity:** Das Vorhandensein dieses Attribut teilt Visual Studio und MSBuild, die das SDK ist ein Plattform-SDK und die Verweise hinzugefügt, daraus dürfen nicht kopiert werden, lokal.<br /><br /> **TargetFramework:** Dieses Attribut wird von Visual Studio verwendet, um sicherzustellen, die nur Projekte, die auf die gleichen Frameworks gemäß dem Wert dieses Attributs kann das SDK nutzen.<br /><br /> **MinVSVersion:** Dieses Attribut wird von Visual Studio verwendet, um nur die SDKs verwenden, die auf sie anwenden.<br /><br /> **Referenz:** Dieses Attribut muss für nur die Verweise angegeben werden, die Steuerelemente enthalten. Informationen zur Verwendung an, ob ein Verweis auf Steuerelemente enthält finden Sie unten. |

## <a name="ExtensionSDKs"></a> Erweiterungs-SDKs
 In den folgenden Abschnitten wird beschrieben, was Sie tun, um ein Erweiterungs-SDK bereitstellen müssen.

### <a name="installation"></a>Installation
 Erweiterungs-SDKs können für einen bestimmten Benutzer oder für alle Benutzer installiert werden, ohne einen Registrierungsschlüssel. Um ein SDK für alle Benutzer zu installieren, verwenden Sie den folgenden Pfad:

 *% Programm Files%\Microsoft SDKs\<Zielplattform\>\v < Versionsnummer der Plattform\>\ExtensionSDKs*

 Verwenden Sie für eine benutzerdefinierte Installation den folgenden Pfad:

 *%USERPROFILE%\AppData\Local\Microsoft SDKs\<Zielplattform\>\v < Versionsnummer der Plattform\>\ExtensionSDKs*

 Wenn Sie einen anderen Speicherort verwenden möchten, müssen Sie einen der folgenden Schritte ausführen:

1. Geben sie in einem Registrierungsschlüssel:

     **HKLM\Software\Microsoft\Microsoft SDKs\<Zielplattform > \v < Versionsnummer der Plattform\>\ExtensionSDKs\<SDKName >\<SDKVersion >** \

     und fügen Sie einen (Standard)-Unterschlüssel mit dem Wert des `<path to SDK><SDKName><SDKVersion>`.

2. Fügen Sie die MSBuild-Eigenschaft `SDKReferenceDirectoryRoot` zu Ihrer Projektdatei. Der Wert dieser Eigenschaft ist eine durch Semikolons getrennte Liste von Verzeichnissen, die in denen befinden die Erweiterungs-SDKs, die Sie verweisen möchten.

### <a name="installation-layout"></a>Installationslayout
 Erweiterungs-SDKs haben das folgende installationslayout:

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

1. \\< SDKName\>\\< SDKVersion\>: Name und Version der Erweiterung SDK wird die entsprechenden Ordnernamen im Pfad zum SDK-Stamm abgeleitet. MSBuild verwendet diese Identität, um das SDK finden Sie auf dem Datenträger, und zeigt diese Identität in Visual Studio die **Eigenschaften** Fenster und **Verweis-Manager** Dialogfeld.

2. *Verweise* Ordner: die Binärdateien, die die APIs enthalten. Dabei kann es sich um Windows-Metadatendateien (WinMD) oder Assemblys handeln.

3. *Redist* Ordner: die Dateien, die für die Common Language Runtime/Debuggen erforderlich sind, und sollte als Teil der Anwendung des Benutzers verpackt zu erhalten. Alle Binärdateien platziert werden soll, darunter *\redist\\< Config\>\\< Arch\>* , und binärdateinamen sollte das folgende Format, um die Eindeutigkeit sicherzustellen: *]* \<Unternehmen >. \<Produkt >. \<Zweck >. \<Erweiterung ><em>. Z. B. *Microsoft.Cpp.Build.dll</em>. Alle Dateien mit Namen, die in Konflikt stehen möglicherweise mit dem Dateinamen aus anderen SDKs (z. B. Javascript, Css, Pri, Xaml, Png und Jpg-Dateien) platziert werden soll, darunter <em>\redist\\< Config\>\\< arch\> \\< Sdkname\> \* steuert, mit Ausnahme der Dateien, die XAML zugeordnet sind. Diese Dateien gespeichert werden sollen, darunter * \redist\\< Config\>\\< Arch\>\\< Komponentenname\>\\</em>.

4. *DesignTime* Ordner: die Dateien, die auf nur pre-ausführen/Debuggen erforderlich sind, Zeit und sollten nicht als Teil des Benutzers-Anwendung verpackt werden. Diese können XML-Dokumente, Bibliotheken, Headern, Toolbox während der Entwurfszeit-Binärdateien, MSBuild-Elemente usw. sein. Alle SDK, die vorgesehen ist, für die Nutzung von einem systemeigenen Projekt muss eine *SDKName.props* Datei. Das folgende Beispiel zeigt ein Beispiel für diesen Dateityp.

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

    XML-Referenzdokumente werden zusammen mit der Referenzdatei platziert. Z. B. das XML-Referenzdokument für die *\References\\< Config\>\\< Arch\>\sample.dll* Assembly *\References\\ < Config\>\\< Arch\>\sample.xml*, und die lokalisierte Version dieses Dokuments ist *\References\\< Config\>\\< Arch\>\\< Gebietsschema\>\sample.xml*.

5. *Konfiguration* Ordner: drei Unterordnern: *Debuggen von*, *Retail*, und *CommonConfiguration*. SDK-Autoren können ihre Dateien unterhalb platzieren *CommonConfiguration* bei der gleiche Satz von SDK-Dateien genutzt werden sollen, unabhängig von der Konfiguration für die SDK-Consumers.

6. *Architektur* Ordner: die folgenden Architekturen werden unterstützt: X86, X64, ARM, Neutral. Win32 X86 zugeordnet, und "anycpu" neutrale zugeordnet.

### <a name="sdkmanifestxml"></a>SDKManifest.xml
 Diese Datei beschreibt, wie das SDK von Visual Studio reserviert werden soll. Nachfolgend finden Sie ein Beispiel:

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

 Die folgende Liste stellt die Elemente der Datei.

1. DisplayName: der Wert, der im Verweis-Manager, Projektmappen-Explorer, Objekt-Browser und andere Speicherorte in der Benutzeroberfläche von Visual Studio angezeigt wird.

2. ProductFamilyName: Der gesamte SDK-Produktname. Z. B. die [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK heißt "Microsoft.WinJS.1.0" und "Microsoft.WinJS.2.0", die zu derselben Familie der SDK-Familie, "Microsoft.WinJS" gehören. Dieses Attribut ermöglicht Visual Studio und MSBuild, um diese Verbindung zu erstellen. Wenn dieses Attribut nicht vorhanden ist, wird der SDK-Name als der Name der Produktreihe verwendet.

3. FrameworkIdentity: Gibt eine Abhängigkeit auf eine oder mehrere Bibliotheken der Windows-Komponente. Der Wert dieses Attributs wird in der verwendeten app-Manifest eingefügt. Dieses Attribut gilt nur für Windows-Komponentenbibliotheken zur Verfügung.

4. TargetFramework: Gibt an, die SDKs, die im Verweis-Manager und der Toolbox verfügbar sind. Dies ist eine durch Semikolons getrennte Liste von Target frameworkMoniker, z. B. ".NET Framework, Version = v2. 0; .NET Framework, Version 4.5.1 =". Wenn mehrere Versionen des gleichen Zielframeworks angegeben sind, verwendet der Verweis-Manager die niedrigste angegebene Version filtern. Z. B. wenn ".NET Framework, Version = v2. 0; .NET Framework, Version 4.5.1 =" angegeben ist, verwendet der Bezugsmanager ".NET Framework, Version = v2. 0". Wenn ein bestimmtes Ziel-Framework-Profil angegeben ist, wird nur für dieses Profil vom Verweis-Manager verwendet werden filtern. Z. B., wenn "Silverlight, Version = v4. 0, Profil WindowsPhone =" angegeben ist, Verweis-Manager filtert auf nur die Windows Phone-Profil ein Projekt, das vollständige Silverlight 4.0 Framework wird das SDK im Verweis-Manager nicht angezeigt.

5. MinVSVersion: Die minimale Visual Studio-Version.

6. MaxPlatformVerson: Die maximale zielplattformversion sollte verwendet werden, an die Plattformversionen, auf denen Ihre Erweiterungs-SDK nicht funktionieren. Beispielsweise sollte das Microsoft Visual C++ Runtime Package V11. 0 nur von Windows 8-Projekte verwiesen werden. Daher ist die Windows 8-Projekt MaxPlatformVersion 8.0. Dies bedeutet, dass der Verweis-Manager Microsoft Visual C++ Runtime Package für ein Windows 8.1-Projekt filtert, und MSBuild löst einen Fehler aus. wenn eine [!INCLUDE[win81](../debugger/includes/win81_md.md)] Projekt verweist darauf. Hinweis: dieses Element wird unterstützt ab [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].

7. AppliesTo: Gibt an, die SDKs, die im Verweis-Manager verfügbar sind, durch Angabe der entsprechende Visual Studio-Projekttypen. Es werden neun Werte erkannt: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, verwaltet, und systemeigene. Der Autor des SDK kann verwenden, und ("+"), oder ("&#124;") und nicht ("!") Operatoren, die genau den Bereich der Projekttypen anzugeben, die für das SDK gelten.

    WindowsAppContainer identifiziert Projekte für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] apps.

8. SupportPrefer32Bit: Unterstützte Werte sind "True" und "False". Der Standardwert ist "True". Wenn der Wert auf "False" festgelegt ist, gibt MSBuild einen Fehler für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Projekte (oder eine Warnung für Desktopprojekte), wenn das Projekt, das das SDK verweist Prefer32Bit aktiviert wurde. Weitere Informationen zu Prefer32Bit, finden Sie unter [Seite "erstellen", Projekt-Designer (c#)](../ide/reference/build-page-project-designer-csharp.md) oder [Seite "Kompilieren", Projekt-Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. SupportedArchitectures: Eine durch Semikolons getrennte Liste von Architekturen, die das SDK unterstützt. MSBuild zeigt eine Warnung aus, wenn die Ziel-SDK-Architektur in das verarbeitende Projekt nicht unterstützt wird. Wenn dieses Attribut nicht angegeben ist, wird MSBuild nie dieser Art der Warnung angezeigt.

10. SupportsMultipleVersions: Wenn dieses Attribut, um festgelegt wird **Fehler** oder **Warnung**, MSBuild gibt an, dass mehrere Versionen derselben Familie SDK nicht das gleiche Projekt verweisen kann. Wenn dieses Attribut ist nicht vorhanden oder NA hodnotu nastaven **zulassen**, MSBuild nicht diese Art von Fehler oder eine Warnung angezeigt.

11. AppX: Gibt den Pfad zu die app-Pakete für die Bibliothek der Windows-Komponente auf dem Datenträger an. Dieser Wert wird an die Komponente für die Registrierung der Komponente Windows-Bibliothek während des lokalen Debuggens übergeben. Die Namenskonvention für den Dateinamen ist  *\<Unternehmen >.\< Produkt >. \<Architektur >. \<Configuration >. \<Version > AppX*. Konfiguration und Architektur sind optional in den Attributnamen und Wert des Attributs, wenn sie nicht der Komponentenbibliothek Windows angewendet werden. Dieser Wert gilt nur für Windows-Komponentenbibliotheken zur Verfügung.

12. CopyRedistToSubDirectory: Gibt an, wo die Dateien unter der *\redist* Ordner kopiert werden sollen, relativ zum Stammverzeichnis app-Paket (, also die **Paketspeicherort** ausgewählt, die der **App-Pakete erstellen** -Assistent) und Common Language Runtime-Layoutstamm. Der Standardspeicherort ist der Stamm des app-Pakets und **F5** Layout.

13. DependsOn: Eine Liste der SDK-Identitäten, die die SDKs zu definieren, von denen dieses SDK abhängig ist. Dieses Attribut wird im Detailbereich des Verweis-Managers angezeigt.

14. MoreInfo: Die URL zur Webseite, die Hilfe und Weitere Informationen bereitstellt. Dieser Wert wird unter dem Link "Weitere Informationen" im rechten Bereich des Verweis-Managers verwendet.

15. Registrierungstyp: Gibt die WinMD-Registrierung im app-Manifest an, und ist für systemeigene WinMD, die eine Entsprechung-Implementierung von DLL erforderlich.

16. Referenz der Datei: Für nur die Verweise, die Steuerelemente enthalten oder systemeigene WinMDs angegeben. Informationen dazu, wie Sie angeben, ob ein Verweis auf Steuerelemente enthält, finden Sie unter [Geben Sie den Speicherort von Toolboxelementen](#ToolboxItems) unten.

## <a name="ToolboxItems"></a> Geben Sie den Speicherort von Toolboxelementen
 Das Element ToolBoxItems der *SDKManifest.xml* Schema gibt die Kategorie und Standort von Toolboxelementen in Plattform- und Erweiterungs-SDKs. Die folgenden Beispiele zeigen, wie Sie verschiedene Speicherorte anzugeben. Dies gilt für WinMD oder die DLL-Verweise.

1. Richten Sie Kontrollen, in die Toolbox Standardkategorie.

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Platzieren Sie Steuerelemente unter einen bestimmten Kategorienamen.

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Platzieren Sie Steuerelemente in bestimmten Kategorienamen.

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Platzieren Sie Steuerelemente in anderen Kategorienamen in Blend und Visual Studio.

    ```
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Bestimmte Steuerelemente anders in Blend und Visual Studio aufgelistet werden.

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Bestimmte Steuerelemente aufgelistet, und platzieren Sie sie an, unter dem Visual Studio-Common-Pfad oder nur in der Gruppe für alle Steuerelemente.

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Bestimmte Steuerelemente aufgelistet, und zeigen Sie nur eine bestimmte Gruppe in ChooseItems, ohne sie in der Toolbox.

    ```
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erstellen eines SDKS mit C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Exemplarische Vorgehensweise: Erstellen Sie eine SDK mit C# oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)
