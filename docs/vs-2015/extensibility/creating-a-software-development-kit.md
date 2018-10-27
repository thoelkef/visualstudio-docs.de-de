---
title: Erstellen eines Software Development Kits | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 296bc30089d4c0f4b2b739e1dd977fd66cba1ace
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143293"
---
# <a name="creating-a-software-development-kit"></a>Erstellen eines Software Development Kits
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Software Development Kit (SDK) ist eine Sammlung von APIs, die Sie als ein einzelnes Element in Visual Studio verweisen können. Die **Verweis-Manager** Dialogfeld listet alle SDKs, die für das Projekt relevant sind. Wenn Sie ein Projekt eine SDK hinzufügen, sind die APIs in Visual Studio verfügbar.  
  
 Es gibt zwei Arten von SDKs:  
  
- Plattform-SDKs handelt es sich um erforderliche Komponenten für die Entwicklung von apps für eine Plattform. Z. B. die [!INCLUDE[win81](../includes/win81-md.md)] SDK ist erforderlich, um die Entwicklung [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] apps.  
  
- Erweiterungs-SDKs sind optionale Komponenten, die eine Plattform zu erweitern, aber nicht obligatorisch für die Entwicklung von apps für die betreffende Plattform.  
  
  Die folgenden Abschnitte beschreiben die allgemeine Infrastruktur von SDKs und erstellen Sie eine Plattform-SDK und einer Erweiterungs-SDK.  
  
- [Plattform-SDKs](#PlatformSDKs)  
  
- [Erweiterungs-SDKs](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> Plattform-SDKs  
 Plattform-SDKs sind erforderlich, um apps für eine Plattform zu entwickeln. Z. B. die [!INCLUDE[win81](../includes/win81-md.md)] SDK ist erforderlich, um das Entwickeln von apps für [!INCLUDE[win81](../includes/win81-md.md)].  
  
### <a name="installation"></a>Installation  
 Alle Plattform-SDKs installiert werden unter HKLM\Software\Microsoft\Microsoft SDKs\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK-Stamm]. Entsprechend der [!INCLUDE[win81](../includes/win81-md.md)] unter HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 SDK installiert ist.  
  
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
  
|Knoten|Beschreibung|  
|----------|-----------------|  
|Verweise (Ordner)|Enthält die Binärdateien, die APIs enthalten, die für codiert werden können. Diese können es sich um Windows-Metadatendateien (WinMD) oder Assemblys enthalten.|  
|DesignTime-Ordner|Enthält Dateien, die nur zum Zeitpunkt der pre-ausführen/Debuggen erforderlich sind. Diese können XML-Dokumente, Bibliotheken, Header, Toolbox während der Entwurfszeit-Binärdateien, MSBuild-Elementen usw. enthalten.<br /><br /> XML-Dokumente würden, im Idealfall im Ordner \DesignTime platziert werden, aber weiterhin XML-Dokumente, für Verweise, zusammen mit der Referenzdatei in Visual Studio platziert werden soll. Z. B. das XML-Dokument für einen Verweis \References\\[Config]\\[arch]\sample.dll werden \References\\[Config]\\[arch]\sample.xml und die lokalisierte Version von diesem Dokument werden \References\\[Config]\\[Arch]\\[locale]\sample.xml.|  
|Ordner "Configuration"|Es darf nur drei Ordnern: Debug "," Retail "und" CommonConfiguration. SDK-Autoren können ihre Dateien unterhalb CommonConfiguration platzieren, wenn Sie der gleiche Satz von SDK-Dateien, unabhängig von der Konfiguration genutzt werden sollen, die SDK-Consumers ausgerichtet wird.|  
|Ordner "Architektur"|Jede unterstützte Architektur Ordner kann vorhanden sein. Visual Studio unterstützt die folgenden Architekturen: X86, X64, ARM "und" Neutral. Hinweis: Win32 X86, und "anycpu" auf neutral.<br /><br /> MSBuild sucht nur unter \CommonConfiguration\neutral Plattform-SDKs.|  
|SDKManifest.xml|Diese Datei beschreibt, wie das SDK von Visual Studio reserviert werden soll. Betrachten Sie das SDK-Manifest für [!INCLUDE[win81](../includes/win81-md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **"DisplayName":** der Wert, der die Objekt-Browser in der Suchliste angezeigt.<br /><br /> **PlatformIdentity:** das Vorhandensein dieses Attribut teilt Visual Studio und MSBuild, dass das SDK ein Plattform-SDK ist und die Verweise hinzugefügt, daraus kopiert werden soll, darf nicht lokal.<br /><br /> **TargetFramework:** dieses Attribut wird von Visual Studio verwendet, um sicherzustellen, die nur Projekte, die auf die gleichen Frameworks gemäß dem Wert dieses Attributs kann das SDK nutzen.<br /><br /> **MinVSVersion:** dieses Attribut wird von Visual Studio verwendet, um nur die SDKs verwenden, die auf sie anwenden.<br /><br /> **Referenz:** dieses Attribut muss für nur die Verweise angegeben werden, die Steuerelemente enthalten. Informationen zur Verwendung an, ob ein Verweis auf Steuerelemente enthält finden Sie unten.|  
  
##  <a name="ExtensionSDKs"></a> Erweiterungs-SDKs  
 In den folgenden Abschnitten wird beschrieben, was Sie tun, um ein Erweiterungs-SDK bereitstellen müssen.  
  
### <a name="installation"></a>Installation  
 Erweiterungs-SDKs können für einen bestimmten Benutzer oder für alle Benutzer installiert werden, ohne einen Registrierungsschlüssel. Um ein SDK für alle Benutzer zu installieren, verwenden Sie den folgenden Pfad:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Verwenden Sie für eine benutzerdefinierte Installation den folgenden Pfad:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Wenn Sie einen anderen Speicherort verwenden möchten, müssen Sie einen der folgenden Schritte ausführen:  
  
1.  Geben sie in einem Registrierungsschlüssel:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     und fügen Sie einen (Standard)-Unterschlüssel mit dem Wert des `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Fügen Sie die MSBuild-Eigenschaft `SDKReferenceDirectoryRoot` zu Ihrer Projektdatei. Der Wert dieser Eigenschaft ist eine Semi Doppelpunkt getrennte Liste von Verzeichnissen, die in denen befinden die Erweiterungs-SDKs, die Sie verweisen möchten.  
  
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
  
1.  \\< SDKName\>\\< SDKVersion\>: Name und Version der Erweiterung SDK wird die entsprechenden Ordnernamen im Pfad zum SDK-Stamm abgeleitet. MSBuild verwendet diese Identität, um das SDK finden Sie auf dem Datenträger, und zeigt diese Identität in Visual Studio die **Eigenschaften** Fenster und **Verweis-Manager** Dialogfeld.  
  
2.  Ordner "Verweise": die Binärdateien, die die APIs enthalten. Dabei kann es sich um Windows-Metadatendateien (WinMD) oder Assemblys handeln.  
  
3.  Ordner "Redist": die Dateien, die für die Common Language Runtime/Debuggen erforderlich sind, und sollte als Teil der Anwendung des Benutzers verpackt zu erhalten. Alle Binärdateien platziert werden soll, darunter \redist\\< Config\>\\< Arch\>, und binärdateinamen sollte das folgende Format, um die Eindeutigkeit sicherzustellen:  **\<Unternehmen >.\< Produkt >. \<Zweck >. \<Erweiterung >**. Beispiel: Microsoft.Cpp.Build.dll. Alle Dateien mit Namen, die in Konflikt stehen möglicherweise mit dem Dateinamen aus anderen SDKs (z. B. Javascript, Css, Pri, Xaml, Png und Jpg-Dateien) platziert werden soll, darunter \redist\\< Config\>\\< Arch\> \\< Sdkname\>\ steuert, mit Ausnahme der Dateien, die XAML zugeordnet sind. Diese Dateien gespeichert werden sollen, darunter \redist\\< Config\>\\< Arch\>\\< Komponentenname\>\\.  
  
4.  DesignTime-Ordner: die Dateien, die auf nur pre-ausführen/Debuggen erforderlich sind, Zeit und sollten nicht als Teil des Benutzers-Anwendung verpackt werden. Diese können XML-Dokumente, Bibliotheken, Headern, Toolbox während der Entwurfszeit-Binärdateien, MSBuild-Elemente usw. sein. Alle SDK, die vorgesehen ist, für die Nutzung von einem systemeigenen Projekt muss eine *SDKName*.props-Datei. Das folgende Beispiel zeigt ein Beispiel für diesen Dateityp.  
  
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
  
     XML-Referenzdokumente werden zusammen mit der Referenzdatei platziert. Z. B. das XML-Referenzdokument für die **\References\\< Config\>\\< Arch\>\sample.dll** Assembly **\References\\ < Config\>\\< Arch\>\sample.xml**, und die lokalisierte Version dieses Dokuments ist **\References\\< Config\>\\< Arch\>\\< Gebietsschema\>\sample.xml**.  
  
5.  Ordner "Configuration": drei Unterordnern: Debuggen, Verkaufs- und CommonConfiguration. SDK-Autoren können ihre Dateien unterhalb CommonConfiguration platzieren, wenn Sie der gleiche Satz von SDK-Dateien genutzt werden sollen, unabhängig von der Konfiguration für die SDK-Consumers.  
  
6.  Ordner "Architektur": die folgenden Architekturen werden unterstützt: X86, X64, ARM, Neutral. Win32 X86 zugeordnet, und "anycpu" neutrale zugeordnet.  
  
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
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 Die folgende Liste stellt die Elemente der Datei.  
  
1.  DisplayName: der Wert, der im Verweis-Manager, Projektmappen-Explorer, Objekt-Browser und andere Speicherorte in der Benutzeroberfläche von Visual Studio angezeigt wird.  
  
2.  ProductFamilyName: Der gesamte SDK Produktname. Z. B. die [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] SDK heißt "Microsoft.WinJS.1.0" und "Microsoft.WinJS.2.0", die zu derselben Familie der SDK-Familie, "Microsoft.WinJS" gehören. Dieses Attribut ermöglicht Visual Studio und MSBuild, um diese Verbindung zu erstellen. Wenn dieses Attribut nicht vorhanden ist, wird der SDK-Name als der Name der Produktreihe verwendet.  
  
3.  FrameworkIdentity: Gibt eine Abhängigkeit auf eine oder mehrere Windows-Komponentenbibliotheken, die der Wert dieses Attributs in der verwendeten app-Manifest eingefügt wird. Dieses Attribut gilt nur für Windows-Komponentenbibliotheken zur Verfügung.  
  
4.  TargetFramework: Gibt an, die SDKs, die im Verweis-Manager und der Toolbox verfügbar sind. Dies ist eine durch Semikolons getrennte Liste von Target frameworkMoniker, z. B. ".NET Framework, Version = v2. 0; .NET Framework, Version 4.5.1 =". Wenn mehrere Versionen des gleichen Zielframeworks angegeben sind, verwendet der Verweis-Manager die niedrigste angegebene Version filtern. Z. B. wenn ".NET Framework, Version = v2. 0; .NET Framework, Version 4.5.1 =" angegeben ist, verwendet der Bezugsmanager ".NET Framework, Version = v2. 0". Wenn ein bestimmtes Ziel-Framework-Profil angegeben ist, wird nur für dieses Profil vom Verweis-Manager verwendet werden filtern. Z. B., wenn "Silverlight, Version = v4. 0, Profil WindowsPhone =" angegeben ist, Verweis-Manager filtert auf nur die Windows Phone-Profil ein Projekt, das vollständige Silverlight 4.0 Framework wird das SDK im Verweis-Manager nicht angezeigt.  
  
5.  MinVSVersion: die minimale Visual Studio-Version.  
  
6.  MaxPlatformVerson: Die maximale zielplattformversion sollte verwendet werden, an die Plattformversionen, auf denen Ihre Erweiterungs-SDK nicht funktionieren. Beispielsweise sollte das Microsoft Visual C++ Runtime Package V11. 0 nur von Windows 8-Projekte verwiesen werden. Daher ist die Windows 8-Projekt MaxPlatformVersion 8.0. Dies bedeutet, dass der Verweis-Manager Microsoft Visual C++ Runtime Package für ein Windows 8.1-Projekt filtert, und MSBuild löst einen Fehler aus. wenn eine [!INCLUDE[win81](../includes/win81-md.md)] Projekt verweist darauf. Hinweis: dieses Element wird unterstützt ab [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].  
  
7.  AppliesTo: Gibt an, die SDKs, die im Verweis-Manager verfügbar sind, durch Angabe der entsprechende Visual Studio-Projekttypen. Es werden neun Werte erkannt: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, verwaltet und systemeigen. Der Autor des SDK kann verwenden, und ("+"), oder ("&#124;") und nicht ("!") Operatoren, die genau den Bereich der Projekttypen anzugeben, die für das SDK gelten.  
  
     WindowsAppContainer identifiziert Projekte für [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] apps.  
  
8.  SupportPrefer32Bit: Unterstützte Werte sind "True" und "False". Der Standardwert ist "True". Wenn der Wert auf "False" festgelegt ist, gibt MSBuild einen Fehler für [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Projekte (oder eine Warnung für Desktopprojekte), wenn das Projekt, das das SDK verweist Prefer32Bit aktiviert wurde. Weitere Informationen zu Prefer32Bit, finden Sie unter [Seite "erstellen", Projekt-Designer (c#)](../ide/reference/build-page-project-designer-csharp.md) oder [Seite "Kompilieren", Projekt-Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: eine durch Semikolons getrennte Liste von Architekturen, die das SDK unterstützt. MSBuild zeigt eine Warnung aus, wenn die Ziel-SDK-Architektur in das verarbeitende Projekt nicht unterstützt wird. Wenn dieses Attribut nicht angegeben ist, wird MSBuild nie dieser Art der Warnung angezeigt.  
  
10. SupportsMultipleVersions: Wenn dieses Attribut, um festgelegt wird **Fehler** oder **Warnung**, MSBuild gibt an, dass mehrere Versionen derselben Familie SDK nicht das gleiche Projekt verweisen kann. Wenn dieses Attribut ist nicht vorhanden oder NA hodnotu nastaven **zulassen**, MSBuild nicht diese Art von Fehler oder eine Warnung angezeigt.  
  
11. AppX: Gibt den Pfad zu der app-Pakete für die Bibliothek der Windows-Komponente auf dem Datenträger. Dieser Wert wird an die Komponente für die Registrierung der Komponente Windows-Bibliothek während des lokalen Debuggens übergeben. Die Namenskonvention für den Dateinamen ist  **\<Unternehmen >.\< Produkt >. \<Architektur >. \<Configuration >. \<Version > AppX**. Konfiguration und Architektur sind optional in den Attributnamen und Wert des Attributs, wenn sie nicht der Komponentenbibliothek Windows angewendet werden. Dieser Wert gilt nur für Windows-Komponentenbibliotheken zur Verfügung.  
  
12. CopyRedistToSubDirectory: Gibt an, in dem die Dateien im Ordner \redist relativ zum Stammverzeichnis app-Paket kopiert werden sollen (d. h. die **Paketspeicherort** im App-Pakete erstellen-Assistenten ausgewählt) und Common Language Runtime-Layoutstamm. Der Standardspeicherort ist der Stamm der app-Paket und die F5-Layout.  
  
13. "DependsOn": Eine Liste von SDK-Identitäten, die die SDKs zu definieren, von denen dieses SDK abhängig ist. Dieses Attribut wird im Detailbereich des Verweis-Managers angezeigt.  
  
14. MoreInfo: die URL zur Webseite, die Hilfe und Weitere Informationen bereitstellt. Dieser Wert wird unter dem Link "Weitere Informationen" im rechten Bereich des Verweis-Managers verwendet.  
  
15. Registrierungstyp: die WinMD-Registrierung im app-Manifest angegeben und ist für native WinMD, die eine Entsprechung-Implementierung von DLL erforderlich.  
  
16. Dateiverweis:, die für die nur die Verweise, die Steuerelemente enthalten oder systemeigene WinMDs angegeben werden. Informationen dazu, wie Sie angeben, ob ein Verweis auf Steuerelemente enthält, finden Sie unter [angeben der Speicherort der Toolboxelemente](#ToolboxItems) unten.  
  
##  <a name="ToolboxItems"></a> Angeben des Speicherorts von Toolboxelementen  
 Das ToolBoxItems-Element des Schemas SDKManifest.xml gibt die Kategorie und Standort von Toolboxelementen in Plattform- und Erweiterungs-SDKs an. Die folgenden Beispiele zeigen, wie Sie verschiedene Speicherorte anzugeben. Dies gilt für WinMD oder die DLL-Verweise.  
  
1.  Richten Sie Kontrollen, in die Toolbox Standardkategorie.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Platzieren Sie Steuerelemente unter einen bestimmten Kategorienamen.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Platzieren Sie Steuerelemente in bestimmten Kategorienamen.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Platzieren Sie Steuerelemente in anderen Kategorienamen in Blend und Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Bestimmte Steuerelemente anders in Blend und Visual Studio aufgelistet werden.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Bestimmte Steuerelemente aufgelistet, und platzieren Sie sie an, unter dem Visual Studio-Common-Pfad oder nur in der Gruppe für alle Steuerelemente.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Bestimmte Steuerelemente aufgelistet, und zeigen Sie nur eine bestimmte Gruppe in ChooseItems, ohne sie in der Toolbox.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines SDKS mit C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Exemplarische Vorgehensweise: Erstellen eines SDKS mit c# oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)

