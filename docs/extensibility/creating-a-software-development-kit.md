---
title: Erstellen eines Software Development Kits | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: "54"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4ea17b02cfa2e987c4a3c02acddf838001b4ae2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-software-development-kit"></a>Erstellen eines Software Development Kits
Ein Software Development Kit (SDK) ist eine Sammlung von APIs, die Sie als ein einzelnes Element in Visual Studio verweisen können. Die **Verweis-Manager** Dialogfeld führt alle SDK auf, die für das Projekt relevant sind. Wenn Sie ein Projekt eine SDK hinzufügen, sind die APIs in Visual Studio verfügbar.  
  
 Es gibt zwei Arten der SDKs:  
  
-   Plattform-SDKs sind erforderliche Komponenten für die Entwicklung von apps für eine Plattform. Z. B. die [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK ist erforderlich, um entwickeln [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] apps.  
  
-   Erweiterungs-SDKs sind optionale Komponenten, die eine Plattform zu erweitern, aber nicht für das Entwickeln von apps für diese Plattform erforderlich.  
  
 Die folgenden Abschnitte beschreiben die allgemeine Infrastruktur des SDKs und erstellen Sie eine Plattform-SDK und einer Erweiterungs-SDK.  
  
-   [Plattform-SDKs](#PlatformSDKs)  
  
-   [Erweiterungs-SDKs](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a>Plattform-SDKs  
 Plattform-SDKs sind erforderlich, zum Entwickeln von apps für eine Plattform. Z. B. die [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK ist erforderlich, um das Entwickeln von apps für [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### <a name="installation"></a>Installation  
 Alle Plattform-SDKs wird unter HKLM\Software\Microsoft\Microsoft SDKs installiert\\[TPI] \v [TPI]\\ @InstallationFolder = [SDK Root]. Entsprechend der [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK wird unter HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 installiert.  
  
### <a name="layout"></a>Layout  
 Plattform-SDKs müssen die folgenden dargestellt:  
  
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
|Verweise (Ordner)|Enthält die Binärdateien, die APIs enthalten, die gegen codiert werden können. Diese können Windows-Metadatendateien (WinMD) oder Assemblys enthalten.|  
|DesignTime Ordner|Enthält Dateien, die nur zum Zeitpunkt der pre-run/Debuggen erforderlich sind. Diese können XML-Dokumente, Bibliotheken, Header, Toolbox während der Entwurfszeit-Binärdateien, MSBuild-Elementen usw. enthalten.<br /><br /> XML-Dokumente würde idealerweise im Ordner "\DesignTime" platziert werden, aber XML-Dokumente Verweise weiterhin zusammen mit dem Verweisdatei in Visual Studio platziert werden. Z. B. das XML-Dokument für einen Verweis \References\\[Config]\\[arch]\sample.dll werden \References\\[Config]\\[arch]\sample.xml und die lokalisierte Version dieses Dokuments werden \References\\[Config]\\[Arch]\\[locale]\sample.xml.|  
|Ordner für die Konfiguration|Es können nur drei Ordner vorhanden sein: Debug "," Retail "und" CommonConfiguration. SDK-Autoren können ihre Dateien unter CommonConfiguration platzieren, wenn Sie der gleiche Satz von SDK-Dateien, unabhängig von der Konfiguration verwendet werden sollen, die der Consumer SDK abzielen.|  
|Architektur-Ordner|Kann einen beliebigen unterstützten Architektur Ordner vorhanden sein. Visual Studio unterstützt die folgenden Architekturen: X86, X64, ARM- und Neutral. Hinweis: Win32 X86 ist und "anycpu" neutrale zugeordnet.<br /><br /> MSBuild sucht nur unter \CommonConfiguration\neutral Plattform-SDKs.|  
|SDKManifest.xml|Diese Datei wird beschrieben, wie Visual Studio SDK reserviert werden soll. Betrachten Sie das SDK-Manifest für [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** der Wert, der den Objektkatalog in der Liste angezeigt.<br /><br /> **PlatformIdentity:** das Vorhandensein dieses Attributs teilt Visual Studio und MSBuild, dass das SDK eine Plattform-SDK ist und die Verweise hinzugefügt, daraus kopiert werden sollten nicht lokal.<br /><br /> **TargetFramework:** dieses Attribut wird von Visual Studio verwendet, um sicherzustellen, die nur Projekte, auf die gleichen Frameworks entsprechend den Angaben in den Wert dieses Attributs, das SDK genutzt werden kann.<br /><br /> **MinVSVersion:** dieses Attribut wird von Visual Studio verwendet, um nur die SDKs nutzen, die für sie gelten.<br /><br /> **Referenz:** dieses Attribut muss für die nur die Verweise angegeben werden, die Steuerelemente enthalten. Informationen dazu, wie Sie angeben, ob ein Verweis Steuerelemente enthält finden Sie weiter unten.|  
  
##  <a name="ExtensionSDKs"></a>Erweiterungs-SDKs  
 In den folgenden Abschnitten wird beschrieben, was Sie tun können, um eine Erweiterungs-SDK bereitstellen müssen.  
  
### <a name="installation"></a>Installation  
 Erweiterungs-SDKs können für einen bestimmten Benutzer oder für alle Benutzer installiert werden, ohne dass einen Registrierungsschlüssel. Um ein SDK für alle Benutzer zu installieren, verwenden Sie den folgenden Pfad ein:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Verwenden Sie für eine benutzerspezifische-Installation die folgenden Pfad ein:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Wenn Sie einen anderen Speicherort verwenden möchten, müssen Sie eine der beiden folgenden Aktionen ausführen:  
  
1.  Geben Sie ihn in einem Registrierungsschlüssel ein:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     und fügen Sie einen Unterschlüssel (Standard), dessen Wert der `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Fügen Sie die MSBuild-Eigenschaft `SDKReferenceDirectoryRoot` der Projektdatei. Der Wert dieser Eigenschaft ist eine Semi Doppelpunkt getrennte Liste von Verzeichnissen, in denen die Erweiterungs-SDKs, die Sie verweisen möchten befinden.  
  
### <a name="installation-layout"></a>Installationslayout  
 Erweiterungs-SDKs haben die folgenden installationslayout:  
  
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
  
1.  \\< SDKName\>\\< SDKVersion\>: Name und Version der Erweiterung SDK ist die entsprechenden Ordnernamen im Pfad zum Stamm SDK abgeleitet. MSBuild verwendet diese Identität, um das SDK auf dem Datenträger zu finden, und zeigt diese Identität in Visual Studio die **Eigenschaften** Fenster und **Verweis-Manager** Dialogfeld.  
  
2.  Ordner "Verweise": die Binärdateien, die die APIs enthalten. Diese können Windows-Metadatendateien (WinMD) oder Assemblys sein.  
  
3.  Ordner "Redist": die Dateien, die Laufzeit/Debuggen erforderlich sind und als Teil der Anwendung des Benutzers abrufen soll. Alle Binärdateien platziert werden sollten, darunter \redist\\< Config\>\\< Arch\>, und binärdateinamen sollte das folgende Format zum Sicherstellen der Eindeutigkeit:  **\<Unternehmen >.\< Product >. \<Zweck >. \<Erweiterung >**. Beispiel: Microsoft.Cpp.Build.dll. Alle Dateien mit Namen, die in Konflikt stehen möglicherweise mit Dateinamen, die von anderen SDKs (z. B. Javascript, Css, Pri, Xaml, Png und Jpg-Dateien) gespeichert werden sollen, darunter \redist\\< Config\>\\< Arch\> \\< Sdkname\>\ steuert, mit Ausnahme der Dateien, die XAML zugeordnet sind. Diese Dateien gespeichert werden sollen, darunter \redist\\< Config\>\\< Arch\>\\< Komponentenname\>\\.  
  
4.  DesignTime Ordner: die Dateien, die auf nur pre-run/Debuggen benötigt werden Zeit und sollten nicht als Teil des Benutzers Anwendung verpackt werden. Diese können XML-Dokumente, Bibliotheken, Header, Toolbox während der Entwurfszeit-Binärdateien, MSBuild-Elemente usw. sein. Alle SDK, die vorgesehen ist, Verbrauch von einem systemeigenen Projekt muss über eine *SDKName*PROPS-Datei. Das folgende Beispiel zeigt ein Beispiel für diese Art von Datei.  
  
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
  
     XML-Referenzdokumente werden zusammen mit der Verweisdatei platziert. Z. B. das XML-Verweisdokument für die **\References\\< Config\>\\< Arch\>\sample.dll** Assembly **\References\\ < Config\>\\< Arch\>\sample.xml**, und die lokalisierte Version dieses Dokuments ist **\References\\< Config\>\\< Arch\>\\< Locale\>\sample.xml**.  
  
5.  Ordner für die Konfiguration: drei Unterordnern: Debuggen, Verkaufs- und CommonConfiguration. SDK-Autoren können ihre Dateien unter CommonConfiguration platzieren, wenn der der gleiche Satz von SDK-Dateien genutzt werden sollen, unabhängig von der Konfiguration, die vom Consumer SDK vorgesehen.  
  
6.  Architektur-Ordner: die folgenden Architekturen werden unterstützt: X86, X64, "ARM", "Neutral. Win32 X86 zugeordnet, und "anycpu" neutrale zugeordnet.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Diese Datei wird beschrieben, wie Visual Studio SDK reserviert werden soll. Nachfolgend finden Sie ein Beispiel:  
  
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
  
 Die folgende Liste enthält die Elemente der Datei.  
  
1.  DisplayName: der Wert, der im Verweis-Manager, Projektmappen-Explorer, Objektkatalog und andere Speicherorte in der Benutzeroberfläche von Visual Studio angezeigt wird.  
  
2.  ProductFamilyName: Der gesamte SDK Produktname. Z. B. die [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK heißt "Microsoft.WinJS.1.0" und "Microsoft.WinJS.2.0", die zu derselben Familie der SDK-Produktfamilie Produkte "Microsoft.WinJS" gehören. Dieses Attribut ermöglicht Visual Studio und MSBuild, um diese Verbindung herzustellen. Wenn dieses Attribut nicht vorhanden ist, wird der SDK-Name als der Name der Produktreihe verwendet.  
  
3.  FrameworkIdentity: Gibt eine Abhängigkeit auf eine oder mehrere Windows-Komponentenbibliotheken, die der Wert dieses Attributs in der verwendeten app-Manifest eingefügt wird. Dieses Attribut gilt nur für Windows-Komponentenbibliotheken zur Verfügung.  
  
4.  TargetFramework: Gibt die SDKs, die im Verweis-Manager und der Toolbox verfügbar sind. Dies ist eine durch Semikolons getrennte Liste der Ziel-Framework-Moniker, z. B. ".NET Framework, Version = v2. 0; .NET Framework, Version = 4.5.1". Wenn mehrere Versionen der gleichen Zielframeworks angegeben sind, verwendet die Verweis-Manager die niedrigste Version angegebene für filterzwecke an. Beispielsweise, wenn ".NET Framework, Version = v2. 0; .NET Framework, Version = 4.5.1" angegeben ist, wird Verweis-Manager verwendet ".NET Framework, Version = v2. 0". Wenn ein bestimmtes Ziel-Framework-Profil angegeben wird, wird nur das Profil durch Verweis-Manager verwendet werden für filterzwecke. Beispielsweise, wenn "Silverlight, Version = v4. 0, Profile = WindowsPhone" angegeben ist, Verweis-Manager filtert nur im Windows Phone-Profil; ein Projekt, das vollständige Silverlight-Framework 4.0 ausgerichtet wird das SDK im Verweis-Manager nicht angezeigt.  
  
5.  MinVSVersion: die Visual Studio Mindestversion.  
  
6.  MaxPlatformVerson: Die maximale Version der Zielplattform sollte verwendet werden, um die Plattformversionen anzugeben, auf denen die Erweiterung-SDK nicht funktionieren. Beispielsweise sollte der Microsoft Visual C++ Runtime Package V11. 0 nur von Windows 8-Projekte verwiesen werden. Daher ist das Windows 8-Projekt MaxPlatformVersion 8.0. Dies bedeutet, dass der Verweis-Manager Microsoft Visual C++-Laufzeitpaket für ein Windows 8.1-Projekt filtert, und MSBuild einen Fehler löst bei einer [!INCLUDE[win81](../debugger/includes/win81_md.md)] Projekt verweist darauf. Hinweis: dieses Element wird unterstützt ab [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
7.  AppliesTo: Gibt die SDKs, die im Verweis-Manager verfügbar sind, durch Angeben der geltenden Visual Studio-Projekttypen. Es werden neun Werte erkannt: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, verwaltet und systemeigen. Der Autor des SDK können und ("+"), oder ("&#124;"), nicht ("!") Operatoren, die genau den Bereich der Projekttypen anzugeben, die für das SDK gelten.  
  
     WindowsAppContainer identifiziert Projekte für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] apps.  
  
8.  SupportPrefer32Bit: Unterstützte Werte sind "True" und "False". Der Standardwert ist "True". Wenn der Wert auf "False" festgelegt ist, gibt MSBuild einen Fehler für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Projekte (oder eine Warnung für Desktopprojekte) Wenn das Projekt, das das SDK verweist Prefer32Bit aktiviert wurde. Weitere Informationen zu Prefer32Bit, finden Sie unter [Seite "Build", Projekt-Designer (c#)](../ide/reference/build-page-project-designer-csharp.md) oder [Seite kompilieren, Projekt-Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: eine durch Semikolons getrennte Liste von Architekturen, die das SDK unterstützt. MSBuild zeigt eine Warnung aus, wenn die gezielte SDK-Architektur in das betreffende Projekt nicht unterstützt wird. Wenn dieses Attribut nicht angegeben ist, zeigt MSBuild nie diesen Typ der Warnung.  
  
10. SupportsMultipleVersions: Wenn dieses Attribut, um festgelegt ist **Fehler** oder **Warnung**, MSBuild gibt an, dass die gleiche Projekt mehrere Versionen derselben Familie SDK verweisen kann. Wenn dieses Attribut ist nicht vorhanden oder, um festgelegt wird **zulassen**, MSBuild wird diese Art von Fehler oder eine Warnung angezeigt.  
  
11. AppX: Gibt den Pfad zu der app-Pakete für die Bibliothek der Windows-Komponenten auf dem Datenträger. Dieser Wert wird an die Komponente für die Registrierung von der Bibliothek für Windows-Komponente beim lokalen Debuggen übergeben. Die Namenskonvention für den Dateinamen ist  **\<Unternehmen >.\< Product >. \<Architektur >. \<Konfiguration >. \<Version > AppX**. Konfiguration und Architektur sind in den Attributnamen und Wert des Attributs optional, wenn sie für die Bibliothek für Windows-Komponente nicht gelten. Dieser Wert gilt nur für Windows-Komponentenbibliotheken zur Verfügung.  
  
12. CopyRedistToSubDirectory: Gibt an, in dem die Dateien im Ordner \redist relativ zum Stammverzeichnis app-Paket kopiert werden sollen (d. h. die **Paketspeicherort** in den App-Pakete erstellen-Assistenten ausgewählt wurde) und Common Language Runtime-Layout-Stamm. Der Standardspeicherort ist der Stamm der app-Paket und die F5-Layout.  
  
13. "DependsOn": Eine Liste von SDK-Identitäten, die die SDKs definieren, von denen dieses SDK abhängig ist. Dieses Attribut wird im Detailbereich des Verweis-Managers angezeigt.  
  
14. MoreInfo: die URL der Webseite, die Hilfe und Weitere Informationen bereitstellt. Dieser Wert wird in den Link Weitere Informationen im rechten Bereich des Verweis-Managers verwendet.  
  
15. Registrierungstyp: Gibt an, die WinMD-Registrierung im app-Manifest und ist für systemeigene WinMD, besitzt eine Entsprechung Implementierung DLL erforderlich.  
  
16. Dateiverweis: für die nur die Verweise, die Steuerelemente enthalten oder sind systemeigene WinMDs angegeben. Weitere Informationen dazu, wie Sie angeben, ob ein Verweis Steuerelemente enthält, finden Sie unter [angeben Speicherort Toolboxelemente](#ToolboxItems) unten.  
  
##  <a name="ToolboxItems"></a>Angeben des Speicherorts von Toolboxelementen  
 Das ToolBoxItems-Element des Schemas SDKManifest.xml gibt die Kategorie und Standort von Toolboxelementen in Platform und Erweiterungs-SDKs. Die folgenden Beispiele zeigen, wie um verschiedene Speicherorte anzugeben. Dieser Schritt betrifft WinMD oder DLL-Verweise.  
  
1.  Richten Sie Kontrollen in die Toolbox Standardkategorie.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Richten Sie Kontrollen unter einen bestimmten Kategorienamen.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Richten Sie Kontrollen unter bestimmten Kategorienamen.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Richten Sie Kontrollen unter verschiedenen Kategorienamen in Blend und Visual Studio ein.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Auflisten von bestimmter Steuerelemente im Verbund und Visual Studio unterschiedlich.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Bestimmte Steuerelemente aufgelistet und platzieren Sie sie an, unter dem Visual Studio-Common-Pfad oder nur in der Gruppe "alle Steuerelemente".  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Bestimmte Steuerelemente aufgelistet, und zeigen Sie nur eine bestimmte Gruppe in ChooseItems, ohne sie in der Toolbox wird.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer SDKS mit C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Exemplarische Vorgehensweise: Erstellen einer SDKS mit c# oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)