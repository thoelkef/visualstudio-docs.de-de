---
title: Arbeitsauslastungs- und Komponenten-IDs in Visual Studio Enterprise 2017 | Microsoft-Dokumentation
description: "Verwenden Sie Arbeitsauslastungs- und Komponenten-IDs, um Visual Studio über die Befehlszeile zu installieren oder um sie als Abhängigkeit in einem VSIX-Manifest anzugeben"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 03/07/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
- vs-ide-sdk
ms.assetid: be73e3af-d87b-4d14-bd08-2e4bda074fb3
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: b0cb7006a82c1325fd7faecd6ffebb515bb93054
ms.lasthandoff: 03/07/2017

---

# <a name="visual-studio-enterprise-2017-component-directory"></a>Visual Studio Enterprise 2017-Komponentenverzeichnis

In den Tabellen auf dieser Seite sind die IDs aufgeführt, die Sie verwenden können, um Visual Studio über die Befehlszeile zu installieren, oder die Sie als Abhängigkeit in einem VSIX-Manifest angeben können. Beachten Sie, dass weitere Komponenten hinzugefügt werden, wenn wir Updates für Visual Studio veröffentlichen.

Beachten Sie zudem Folgendes im Hinblick auf die Seite:

* Für jede Arbeitsauslastung gibt es einen eigenen Abschnitt, gefolgt von der Arbeitsauslastungs-ID und einer Tabelle der Komponenten, die für die Arbeitsauslastung zur Verfügung stehen.
* Die **erforderlichen** Komponenten werden standardmäßig bei der Installation der Arbeitsauslastung installiert. *Bei Bedarf können Sie auch die**empfohlenen**und**optionalen** Komponenten installieren.
* Wir haben auch einen Abschnitt hinzugefügt, in dem die zusätzlichen Komponenten aufgeführt sind, die keiner Arbeitsauslastung zugeordnet sind.

Wenn Sie Abhängigkeiten im VSIX-Manifest festlegen, müssen Sie nur Komponenten-IDs angeben. Verwenden Sie die Tabellen auf dieser Seite, um die minimalen Komponentenabhängigkeiten zu bestimmen. In einigen Fällen könnte dies bedeuten, dass Sie nur eine Komponente einer Arbeitsauslastung angeben. In anderen Fällen könnte dies bedeuten, dass Sie mehrere Komponenten einer einzelnen Arbeitsauslastung oder mehrere Komponenten von mehreren Arbeitsauslastungen angeben. Weitere Informationen finden Sie auf der Seite [Gewusst wie: Migrieren von Erweiterungsprojekten zu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).


Weitere Informationen zur Verwendung dieser IDs finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Eine Liste der Arbeitsauslastungs- und Komponenten-IDs für andere Produkte finden Sie auf der Seite [Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017](workload-and-component-ids.md).


## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2017"></a>Visual Studio-Kern-Editor (in Visual Studio Enterprise 2017 enthalten)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Beschreibung:** Die Shell-Kernbenutzeroberfläche von Visual Studio, die syntaxfähige Codebearbeitung, Quellcodeverwaltung und Arbeitselementverwaltung bereitstellt.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio-Kern-Editor | Erforderlich


## <a name="azure-development"></a>Azure-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Azure

**Beschreibung:** Azure SDK, Tools und Projekte für die Entwicklung von Cloud-Apps und die Erstellung von Ressourcen.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Erforderlich
Microsoft.Component.NetFX.Core.Runtime | .NET Core-Runtime | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | Erforderlich
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1-Entwicklungstools | Erforderlich
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 – 1.1-Entwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | Erforderlich
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Erforderlich
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Erforderliche Komponenten für die Azure-Entwicklung | Erforderlich
Component.WebSocket | WebSocket4Net | Empfohlen
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake-Tools | Empfohlen
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | Empfohlen
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | Empfohlen
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | Empfohlen
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | Empfohlen
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure Mobile Apps SDK | Empfohlen
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager-Kerntools | Empfohlen
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric-Tools | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | Profilerstellungstools | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | Empfohlen
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Empfohlen
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | Empfohlen
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | Empfohlen
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | Empfohlen
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | Empfohlen
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Empfohlen
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Empfohlen
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | Empfohlen
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Empfohlen
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Empfohlen
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | Empfohlen
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Cloud Services-Tools | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager-Tools | Empfohlen
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | Optional
Microsoft.VisualStudio.Component.PowerShell.Tools | PowerShell-Tools | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional


## <a name="data-storage-and-processing"></a>Datenspeicherung und -verarbeitung

**ID:** Microsoft.VisualStudio.Workload.Data

**Beschreibung:** Verbinden, Entwickeln und Testen von Datenlösungen mit SQL Server, Azure Data Lake, Hadoop oder Azure ML.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Component.Redgate.ReadyRoll | Redgate ReadyRoll | Empfohlen
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt | Empfohlen
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | Empfohlen
Component.WebSocket | WebSocket4Net | Empfohlen
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake-Tools | Empfohlen
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | Empfohlen
Microsoft.Component.MSBuild | MSBuild | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | Empfohlen
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | Empfohlen
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | Empfohlen
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Empfohlen
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | Empfohlen
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | Empfohlen
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | Empfohlen
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | Empfohlen
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | Empfohlen
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | Empfohlen
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Empfohlen
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | Empfohlen
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | Empfohlen
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | Empfohlen
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | Empfohlen
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Empfohlen
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Empfohlen
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | Empfohlen
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Empfohlen
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Empfohlen
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | Empfohlen
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Empfohlen
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | Optional


## <a name="net-desktop-development"></a>.NET-Desktopentwicklung

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Beschreibung:** Erstellen von WPF-, Windows Forms- und Konsolenanwendungen mithilfe von .NET Framework.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | Erforderlich
Microsoft.Component.MSBuild | MSBuild | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time-Debugger | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET-Desktopentwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | Erforderlich
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | Empfohlen
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | Empfohlen
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | Profilerstellungstools | Empfohlen
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6-Tools | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | Empfohlen
Component.Dotfuscator | PreEmptive Protection – Dotfuscator | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | Optional
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1-Entwicklungstools | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 1.0 – 1.1-Entwicklungstools | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | Optional
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Optional
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | Optional


## <a name="game-development-with-unity"></a>Spieleentwicklung mit Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Beschreibung:** Erstellen Sie 2D- und 3D-Spiele mit Unity, einer leistungsfähigen plattformübergreifenden Entwicklungsumgebung.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Erforderlich
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools für Unity | Erforderlich
Component.UnityEngine | Unity-Editor | Empfohlen


## <a name="linux-development-with-c"></a>Linux-Entwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Beschreibung:** Erstellen und debuggen Sie Anwendungen, die in einer Linux-Umgebung ausgeführt werden.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Component.MDD.Linux | Visual C++ für die Linux-Entwicklung | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | Erforderlich


## <a name="desktop-development-with-c"></a>Desktopentwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Beschreibung:** Erstellen Sie klassische Windows-basierte Anwendungen mit dem leistungsfähigen Visual C++-Toolset, ATL und optionalen Features wie MFC und C++/CLI.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Erforderlich
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | Erforderlich
Microsoft.VisualStudio.Component.CodeMap | Code Map | Erforderlich
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time-Debugger | Erforderlich
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Erforderlich
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | Erforderlich
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Architekturtools für C++ | Erforderlich
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Wichtige Visual C++-Desktopfeatures | Erforderlich
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | Empfohlen
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafiktools Windows 8.1 SDK | Empfohlen
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Empfohlen
Microsoft.VisualStudio.Component.VC.CMake.Project | Visual C++-Tools für CMake | Empfohlen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | Empfohlen
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141-Toolset (x86, x64) | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Empfohlen
Component.Incredibuild | IncrediBuild | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Optional
Microsoft.VisualStudio.Component.VC.140 | Toolset für Visual C++ 2015.3 v140 (x86, x64) | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++-ATL-Unterstützung | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC- und ATL-Unterstützung (x86 und x64) | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimentell) | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++-/CLI-Unterstützung | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Standardbibliotheksmodule | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | Optional
Microsoft.VisualStudio.Component.WinXP | Windows XP-Unterstützung für C++ | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK und UCRT SDK | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Windows XP-Unterstützung für C++ | Optional


## <a name="game-development-with-c"></a>Spieleentwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Beschreibung:** Verwenden Sie die ganze Leistungsfähigkeit von C++ zum Erstellen professioneller Spiele mit DirectX, Unreal oder Cocos2d.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | Erforderlich
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | Empfohlen
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafiktools Windows 8.1 SDK | Empfohlen
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Empfohlen
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | Empfohlen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | Empfohlen
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141-Toolset (x86, x64) | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Empfohlen
Component.Cocos | Cocos | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.Unreal | Unreal Engine-Installer | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | Optional
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK und UCRT SDK | Optional


## <a name="mobile-development-with-c"></a>Mobile Entwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Beschreibung:** Erstellen Sie plattformübergreifende Anwendungen für iOS, Android oder Windows mithilfe von C++.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | Erforderlich
Component.Android.NDK.R13B | Android NDK (R13B) | Empfohlen
Component.Android.SDK19 | Android SDK-Setup (API-Ebene 19 und 21) | Empfohlen
Component.Android.SDK22 | Android SDK-Setup (API-Ebene 22) | Empfohlen
Component.Ant | Apache Ant (1.9.3) | Empfohlen
Component.MDD.Android | C++ Android-Entwicklungstools | Empfohlen
Component.Android.Emulator | Visual Studio-Emulator für Android | Optional
Component.Android.NDK.R11C | Android NDK (R11C) | Optional
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 Bit) | Optional
Component.Android.NDK.R12B | Android NDK (R12B) | Optional
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32 Bit) | Optional
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32 Bit) | Optional
Component.Android.SDK23 | Android SDK-Setup (API-Ebene 23) | Optional
Component.Google.Android.Emulator.API23.V2 | Google Android Emulator (API-Ebene 23) | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Optional
Component.MDD.IOS | C++ iOS-Entwicklungstools | Optional


## <a name="net-core-cross-platform-development"></a>Plattformübergreifende .NET Core-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Beschreibung:** Plattformübergreifende Anwendungsentwicklung mit .NET Core, ASP.NET, HTML, JavaScript und CSS

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Component.WebSocket | WebSocket4Net | Erforderlich
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | Erforderlich
Microsoft.Component.MSBuild | MSBuild | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | Erforderlich
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1-Entwicklungstools | Erforderlich
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 – 1.1-Entwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | Erforderlich
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Erforderlich
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | Empfohlen


## <a name="mobile-development-with-net"></a>Mobile Entwicklung mit .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Beschreibung:** Erstellen Sie plattformübergreifende Anwendungen für iOS, Android oder Windows mithilfe von Xamarin.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | Erforderlich
Component.Android.NDK.R13B | Android NDK (R13B) | Empfohlen
Component.Android.SDK23 | Android SDK-Setup (API-Ebene 23) | Empfohlen
Component.Google.Android.Emulator.API23.V2 | Google Android Emulator (API-Ebene 23) | Empfohlen
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Empfohlen
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Empfohlen
Component.Xamarin | Xamarin | Empfohlen
Component.Xamarin.Inspector | Xamarin Workbooks | Empfohlen
Component.Xamarin.Profiler | Xamarin Profiler | Empfohlen
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | Empfohlen
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Empfohlen
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Empfohlen
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | Optional
Microsoft.Component.NetFX.Native | .NET systemeigen | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Profilerstellungstools | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | Optional
Microsoft.VisualStudio.Component.Graphics | Bild- und 3D-Modell-Editoren | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 Mobile-Emulator (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | UWP-Tools für Xamarin (2.0) | Optional


## <a name="aspnet-and-web-development"></a>ASP.NET und Webentwicklung

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Beschreibung:** Erstellen von Webanwendungen mit ASP.NET, ASP.NET Core, HTML, JavaScript und CSS.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Component.WebSocket | WebSocket4Net | Erforderlich
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | Erforderlich
Microsoft.Component.MSBuild | MSBuild | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | Erforderlich
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1-Entwicklungstools | Erforderlich
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 – 1.1-Entwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | Erforderlich
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Erforderlich
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Erforderlich
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | Profilerstellungstools | Empfohlen
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | Empfohlen
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6-Tools | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | Empfohlen
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Empfohlen
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | Optional
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | Optional


## <a name="nodejs-development"></a>Node.js-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Node

**Beschreibung:** Erstellen Sie skalierbare Netzwerkanwendungen mit Node.js, einer asynchronen, ereignisgesteuerten JavaScript-Laufzeit.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | Erforderlich
Microsoft.VisualStudio.Component.Node.Tools | Node.js-Unterstützung | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Erforderlich
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | Empfohlen
Microsoft.VisualStudio.Component.Git | Git für Windows | Empfohlen
Component.WebSocket | WebSocket4Net | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Profilerstellungstools | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141-Toolset (x86, x64) | Optional


## <a name="officesharepoint-development"></a>Office/SharePoint-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Office

**Beschreibung:** Erstellen Sie Office- und SharePoint-Add-Ins, SharePoint-Lösungen und VSTO-Add-Ins mithilfe von C#, VB und JavaScript.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Component.WebSocket | WebSocket4Net | Erforderlich
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | Erforderlich
Microsoft.Component.MSBuild | MSBuild | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Erforderlich
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | Erforderlich
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time-Debugger | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET-Desktopentwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Erforderlich
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools für Visual Studio | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | Erforderlich
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Erforderlich
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | Erforderlich
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Erforderlich
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | Erforderlich
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools für Office (VSTO) | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Optional


## <a name="universal-windows-platform-development"></a>Entwicklung für die universelle Windows-Plattform

**ID:** Microsoft.VisualStudio.Workload.Universal

**Beschreibung:** Erstellen Sie Anwendungen für die universelle Windows-Plattform mit C#, VB, JavaScript oder optional mit C++.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Component.WebSocket | WebSocket4Net | Erforderlich
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | Erforderlich
Microsoft.Component.NetFX.Native | .NET systemeigen | Erforderlich
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Erforderlich
Microsoft.VisualStudio.Component.DiagnosticTools | Profilerstellungstools | Erforderlich
Microsoft.VisualStudio.Component.Graphics | Bild- und 3D-Modell-Editoren | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Erforderlich
Microsoft.VisualStudio.Component.UWP.Support | UWP-Tools (2.0) | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | UWP-Tools für Cordova (2.0) | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | UWP-Tools für Xamarin (2.0) | Erforderlich
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Empfohlen
Microsoft.Component.VC.Runtime.OSSupport | Visual C++ Runtime für UWP | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafiktools Windows 8.1 SDK | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 Mobile-Emulator (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Visual Studio C++-Compiler und -Bibliotheken für ARM | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141-Toolset (x86, x64) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | UWP-Tools für C++ | Optional


## <a name="visual-studio-extension-development"></a>Entwicklung von Visual Studio-Erweiterungen

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Beschreibung:** Erstellen Sie Add-Ons und Extensions für Visual Studio, z.B. neue Befehle, Codeanalysen und Toolfenster.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | Erforderlich
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Erforderliche Komponenten für die Visual Studio-Extensionentwicklung | Erforderlich
Microsoft.VisualStudio.Component.CodeClone | Codeklon | Empfohlen
Microsoft.VisualStudio.Component.CodeMap | Code Map | Empfohlen
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | Profilerstellungstools | Empfohlen
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Empfohlen
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Empfohlen
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Empfohlen
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | Empfohlen
Component.Dotfuscator | PreEmptive Protection – Dotfuscator | Optional
Microsoft.Component.MSBuild | MSBuild | Optional
Microsoft.Component.VC.Runtime.OSSupport | Visual C++ Runtime für UWP | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | Optional
Microsoft.VisualStudio.Component.DslTools | SDK für Modellierung | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Optional
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++-ATL-Unterstützung | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC- und ATL-Unterstützung (x86 und x64) | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141-Toolset (x86, x64) | Optional
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | Optional


## <a name="mobile-development-with-javascript"></a>Mobile Entwicklung mit JavaScript

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Beschreibung:** Erstellen Sie Android-, iOS- und UWP-Apps mithilfe von Tools für Apache Cordova.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Component.CordovaToolset.6.3.1 | Cordova 6.3.1-Toolset | Erforderlich
Component.WebSocket | WebSocket4Net | Erforderlich
Microsoft.VisualStudio.Component.Cordova | Mobile-Entwicklung mit JavaScript-Kernfeatures | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Erforderlich
Component.Android.SDK23 | Android SDK-Setup (API-Ebene 23) | Optional
Component.Google.Android.Emulator.API23.V2 | Google Android Emulator (API-Ebene 23) | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Optional
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Optional
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | Optional
Microsoft.Component.NetFX.Native | .NET systemeigen | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Profilerstellungstools | Optional
Microsoft.VisualStudio.Component.Git | Git für Windows | Optional
Microsoft.VisualStudio.Component.Graphics | Bild- und 3D-Modell-Editoren | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 Mobile-Emulator (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | UWP-Tools für Cordova (2.0) | Optional
## <a name="unaffiliated-components"></a>Nicht zugeordnete Komponenten

Dies sind Komponenten, die in keiner Arbeitsauslastung enthalten sind, jedoch als einzelne Komponenten ausgewählt werden können.

Komponenten-ID | Name
--- | ---
Component.GitHub.VisualStudio | GitHub-Erweiterung für Visual Studio
Microsoft.Component.Blend.SDK.WPF | Blend für Visual Studio SDK für .NET
Microsoft.Component.HelpViewer | Help Viewer
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5-Entwicklungstools
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL-Tools
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Test der codierten UI
Microsoft.VisualStudio.Component.TestTools.Core | Testtools für Kernfeatures
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Tools für Webleistung und Auslastungstests
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK


## <a name="see-also"></a>Siehe auch

* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
* [Administratorhandbuch für Visual Studio](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Erstellen einer Offlineinstallation von Visual Studio](create-an-offline-installation-of-visual-studio.md)

