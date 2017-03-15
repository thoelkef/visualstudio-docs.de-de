---
title: "Erstellen eines Software Development Kits | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 54
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 54
---
# Erstellen eines Software Development Kits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein Software Development Kit (SDK) ist eine Sammlung von APIs, die Sie als ein einzelnes Element in Visual Studio verweisen können. Die **Verweis-Manager** Dialogfeld listet alle SDKs, die für das Projekt relevant sind. Wenn Sie einem Projekt eine SDK hinzufügen, werden die APIs in Visual Studio verfügbar.  
  
 Es gibt zwei Arten von SDKs:  
  
-   Plattform-SDKs handelt es sich um erforderliche Komponenten für die Entwicklung von apps für eine Plattform. Zum Beispiel die [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK ist erforderlich, um die Entwicklung [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] apps.  
  
-   Erweiterung-SDKs sind optionale Komponenten, die eine Plattform zu erweitern, aber nicht obligatorisch für die Entwicklung von apps für diese Plattform.  
  
 Die folgenden Abschnitte beschreiben die allgemeine Infrastruktur des SDKs und erstellen eine Plattform-SDK und einer SDK-Erweiterung.  
  
-   [Plattform-SDKs](#PlatformSDKs)  
  
-   [Erweiterung-SDKs](#ExtensionSDKs)  
  
##  <a name="a-nameplatformsdksa-platform-sdks"></a><a name="PlatformSDKs"></a> Plattform-SDKs  
 Plattform-SDKs sind zum Entwickeln von apps für eine Plattform erforderlich. Zum Beispiel die [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK ist erforderlich, um das Entwickeln von apps für [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### <a name="installation"></a>Installation  
 Alle Plattform-SDKs werden am HKLM\Software\Microsoft\Microsoft SDKs installiert\\[TPI] \v [TPI]\\@InstallationFolder = [SDK Root]. Entsprechend der [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK unter HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 installiert ist.  
  
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
  
|Knoten|Beschreibung|  
|----------|-----------------|  
|Verweise (Ordner)|Enthält Binärdateien, die APIs enthalten, die gegen codiert werden können. Diese könnte Windows-Metadatendateien (WinMD) oder Assemblys enthalten.|  
|DesignTime Ordner|Enthält Dateien, die nur zum Zeitpunkt der pre-run/Debuggen erforderlich sind. Hierzu können XML-Dokumente, Bibliotheken, Header, Toolbox Entwurfszeit-Binärdateien, MSBuild-Elemente und usw. gehören.<br /><br /> XML-Dokumente, im Idealfall gespeichert werden im Ordner \DesignTime jedoch XML-Dokumente Verweise weiterhin zusammen mit der Verweisdatei in Visual Studio eingefügt werden. Z. B. das XML-Dokument für einen Verweis \References\\[Config]\\[arch]\sample.dll werden \References\\[Config]\\[arch]\sample.xml und die lokalisierte Version von diesem Dokument werden \References\\[Config]\\[Arch]\\[locale]\sample.xml.|  
|Ordner "Configuration"|Es darf nur drei Ordner: Debuggen, Einzelhandel und CommonConfiguration. SDK-Autoren können ihre Dateien unterhalb CommonConfiguration platzieren, wenn der gleiche Satz von SDK-Dateien, unabhängig von der Konfiguration genutzt werden sollen, die der Consumer SDK abzielen.|  
|Architektur-Ordner|Unterstützte Architektur Ordner kann vorhanden sein. Visual Studio unterstützt die folgenden Architekturen: X86, X64, ARM und Neutral. Hinweis: Win32 X86 ist und AnyCPU neutrale zugeordnet.<br /><br /> MSBuild sucht nur unter \CommonConfiguration\neutral Plattform-SDKs.|  
|SDKManifest.xml|Diese Datei beschreibt, wie Visual Studio SDK genutzt werden sollten. Betrachten Sie das SDK-Manifest für [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = “Windows”             PlatformIdentity = “Windows, version=8.1”             TargetFramework = “.NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1”             MinVSVersion = “14.0”>              <File Reference = “Windows.winmd”>                <ToolboxItems VSCategory = “Toolbox.Default” />             </File> </FileList>`<br /><br /> **DisplayName:** der Wert, der den Objektkatalog in der Suchliste angezeigt.<br /><br /> **PlatformIdentity:** das Vorhandensein dieses Attribut teilt Visual Studio und MSBuild, dass das SDK ein Plattform-SDK ist und die Verweise hinzugefügt, daraus kopiert werden sollten nicht lokal.<br /><br /> **Für die TargetFramework:** dieses Attribut wird von Visual Studio verwendet, um sicherzustellen, die nur Projekte, auf die gleichen Frameworks gemäß den Wert dieses Attributs kann das SDK nutzen.<br /><br /> **MinVSVersion:** dieses Attribut wird von Visual Studio verwendet, um nur die SDKs nutzen, die darauf anwenden.<br /><br /> **Referenz:** dieses Attribut muss für nur die Verweise angegeben werden, die Steuerelemente enthalten. Informationen dazu, wie Sie angeben, ob ein Verweis auf Steuerelemente enthält finden Sie unter.|  
  
##  <a name="a-nameextensionsdksa-extension-sdks"></a><a name="ExtensionSDKs"></a> Erweiterung-SDKs  
 In den folgenden Abschnitten wird beschrieben, was Sie tun, um eine Erweiterung SDK bereitstellen.  
  
### <a name="installation"></a>Installation  
 Erweiterung-SDKs können für einen bestimmten Benutzer oder für alle Benutzer installiert werden, ohne dass einen Registrierungsschlüssel. Um ein SDK für alle Benutzer zu installieren, verwenden Sie den folgenden Pfad:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Verwenden Sie für eine benutzerspezifische Installation den folgenden Pfad:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Wenn Sie einen anderen Speicherort verwenden möchten, müssen Sie einen der folgenden Schritte ausführen:  
  
1.  Geben sie in einem Registrierungsschlüssel:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     und fügen Sie einen (Standard)-Unterschlüssel mit dem Wert des `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Fügen Sie die MSBuild-Eigenschaft `SDKReferenceDirectoryRoot` zur Projektdatei. Der Wert dieser Eigenschaft ist eine Semi Doppelpunkt getrennte Liste von Verzeichnissen, in denen die Erweiterung-SDKs, die Sie verweisen möchten befinden.  
  
### <a name="installation-layout"></a>Installationslayout  
 Erweiterung-SDKs haben das folgende installationslayout:  
  
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
  
1.  \\< SDKName\>\\< SDKVersion\>: Name und Version der Erweiterung SDK wird die entsprechenden Ordnernamen im Pfad zum Stamm SDK abgeleitet. MSBuild verwendet diese Identität, um das SDK finden Sie auf der Festplatte, und zeigt diese Identität in Visual Studio die **Eigenschaften** Fenster und **Verweis-Manager** Dialogfeld.  
  
2.  Ordner "Verweise": die Binärdateien, die die APIs enthalten. Dabei kann es sich um Windows-Metadatendateien (WinMD) oder Assemblys handeln.  
  
3.  Ordner "Redist": die Dateien, die für die Common Language Runtime/Debuggen erforderlich sind und als Teil der Anwendung des Benutzers erhalten soll. Alle Binärdateien platziert werden soll, unter \redist\\< Config\>\\< Arch\>, und die binären Namen sollte das folgende Format, um sicherzustellen, dass: **\< Unternehmen>. \< Produkt>. \< Zweck>. \< Erweiterung>**. Beispiel: Microsoft.Cpp.Build.dll. Alle Dateien mit Namen, die möglicherweise Konflikte mit Namen von anderen SDKs (z. B. Javascript, Css, Pri, Xaml, Png und Jpg-Dateien) gespeichert werden sollen, darunter \redist\\< Config\>\\< Arch\>\\< Sdkname\>\ steuert, mit Ausnahme der Dateien, die mit XAML zugeordnet sind. Diese Dateien gespeichert werden sollen, darunter \redist\\< Config\>\\< Arch\>\\< Komponentenname\>\\.  
  
4.  DesignTime Ordner: Dateien, die auf nur pre-run/Debuggen benötigt werden Zeit und sollten nicht als Teil der Anwendung verpackt werden. Dabei kann es sich um XML-Dokumente, Bibliotheken, Header, Toolbox Entwurfszeit-Binärdateien, MSBuild-Elemente und usw. handeln. Alle SDKS, das bestimmt ist, für die Nutzung von einem systemeigenen Projekt benötigen eine *SDKName*PROPS-Datei. Im folgenden sehen ein Beispiel für diese Art von Datei.  
  
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
  
     XML-Referenzdokumente werden zusammen mit der Verweisdatei platziert. Z. B. das XML-Dokument referenzieren für die **\References\\< Config\>\\< Arch\>\sample.dll** Assembly **\References\\< Config\>\\< Arch\>\sample.xml**, und die lokalisierte Version von diesem Dokument ist **\References\\< Config\>\\< Arch\>\\< Gebietsschema\>\sample.xml**.  
  
5.  Konfigurationsordner: drei Unterordnern: Debug, Verkaufs- und CommonConfiguration. SDK-Autoren können ihre Dateien unterhalb CommonConfiguration platzieren, wenn der gleiche Satz von SDK-Dateien genutzt werden sollen, unabhängig von der Konfiguration, die das Ziel des SDK-Consumers.  
  
6.  Architektur-Ordner: folgenden Architekturen werden unterstützt: X86, X64, ARM, Neutral. Win32 ordnet X86 und AnyCPU neutrale zugeordnet.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Diese Datei beschreibt, wie Visual Studio SDK genutzt werden sollten. Nachfolgend finden Sie ein Beispiel:  
  
```  
<FileList>  
DisplayName = “My SDK”  
ProductFamilyName = “My SDKs”  
TargetFramework = “.NETCore, version=v4.5.1; .NETFramework, version=v4.5.1”  
MinVSVersion = “14.0”  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = “True”  
SupportedArchitectures = “x86;x64;ARM”  
SupportsMultipleVersions = “Error”  
CopyRedistToSubDirectory = “.”  
DependsOn = “SDKB, version=2.0”  
MoreInfo = “http://msdn.microsoft.com/MySDK”>  
<File Reference = “MySDK.Sprint.winmd” Implementation = “XNASprintImpl.dll”>  
<Registration Type = “Flipper” Implementation = “XNASprintFlipperImpl.dll” />  
<Registration Type = “Flexer” Implementation = “XNASprintFlexerImpl.dll” />  
<ToolboxItems VSCategory = “Toolbox.Default” />  
</File>  
</FileList>  
```  
  
 Die folgende Liste enthält die Elemente der Datei.  
  
1.  DisplayName: der Wert, der im Verweis-Manager, Projektmappen-Explorer, Objektkatalog und andere Speicherorte in der Benutzeroberfläche von Visual Studio angezeigt wird.  
  
2.  ProductFamilyName: Der gesamte SDK Produktname. Zum Beispiel die [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK heißt "Microsoft.WinJS.1.0" und "Microsoft.WinJS.2.0", die zu derselben Familie der SDK-Familie, "Microsoft.WinJS" gehören. Dieses Attribut ermöglicht Visual Studio und MSBuild, um diese Verbindung herzustellen. Wenn dieses Attribut nicht vorhanden ist, wird der SDK-Name als der Name der Produktreihe verwendet.  
  
3.  FrameworkIdentity: Gibt eine Abhängigkeit auf eine oder mehrere Windows-Komponentenbibliotheken, die der Wert dieses Attributs in der verarbeitenden app-Manifest eingefügt wird. Dieses Attribut ist nur für Windows-Komponenten-Bibliotheken.  
  
4.  Für die TargetFramework: Gibt die SDKs, die in den Verweis-Manager und der Toolbox verfügbar sind. Dies ist eine durch Semikolons getrennte Liste der Ziel-Framework-Moniker, z. B. ".NET Framework, Version = v2. 0; .NET Framework, Version 4.5.1 =". Wenn mehrere Versionen des gleichen Zielframeworks angegeben sind, verwendet der Verweis-Manager die niedrigste angegebene Version filtern. Zum Beispiel wenn ".NET Framework, Version = v2. 0; .NET Framework, Version 4.5.1 =" angegeben ist, Verweis-Manager verwendet ".NET Framework, Version = v2. 0". Wenn ein bestimmtes Ziel-Framework-Profil angegeben ist, wird nur das Profil durch den Verweis-Manager verwendet werden zum Filtern. Beispielsweise, wenn "Silverlight, Version = v4. 0, Profile = Windows Phone" angegeben ist, Verweis-Manager filtert nur im Windows Phone-Profil; ein Projekt auf das vollständige Framework, Silverlight 4.0 wird das SDK im Verweis-Manager nicht angezeigt.  
  
5.  MinVSVersion: die Visual Studio Mindestversion.  
  
6.  MaxPlatformVerson: Die maximale Version der Zielplattform sollte verwendet werden, an die Plattformversionen, auf denen der SDK-Erweiterung nicht funktioniert. Der Microsoft Visual C++ Runtime Package V11. 0 sollte z. B. nur von Windows 8-Projekte verwiesen werden. Daher ist die Windows 8-Projekt MaxPlatformVersion 8.0. Dies bedeutet, dass der Verweis-Manager Microsoft Visual C++ Runtime Package für Windows 8.1-Projekt filtert und MSBuild einen Fehler löst bei einer [!INCLUDE[win81](../debugger/includes/win81_md.md)] Projekt darauf verweist. Hinweis: dieses Element wird ab unterstützt [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].  
  
7.  AppliesTo: Gibt die SDKs, die durch Angabe der entsprechende Visual Studio-Projekttypen im Verweis-Manager verfügbar sind. Es werden neun Werte erkannt: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, verwaltet und systemeigen. Der Autor des SDK kann verwenden, und ("+"), oder ("&#124;"), nicht ("!") Operatoren zum Angeben der genau des Bereichs Projekttypen zur Verfügung, die für das SDK gelten.  
  
     WindowsAppContainer identifiziert die Projekte für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] apps.  
  
8.  SupportPrefer32Bit: Die unterstützten Werte sind "True" und "False". Der Standardwert ist "True". Wenn der Wert auf 'False' festgelegt ist, gibt MSBuild Fehler [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Projekte (oder eine Warnung für Desktopprojekte), wenn das Projekt, das das SDK verweist Prefer32Bit aktiviert wurde. Weitere Informationen zu Prefer32Bit, finden Sie unter [Seite erstellen, Projekt-Designer (c#)](../ide/reference/build-page-project-designer-csharp.md) oder [Seite kompilieren, Projekt-Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: eine durch Semikolons getrennte Liste von Architekturen, die das SDK unterstützt. MSBuild wird eine Warnung angezeigt, wenn die Ziel die SDK-Architektur in das betreffende Projekt nicht unterstützt wird. Wenn dieses Attribut nicht angegeben ist, zeigt die MSBuild nie dieser Art der Warnung.  
  
10. SupportsMultipleVersions: Wenn dieses Attribut, um festgelegt wird **Fehler** oder **Warnung**, MSBuild gibt an, dass die gleiche Projekt mehrere Versionen derselben Familie SDK verweisen kann. Wenn dieses Attribut nicht vorhanden oder ist auf festgelegt **Zulassen**, MSBuild wird diese Art von Fehler oder eine Warnung angezeigt.  
  
11. AppX: Gibt den Pfad zu der app-Pakete für die Bibliothek zu Windows-Komponente auf dem Datenträger. Dieser Wert wird an die Komponente für die Registrierung der Komponente Windows-Bibliothek beim lokalen Debuggen übergeben. Die Namenskonvention für den Dateinamen ist **\< Unternehmen>. \< Product>. \< Architektur>. \< Configuration>. \< Version>AppX**. Konfiguration und Architektur sind in der Attributname und Attributwert optional, wenn sie nicht in die Windows-Komponentenbibliothek angewendet werden. Dieser Wert gilt nur für Windows-Komponentenbibliotheken zur Verfügung.  
  
12. CopyRedistToSubDirectory: Gibt an, wo die Dateien im Ordner \redist relativ zum Stammverzeichnis app-Pakets kopiert werden sollen (d. h. die **Paket Speicherort** im App-Pakete erstellen-Assistenten ausgewählt) und Common Language Runtime Layoutstamm. Der Standardspeicherort ist der Stamm der app-Pakets und des Layouts von F5.  
  
13. DependsOn: Eine Liste von SDK-Identitäten, die die SDKs definieren, der dieses SDK abhängig. Dieses Attribut wird im Detailbereich des Verweis-Managers angezeigt.  
  
14. Weitere Informationen: die URL der Webseite, die Hilfe und Weitere Informationen bietet. Dieser Wert wird in den Link Weitere Informationen im rechten Bereich des Verweis-Managers verwendet.  
  
15. Registrierungstyp: Gibt die WinMD-Registrierung im app-Manifest und ist erforderlich für systemeigene WinMD, eine Entsprechung Implementierung DLL verfügt.  
  
16. Datei-Referenz: angegeben nur die Verweise, die Steuerelemente enthalten oder systemeigene WinMDs. Weitere Informationen dazu, wie Sie angeben, ob ein Verweis auf Steuerelemente enthält, finden Sie unter [Angeben der Speicherort der Toolboxelemente](#ToolboxItems) unten.  
  
##  <a name="a-nametoolboxitemsa-specifying-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a> Angeben des Speicherorts von Toolboxelementen  
 Das ToolBoxItems-Element des Schemas SDKManifest.xml gibt die Kategorie und Standort von Toolboxelementen in Plattform und Erweiterung-SDKs. Die folgenden Beispiele zeigen, wie Sie verschiedene Speicherorte anzugeben. Dies gilt für WinMD oder DLL-Verweise.  
  
1.  Platzieren Sie Steuerelemente in der Toolbox Standardkategorie.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Default”/>       
    </File>  
    ```  
  
2.  Platzieren Sie Steuerelemente unter einen bestimmten Kategorienamen.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory= “MyCategoryName”/>  
    </File>  
    ```  
  
3.  Platzieren Sie Steuerelemente in bestimmten Kategorienamen.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = “Data”>  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Platzieren Sie Steuerelemente in anderen Kategorienamen in Blend und Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph” BlendCategory = “Controls/sample/Graph”>   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Bestimmte Steuerelemente in Blend und Visual Studio anders aufgezählt werden.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = “Controls/sample/Graph”>  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Auflisten von bestimmten Steuerelementen und platzieren Sie diese unter dem Visual Studio-Common-Pfad oder nur in der Gruppe für alle Steuerelemente.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Common”>  
        <ToolboxItems />  
        <ToolboxItems VSCategory = “Toolbox.All”>  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Bestimmte Steuerelemente auflisten und nur eine bestimmte Gruppe in ChooseItems anzeigen, ohne sie in der Toolbox.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.ChooseItemsOnly”>  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer SDK mit C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Exemplarische Vorgehensweise: Erstellen einer SDK mit c# oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Verwalten von Verweise in einem Projekt](../ide/managing-references-in-a-project.md)