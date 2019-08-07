---
title: Erstellen eines Software Development Kits | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 042002b6fddb674c0f1c156be2d992cc96cb9f81
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787666"
---
# <a name="create-a-software-development-kit"></a>Erstellen einer Software Development Kit

Ein Software Development Kit (SDK) ist eine Sammlung von APIs, die Sie als einzelnes Element in Visual Studio referenzieren können. Im Dialogfeld **Verweis-Manager** werden alle für das Projekt relevanten sdkys aufgelistet. Wenn Sie einem Projekt ein SDK hinzufügen, sind die APIs in Visual Studio verfügbar.

Es gibt zwei Arten von sdkchen:

- Platform sdgs sind erforderliche Komponenten zum Entwickeln von Apps für eine Plattform. Beispielsweise ist das [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK zum entwickeln [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] von-apps erforderlich.

- Erweiterungs-sDas sind optionale Komponenten, die eine Plattform erweitern, jedoch nicht für die Entwicklung von Apps für diese Plattform obligatorisch sind.

In den folgenden Abschnitten wird die allgemeine Infrastruktur von SDKs und das Erstellen eines Platform SDK und eines Erweiterungs-SDKs beschrieben.

## <a name="platform-sdks"></a>Plattform-sdgs

Plattform-sdgs sind erforderlich, um Apps für eine Plattform zu entwickeln. Beispielsweise ist das [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK zum Entwickeln von Apps für [!INCLUDE[win81](../debugger/includes/win81_md.md)]erforderlich.

### <a name="installation"></a>Installation

Alle Plattform-SDKs werden unter " *HKLM\Software\Microsoft\Microsoft SDKs\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK Root]* " installiert. Dementsprechend wird das [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK unter " *HKLM\Software\Microsoft\Microsoft sdks\windows\v8.1*" installiert.

### <a name="layout"></a>Layout

Platform sdgs verfügen über das folgende Layout:

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
| Ordner " *Verweise* " | Enthält Binärdateien, die APIs enthalten, die für codiert werden können. Diese können Windows-Metadatendateien (winmd) oder Assemblys enthalten. |
| *DesignTime* -Ordner | Enthält Dateien, die nur zum Zeitpunkt des Vorlaufs/Debuggens benötigt werden. Hierzu können XML-Dokumente, Bibliotheken, Header, Toolbox-Entwurfszeit Binärdateien, MSBuild-Artefakte usw. gehören.<br /><br /> XML-Dokumente würden im Idealfall in den Ordner *\designtime* eingefügt werden, aber XML-Dokumente für Verweise werden weiterhin neben der Verweis Datei in Visual Studio platziert. Das XML-Dokument für den Verweis "<em>\references\\\\[config] [Arch] \sample.dll</em> " lautet beispielsweise " *\references\\[config]\\[Arch] \sample.XML*", und die lokalisierte Version dieses Dokuments lautet: *\References\\[config]\\[Arch]\\[locale] \sample.XML*. |
| *Konfigurations* Ordner | Es dürfen nur drei Ordner vorhanden sein: *Debug*, *Retail* und *commonconfiguration*. SDK-Autoren können Ihre Dateien unter *commonconfiguration* platzieren, wenn dieselbe Gruppe von SDK-Dateien verwendet werden soll, unabhängig von der Konfiguration, auf die der SDK-Consumer ausgerichtet ist. |
| *Architektur* Ordner | Alle unterstützten *Architektur* Ordner können vorhanden sein. Visual Studio unterstützt die folgenden Architekturen: x86, x64, Arm und neutral. Hinweis: Win32 ist x86 zugeordnet, und AnyCPU ist neutral zugeordnet.<br /><br /> MSBuild wird nur unter *\commonconfiguration\neutral* für Platform sdgs untersucht. |
| *SDKManifest.xml* | Diese Datei beschreibt, wie Visual Studio das SDK nutzen soll. Sehen Sie sich das SDK- [!INCLUDE[win81](../debugger/includes/win81_md.md)]Manifest für Folgendes an:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Der Wert, der vom Objektkatalog in der Liste durchsuchen angezeigt wird.<br /><br /> **Platformidentity:** Das vorhanden sein dieses Attributs weist Visual Studio und MSBuild an, dass es sich bei dem SDK um ein Platform SDK handelt und dass die von ihm hinzugefügten Verweise nicht lokal kopiert werden sollten.<br /><br /> **TargetFramework:** Dieses Attribut wird von Visual Studio verwendet, um sicherzustellen, dass nur Projekte, die auf dieselben Frameworks abzielen, wie im Wert dieses Attributs angegeben, das SDK nutzen können.<br /><br /> **MinVSVersion:** Dieses Attribut wird von Visual Studio verwendet, um nur die sdche zu verwenden, die für das Attribut gelten.<br /><br /> **Angabe** Dieses Attribut muss nur für die Verweise angegeben werden, die Steuerelemente enthalten. Informationen dazu, wie Sie angeben, ob ein Verweis Steuerelemente enthält, finden Sie unten. |

## <a name="extension-sdks"></a>Erweiterungs-sdche

In den folgenden Abschnitten wird beschrieben, was Sie tun müssen, um ein Erweiterungs-SDK bereitzustellen.

### <a name="installation"></a>Installation

Erweiterungs-sdche können für einen bestimmten Benutzer oder für alle Benutzer installiert werden, ohne einen Registrierungsschlüssel anzugeben. Verwenden Sie zum Installieren eines SDK für alle Benutzer den folgenden Pfad:

*%Programme%\Microsoft sdgs\<Target Platform\>\v < Platform Versionsnummer\>\extensionsdgs*

Verwenden Sie für eine benutzerspezifische Installation den folgenden Pfad:

*%UserProfile%\appdata\local\microsoft sdgs\<Zielplattform\>\v < Plattform-Versions\>Nummer \extensionsdgs*

Wenn Sie einen anderen Speicherort verwenden möchten, müssen Sie einen der beiden folgenden Schritte ausführen:

1. Geben Sie ihn in einem Registrierungsschlüssel an:

     **HKLM\Software\Microsoft\Microsoft SDKs\<Zielplattform > \v < Platt Form Versions\>Nummer \extensionsdks\<sdkname\<> sdkversion >** \

     und fügen einen (Standard-) Unterschlüssel mit `<path to SDK><SDKName><SDKVersion>`dem Wert hinzu.

2. Fügen Sie die MSBuild `SDKReferenceDirectoryRoot` -Eigenschaft zu Ihrer Projektdatei hinzu. Der Wert dieser Eigenschaft ist eine durch Semikolons getrennte Liste von Verzeichnissen, in denen sich die Erweiterungs-sdches befinden, auf die verwiesen werden soll.

### <a name="installation-layout"></a>Installations Layout

Erweiterungs-sdert verfügen über das folgende Installations Layout:

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

1. \\< sdkname\>\\< sdkversion\>: der Name und die Version des Erweiterungs-SDK werden von den entsprechenden Ordnernamen im Pfad zum SDK-Stamm abgeleitet. MSBuild verwendet diese Identität, um das SDK auf dem Datenträger zu finden, und Visual Studio zeigt diese Identität im **Eigenschaften** Fenster und im **Verweis-Manager** -Dialogfeld an.

2. *Verweise* Ordner: die Binärdateien, die die APIs enthalten. Dies können Windows-Metadatendateien (winmd) oder Assemblys sein.

3. *Redist* -Ordner: die Dateien, die für die Laufzeit/das Debuggen erforderlich sind und als Teil der Anwendung des Benutzers verpackt werden. Alle Binärdateien sollten unterhalb von *\Redist\\< config\>\\< Arch\>* platziert werden, und die binären Namen sollten das folgende Format aufweisen, um die Eindeutigkeit sicherzustellen: *]* \<Company >. \<Produkt >. \<Zweck >. \<Erweiterungs ><em>. Beispiel: * Microsoft. cpp. Build. dll</em>. Alle Dateien, deren Namen mit Dateinamen anderer sdcas in Konflikt stehen (z. b. JavaScript-, CSS-, PRI-, XAML-, PNG-und JPG- <em>Dateien),\\sollten unterhalb\>von \Redist < config\\< Arch\>platziertwerden.< sdkname\>außerdenDateien, dieXAML-Steuerelementenzugeordnetsind.\* \\ \\Diese Dateien sollten unterhalb von * \Redist < config\>\\< Arch\\\>\\< componentname\></em>platziert werden.

4. Ordner " *DesignTime* ": die Dateien, die nur zum Zeitpunkt der vor-und Debuggen benötigt werden und nicht als Teil der Anwendung des Benutzers verpackt werden sollten. Dabei kann es sich um XML-Dokumente, Bibliotheken, Header, Toolbox-Entwurfszeit Binärdateien, MSBuild-Artefakte usw. handeln. Jedes SDK, das für die Nutzung durch ein System eigenes Projekt vorgesehen ist, muss über eine *sdkname.* requizeddatei verfügen. Das folgende Beispiel zeigt ein Beispiel für diesen Dateityp.

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

    XML-Verweis Dokumente werden neben der Verweis Datei platziert. Das XML-Referenzdokument für die Assembly *\\\references <\>config\\< Arch\>\sample.dll* lautet z. b. *\references\> \\< config.\\<arch\>\sample.XML*, und die lokalisierte Version dieses Dokuments lautet *\references\\< config\>\\< Arch\>\\< locale\>\sample.XML*.

5. *Konfigurations* Ordner: drei Unterordner: *Debug*, *Retail*und *commonconfiguration*. SDK-Autoren können Ihre Dateien unter *commonconfiguration* platzieren, wenn dieselbe Gruppe von SDK-Dateien verwendet werden soll, unabhängig von der Konfiguration, die der SDK-Consumer als Ziel verwendet.

6. *Architektur* Ordner: die folgenden Architekturen werden unterstützt: x86, x64, arm, neutral. Win32 ist x86 zugeordnet, und AnyCPU ist neutral zugeordnet.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

Die Datei " *sdkmanifest. XML* " beschreibt, wie Visual Studio das SDK nutzen soll. Im Folgenden finden Sie ein Beispiel dazu:

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

1. Display Name: der Wert, der im Verweis-Manager angezeigt wird, Projektmappen-Explorer, Objektkatalog und andere Speicherorte in der Benutzeroberfläche von Visual Studio.

2. Productfamilyname: Der gesamte SDK-Produktname. Das [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK heißt beispielsweise "Microsoft. winjs. 1.0" und "Microsoft. winjs. 2.0", die derselben Familie der SDK-Produktfamilie "Microsoft. winjs" angehören. Mit diesem Attribut können Visual Studio und MSBuild diese Verbindung herstellen. Wenn dieses Attribut nicht vorhanden ist, wird der SDK-Name als Produkt Familienname verwendet.

3. FrameworkIdentity Gibt eine Abhängigkeit von mindestens einer Windows-Komponentenbibliothek an. Der Wert dieses Attributs wird in das Manifest der erbenden app eingefügt. Dieses Attribut ist nur auf Windows-Komponenten Bibliotheken anwendbar.

4. TargetFramework: Gibt die sdche an, die im Verweis-Manager und in der Toolbox verfügbar sind. Dies ist eine durch Semikolons getrennte Liste der zielframeworkmoniker, z. b. ".NET Framework, Version = v 2.0; .NET Framework, Version = v 4.5.1". Wenn mehrere Versionen desselben Ziel Frameworks angegeben werden, verwendet der Verweis-Manager die niedrigste angegebene Version für Filter Zwecke. Wenn z. b. ".NET Framework, Version = v 2.0; .NET Framework, Version = v 4.5.1" angegeben ist, verwendet der Verweis-Manager ".NET Framework, Version = v 2.0". Wenn ein bestimmtes Ziel Framework-Profil angegeben wird, wird nur dieses Profil vom Verweis-Manager zu Filter Zwecken verwendet. Wenn z. b. "Silverlight, Version = v 4.0, Profile = windowsphone" angegeben wird, filtert der Verweis-Manager nur das Windows Phone Profil. für ein Projekt, das auf das vollständige Silverlight 4,0-Framework abzielt, wird das SDK nicht im Verweis-Manager angezeigt.

5. MinVSVersion: Die minimale Visual Studio-Version.

6. MaxPlatformVerson: Die maximale Ziel Platt Form Version sollte verwendet werden, um die Platt Form Versionen anzugeben, auf denen das Erweiterungs-SDK nicht funktioniert. Beispielsweise sollte auf das Microsoft C++ Visual Runtime Package v 11.0 nur von Windows 8-Projekten verwiesen werden. Daher ist die maxplatformversion des Windows 8-Projekts 8,0. Dies bedeutet, dass der Verweis-Manager das Microsoft C++ Visual Runtime-Paket für ein Windows 8.1 Projekt filtert und dass MSBuild einen [!INCLUDE[win81](../debugger/includes/win81_md.md)] Fehler auslöst, wenn ein Projekt darauf verweist. Hinweis: dieses Element wird ab [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]unterstützt.

7. AppliesTo Gibt die sdche an, die im Verweis-Manager verfügbar sind, indem Sie die entsprechenden Visual Studio-Projekttypen angeben. Neun Werte werden erkannt: Windowsapcontainer, VisualC, VB, CSharp, windowsxaml, JavaScript, verwaltet und nativ. Der SDK-Autor kann and ("+"), or ("&#124;"), Not ("!") verwenden. Operatoren, um genau den Bereich von Projekttypen anzugeben, die für das SDK gelten.

    Windowsappcontainer identifiziert Projekte für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] -apps.

8. SupportPrefer32Bit: Unterstützte Werte sind "true" und "false". Der Standardwert ist "true". Wenn der Wert auf "false" festgelegt ist, gibt MSBuild einen Fehler [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] für Projekte (oder eine Warnung für Desktop Projekte) zurück, wenn für das Projekt, das auf das SDK verweist, Prefer32Bit aktiviert ist. Weitere Informationen zu Prefer32Bit finden Sie unter [Seite "erstellen", ProjektC#-Designer ()](../ide/reference/build-page-project-designer-csharp.md) oder " [Kompilierungs Seite", Projekt-Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. Supportedarchitectures: Eine durch Semikolons getrennte Liste von Architekturen, die das SDK unterstützt. MSBuild zeigt eine Warnung an, wenn die Ziel-SDK-Architektur im verarbeitenden Projekt nicht unterstützt wird. Wenn dieses Attribut nicht angegeben ist, zeigt MSBuild diesen Warnungstyp nie an.

10. SupportsMultipleVersions: Wenn dieses Attribut auf " **Error** " oder " **Warning**" festgelegt ist, gibt MSBuild an, dass das gleiche Projekt nicht auf mehrere Versionen derselben SDK-Familie verweisen kann. Wenn dieses Attribut nicht vorhanden oder auf " **zulassen**" festgelegt ist, zeigt MSBuild diese Art von Fehler oder Warnung nicht an.

11. AppX: Gibt den Pfad zu den App-Paketen für die Windows-Komponentenbibliothek auf dem Datenträger an. Dieser Wert wird während des lokalen Debuggens an die Registrierungs Komponente der Windows-Komponentenbibliothek übermittelt. Die Benennungs Konvention für den Dateinamen lautet  *\<Company >\< . Produkt >. \<Architektur >. \<Konfigurations >. Version\<>. AppX*. Konfiguration und Architektur sind im Attributnamen und im Attribut Wert optional, wenn Sie nicht auf die Windows-Komponentenbibliothek angewendet werden. Dieser Wert gilt nur für Windows-Komponenten Bibliotheken.

12. CopyRedistToSubDirectory: Gibt an, wo die Dateien im Ordner *\Redist* relativ zum Stamm des App-Pakets kopiert werden sollen (d. h. der im Assistenten zum **Erstellen von App-Paketen** ausgewählte Paketspeicherort) und das Lauf Zeit Layout-Stammverzeichnis. Der Standard Speicherort ist der Stamm des App-Pakets und des **F5** -Layouts.

13. DependsOn Eine Liste der SDK-Identitäten, die die SDKs definieren, von denen dieses SDK abhängig ist. Dieses Attribut wird im Detailbereich des Verweis-Managers angezeigt.

14. Moreingefo: Die URL der Webseite, die Hilfe und weitere Informationen enthält. Dieser Wert wird im rechten Bereich des Verweis-Managers im Link Weitere Informationen verwendet.

15. Registrierungstyp: Gibt die winmd-Registrierung im App-Manifest an und ist für die systemeigene winmd-Datei erforderlich, die über eine entsprechende Implementierungs-DLL verfügt.

16. Datei Verweis: Wird nur für die Verweise angegeben, die Steuerelemente enthalten oder Native winmds sind. Informationen dazu, wie Sie angeben, ob ein Verweis Steuerelemente enthält, finden Sie unten unter [angeben des Speicher Orts der Toolbox Elemente](#ToolboxItems) .

## <a name="ToolboxItems"></a>Geben Sie den Speicherort von Toolbox Elementen an.

Das **ToolBoxItems** -Element des Schemas " *sdkmanifest. XML* " gibt die Kategorie und den Speicherort der Toolbox Elemente in Plattform-und Erweiterungs-SDKs an. In den folgenden Beispielen wird gezeigt, wie verschiedene Speicherorte angegeben werden. Dies gilt sowohl für winmd-als auch für dll-Verweise.

1. Platzieren Sie Steuerelemente in der Standard Kategorie der Toolbox.

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

4. Platzieren Sie Steuerelemente unter verschiedenen Kategorien Amen in Blend und Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Auflisten spezifischer Steuerelemente in Blend und Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Auflisten bestimmter Steuerelemente und Platzieren der Steuerelemente unter dem allgemeinen Pfad von Visual Studio oder nur in der Gruppe "alle Steuerelemente".

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Listet bestimmte Steuerelemente auf und zeigt nur eine bestimmte Menge in Auswahllisten an, ohne dass Sie in der Toolbox enthalten sind.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Erstellen eines SDK mithilfe vonC++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Exemplarische Vorgehensweise: Erstellen eines SDK mithilfe C# von oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)