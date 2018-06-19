---
title: Workload- und Komponenten-IDs in Visual Studio Enterprise 2017
description: Verwenden Sie Arbeitsauslastungs- und Komponenten-IDs, um Visual Studio über die Befehlszeile zu installieren oder um sie als Abhängigkeit in einem VSIX-Manifest anzugeben
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 05/07/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: be73e3af-d87b-4d14-bd08-2e4bda074fb3
ms.workload:
- multiple
ms.openlocfilehash: 74d10f671f392965579283a276908ce4e5859ed7
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33865576"
---
# <a name="visual-studio-enterprise-2017-component-directory"></a>Visual Studio Enterprise 2017-Komponentenverzeichnis

In den Tabellen auf dieser Seite sind die IDs aufgeführt, die Sie verwenden können, um Visual Studio über die Befehlszeile zu installieren, oder die Sie als Abhängigkeit in einem VSIX-Manifest angeben können. Beachten Sie, dass weitere Komponenten hinzugefügt werden, wenn wir Updates für Visual Studio veröffentlichen.

Beachten Sie zudem Folgendes im Hinblick auf die Seite:

* Für jede Arbeitsauslastung gibt es einen eigenen Abschnitt, gefolgt von der Arbeitsauslastungs-ID und einer Tabelle der Komponenten, die für die Arbeitsauslastung zur Verfügung stehen.
* Die **erforderlichen** Komponenten werden standardmäßig bei der Installation der Arbeitsauslastung installiert.
* Bei Bedarf können Sie auch die **empfohlenen** und **optionalen** Komponenten installieren.
* Wir haben auch einen Abschnitt hinzugefügt, in dem die zusätzlichen Komponenten aufgeführt sind, die keiner Arbeitsauslastung zugeordnet sind.

Wenn Sie Abhängigkeiten im VSIX-Manifest festlegen, müssen Sie nur Komponenten-IDs angeben. Verwenden Sie die Tabellen auf dieser Seite, um die minimalen Komponentenabhängigkeiten zu bestimmen. In einigen Fällen könnte dies bedeuten, dass Sie nur eine Komponente einer Arbeitsauslastung angeben. In anderen Fällen könnte dies bedeuten, dass Sie mehrere Komponenten einer einzelnen Arbeitsauslastung oder mehrere Komponenten von mehreren Arbeitsauslastungen angeben. Weitere Informationen finden Sie auf der Seite [Gewusst wie: Migrieren von Erweiterungsprojekten zu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Weitere Informationen zur Verwendung dieser IDs finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Eine Liste der Arbeitsauslastungs- und Komponenten-IDs für andere Produkte finden Sie auf der Seite [Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017](workload-and-component-ids.md).

## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2017"></a>Visual Studio-Kern-Editor (in Visual Studio Enterprise 2017 enthalten)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Beschreibung:** Die Shell-Kernbenutzeroberfläche von Visual Studio, die syntaxfähige Codebearbeitung, Quellcodeverwaltung und Arbeitselementverwaltung bereitstellt.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio-Kern-Editor | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Visual Studio-Startseite für C++-Benutzer | 15.0.27128.1 | Optional

## <a name="azure-development"></a>Azure-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Azure

**Beschreibung:** Azure SDKs, Tools und Projekte zum Entwickeln von Cloud-Apps und für das Erstellen von Ressourcen und Containern, Docker-Unterstützung eingeschlossen.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 15.0.26720.2 | Erforderlich
Component.Microsoft.VisualStudio.Web.AzureFunctions | Microsoft Azure WebJobs-Tools | 15.7.27617.1 | Erforderlich
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Erforderlich
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Erforderlich
Microsoft.Component.NetFX.Core.Runtime | .NET Core-Runtime | 15.0.26208.0 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.Net.Core.Component.SDK | .NET Core 2.0-Entwicklungstools | 15.6.27406.0 | Erforderlich
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 2.0-Entwicklungstools | 15.7.27617.1 | Erforderlich
Microsoft.NetCore.ComponentGroup.Web | .NET Core 2.0-Entwicklungstools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 15.0.26621.2 | Erforderlich
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 15.0.26621.2 | Erforderlich
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 15.6.27413.0 | Erforderlich
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 1.10.50912.1 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Containerentwicklungstools – Buildtools | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 15.7.27604.0 | Erforderlich
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#-Sprachunterstützung für Webprojekte | 15.7.27703.1 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 15.6.27323.2 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 15.0.26621.2 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Erforderliche Komponenten für die Azure-Entwicklung | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Microsoft Azure WebJobs-Tools | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Erforderlich
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake und Stream Analytics-Tools | 15.7.27604.0 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 15.6.27406.0 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.AspNet45 | Erweiterte ASP.NET-Features | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure Mobile Apps SDK | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager-Kerntools | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric-Tools | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services-Buildtools | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Momentaufnahmedebugger | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 15.7.27512.0 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.6.27323.2 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Cloud Services-Tools | 15.0.26504.0 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager-Tools | 15.0.27005.2 | Empfohlen
Component.PowerShellTools.VS2017 | PowerShell-Tools | 3.0.552 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 – 1.1-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.NetCore.1x.ComponentGroup.Web | Entwicklungstools von .NET Core 1.0 – 1.1 für Web | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.7.27604.0 | Optional

## <a name="data-storage-and-processing"></a>Datenspeicherung und -verarbeitung

**ID:** Microsoft.VisualStudio.Workload.Data

**Beschreibung:** Verbinden, Entwickeln und Testen von Datenlösungen mit SQL Server, Azure Data Lake oder Hadoop.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 15.0.26720.2 | Empfohlen
Component.Redgate.ReadyRoll | Redgate ReadyRoll Core | 1.14.17.5347 | Empfohlen
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt Core | 8.2.5.2924 | Empfohlen
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 2.4.2.1439 | Empfohlen
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Empfohlen
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake und Stream Analytics-Tools | 15.7.27604.0 | Empfohlen
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Empfohlen
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 15.6.27406.0 | Empfohlen
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.7.27520.0 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Core.Component.SDK | .NET Core 2.0-Entwicklungstools | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 15.0.26621.2 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 15.0.26621.2 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 15.6.27413.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services-Buildtools | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 1.10.50912.1 | Empfohlen
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Containerentwicklungstools – Buildtools | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 15.6.27323.2 | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Empfohlen
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 15.6.27309.0 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Empfohlen
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 15.0.26621.2 | Empfohlen
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Empfohlen
Microsoft.VisualStudio.Component.FSharp.Desktop | F#-Desktopsprachunterstützung | 15.7.27604.0 | Optional

## <a name="data-science-and-analytical-applications"></a>Data Science und analytische Anwendungen

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Beschreibung:** Sprachen und Tools zum Erstellen von Data Science-Anwendungen, einschließlich Python, R und F#.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Anaconda3.x64 | Anaconda3 64-Bit (5.1.0) | 5.1.0 | Empfohlen
Microsoft.Component.CookiecutterTools | Unterstützung von Cookiecutter-Vorlagen | 15.0.26621.2 | Empfohlen
Microsoft.Component.PythonTools | Unterstützung der Sprache Python | 15.0.26823.1 | Empfohlen
Microsoft.Component.PythonTools.Web | Webunterstützung für Python | 15.0.27005.2 | Empfohlen
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 1.10.50912.1 | Empfohlen
Microsoft.VisualStudio.Component.FSharp.Desktop | F#-Desktopsprachunterstützung | 15.7.27604.0 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Empfohlen
Microsoft.VisualStudio.Component.R.Open | Microsoft R Client (3.3.2) | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.RHost | Laufzeitunterstützung für R-Entwicklungstools | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Empfohlen
Microsoft.VisualStudio.Component.RTools | Unterstützung der Sprache R | 15.0.26919.1 | Empfohlen
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Empfohlen
Component.Anaconda2.x64 | Anaconda2 64-Bit (5.1.0) | 5.1.0 | Optional
Component.Anaconda2.x86 | Anaconda2 32-Bit (5.1.0) | 5.1.0 | Optional
Component.Anaconda3.x86 | Anaconda3 32-Bit (5.1.0) | 5.1.0 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Native Python-Entwicklungstools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafiktools Windows 8.1 SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | VC++ 2015.3, Version 14.00 (v140) – Toolset für Desktop | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Neueste v141-Tools in VC++ 2017, Version 15.7 v14.14 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Optional

## <a name="net-desktop-development"></a>.NET-Desktopentwicklung

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Beschreibung:** Erstellen von WPF-, Windows Forms- und Konsolenanwendungen mithilfe von C#, Visual Basic und F#.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 15.6.27323.2 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET-Desktopentwicklungstools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Erforderlich
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 15.6.27406.0 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time-Debugger | 15.0.27005.2 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 15.7.27512.0 | Empfohlen
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6-Tools | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.6.27323.2 | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Empfohlen
Component.Dotfuscator | PreEmptive Protection – Dotfuscator | 15.0.26208.0 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 15.0.26720.2 | Optional
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK | .NET Core 2.0-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 – 1.1-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 2.0-Entwicklungstools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 1.10.50912.1 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 15.7.27520.0 | Optional
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Containerentwicklungstools – Buildtools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 15.7.27604.0 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | F#-Desktopsprachunterstützung | 15.7.27604.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 15.0.27005.2 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 15.7.27520.0 | Optional
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Optional
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.7.27604.0 | Optional
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 15.7.27520.0 | Optional
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 15.7.27625.0 | Optional
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Optional

## <a name="game-development-with-unity"></a>Spieleentwicklung mit Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Beschreibung:** Erstellen Sie 2D- und 3D-Spiele mit Unity, einer leistungsfähigen plattformübergreifenden Entwicklungsumgebung.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5-Entwicklungstools | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools für Unity | 15.7.27617.1 | Erforderlich
Component.UnityEngine.x64 | Unity 2017.2-Editor (64 Bit) | 15.6.27406.0 | Empfohlen
Component.UnityEngine.x86 | Unity 5.6-Editor (32 Bit) | 15.6.27406.0 | Empfohlen

## <a name="linux-development-with-c"></a>Linux-Entwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Beschreibung:** Erstellen und debuggen Sie Anwendungen, die in einer Linux-Umgebung ausgeführt werden.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.MDD.Linux | Visual C++ für die Linux-Entwicklung | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Erforderlich
Component.Linux.CMake | Visual C++-Tools für CMake und Linux | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Neueste v141-Tools in VC++ 2017, Version 15.7 v14.14 | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Empfohlen
Component.MDD.Linux.GCC.arm | Eingebettete und IoT-Entwicklung | 15.6.27309.0 | Optional

## <a name="desktop-development-with-c"></a>Desktopentwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Beschreibung:** Erstellen Sie Windows-Desktopanwendungen mit dem Microsoft C++-Toolset, ATL oder MFC.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 15.0.27005.2 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Visual C++ 2017 Redistributable Update | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Architekturtools für C++ | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Wichtige Visual C++-Desktopfeatures | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time-Debugger | 15.0.27005.2 | Empfohlen
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafiktools Windows 8.1 SDK | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Empfohlen
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.VC.ATL | Visual C++-ATL für x86 und x64 | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.Component.VC.CMake.Project | Visual C++-Tools für CMake | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 15.0.26823.1 | Empfohlen
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Testadapter für Boost.Test | 15.6.27309.0 | Empfohlen
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Testadapter für Google Test | 15.6.27309.0 | Empfohlen
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Neueste v141-Tools in VC++ 2017, Version 15.7 v14.14 | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Empfohlen
Component.Incredibuild | IncrediBuild – Buildbeschleunigung | 15.7.27617.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | VC++ 2015.3, Version 14.00 (v140) – Toolset für Desktop | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++-MFC für x86 und x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++-/CLI-Unterstützung | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Module für die Standardbibliothek (experimentell) | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) für Desktop C++ [x86 und x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) für UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) für UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) für Desktop C++ [x86 und x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) für UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) für UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.WinXP | Windows XP-Unterstützung für C++ | 15.7.27703.1 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK und UCRT SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Windows XP-Unterstützung für C++ | 15.7.27703.1 | Optional

## <a name="game-development-with-c"></a>Spieleentwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Beschreibung:** Verwenden Sie die ganze Leistungsfähigkeit von C++ zum Erstellen professioneller Spiele mit DirectX, Unreal oder Cocos2d.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Visual C++ 2017 Redistributable Update | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Neueste v141-Tools in VC++ 2017, Version 15.7 v14.14 | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafiktools Windows 8.1 SDK | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 15.0.26823.1 | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Empfohlen
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.9 | Optional
Component.Android.SDK23.Private | Android SDK-Setup (API-Ebene 23, lokale Installation für die Mobile-Entwicklung mit JavaScript/C++) | 15.7.27703.1 | Optional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.7 | Optional
Component.Cocos | Cocos | 15.0.26906.1 | Optional
Component.Incredibuild | IncrediBuild – Buildbeschleunigung | 15.7.27617.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | Optional
Component.MDD.Android | C++ Android-Entwicklungstools | 15.0.26606.0 | Optional
Component.Unreal | Unreal Engine-Installer | 15.6.27406.0 | Optional
Component.Unreal.Android | Visual Studio-Android-Unterstützung für Unreal Engine | 15.0.27005.2 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.7.27520.0 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) für Desktop C++ [x86 und x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) für UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) für UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) für Desktop C++ [x86 und x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) für UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) für UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK und UCRT SDK | 15.6.27406.0 | Optional

## <a name="mobile-development-with-c"></a>Mobile Entwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Beschreibung:** Erstellen Sie plattformübergreifende Anwendungen für iOS, Android oder Windows mithilfe von C++.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Android.SDK19.Private | Android SDK-Setup (API-Ebene 19, lokale Installation für die Mobile-Entwicklung mit JavaScript/C++) | 15.7.27703.1 | Erforderlich
Component.Android.SDK21.Private | Android SDK-Setup (API-Ebene 21, lokale Installation für die Mobile-Entwicklung mit JavaScript/C++) | 15.7.27703.1 | Erforderlich
Component.Android.SDK22.Private | Android SDK-Setup (API-Ebene 22, lokale Installation für die Mobile-Entwicklung mit JavaScript/C++) | 15.7.27703.1 | Erforderlich
Component.Android.SDK23.Private | Android SDK-Setup (API-Ebene 23, lokale Installation für die Mobile-Entwicklung mit JavaScript/C++) | 15.7.27703.1 | Erforderlich
Component.Android.SDK25.Private | Android SDK-Setup (API-Ebene 25, lokale Installation für die Mobile-Entwicklung mit JavaScript/C++) | 15.7.27703.1 | Erforderlich
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | 15.6.27406.0 | Erforderlich
Component.Android.NDK.R15C | Android NDK (R15C) | 15.2 | Empfohlen
Component.Ant | Apache Ant (1.9.3) | 1.9.3.7 | Empfohlen
Component.MDD.Android | C++ Android-Entwicklungstools | 15.0.26606.0 | Empfohlen
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.9 | Optional
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32 Bit) | 12.1.10 | Optional
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.6 | Optional
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32 Bit) | 13.1.7 | Optional
Component.Android.NDK.R15C_3264 | Android NDK (R15C) (32 Bit) | 15.2 | Optional
Component.Google.Android.Emulator.API23.Private | Google Android-Emulator (API-Ebene 23), lokale Installation | 15.6.27413.0 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM), lokale Installation | 15.6.27413.0 | Optional
Component.Incredibuild | IncrediBuild – Buildbeschleunigung | 15.7.27617.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional
Component.MDD.IOS | C++ iOS-Entwicklungstools | 15.0.26621.2 | Optional

## <a name="net-core-cross-platform-development"></a>Plattformübergreifende .NET Core-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Beschreibung:** Plattformübergreifende Anwendungsentwicklungen mit .NET Core, ASP.NET Core, HTML/JavaScript und Containern einschließlich Docker-Unterstützung.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 15.0.26720.2 | Erforderlich
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Erforderlich
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.Net.Core.Component.SDK | .NET Core 2.0-Entwicklungstools | 15.6.27406.0 | Erforderlich
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 2.0-Entwicklungstools | 15.7.27617.1 | Erforderlich
Microsoft.NetCore.ComponentGroup.Web | .NET Core 2.0-Entwicklungstools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 1.10.50912.1 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Containerentwicklungstools – Buildtools | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 15.7.27604.0 | Erforderlich
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#-Sprachunterstützung für Webprojekte | 15.7.27703.1 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 15.6.27323.2 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 15.0.26621.2 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Erforderlich
Component.Microsoft.VisualStudio.Web.AzureFunctions | Microsoft Azure WebJobs-Tools | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 15.0.26621.2 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 15.0.26621.2 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 15.6.27413.0 | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Momentaufnahmedebugger | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 15.7.27512.0 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.6.27323.2 | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Empfohlen
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Microsoft Azure WebJobs-Tools | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudtools für die Webentwicklung | 15.7.27520.0 | Empfohlen
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 – 1.1-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.NetCore.1x.ComponentGroup.Web | Entwicklungstools von .NET Core 1.0 – 1.1 für Web | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Entwicklungszeit-IIS-Unterstützung | 15.7.27520.0 | Optional

## <a name="mobile-development-with-net"></a>Mobile Entwicklung mit .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Beschreibung:** Erstellen Sie plattformübergreifende Anwendungen für iOS, Android oder Windows mithilfe von Xamarin.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Xamarin | Xamarin | 15.7.27617.1 | Erforderlich
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 15.6.27323.2 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.Net.Core.Component.SDK | .NET Core 2.0-Entwicklungstools | 15.6.27406.0 | Erforderlich
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 2.0-Entwicklungstools | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 15.7.27604.0 | Erforderlich
Microsoft.VisualStudio.Component.Merq | Häufig verwendete interne Xamarin-Tools | 15.0.26720.2 | Erforderlich
Microsoft.VisualStudio.Component.MonoDebugger | Mono-Debugger | 15.0.26720.2 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET-Vorlagen-Engine | 15.6.27323.2 | Erforderlich
Component.Android.SDK27 | Android SDK-Setup (API-Ebene 27) | 15.7.27625.0 | Empfohlen
Component.Google.Android.Emulator.API27 | Google Android-Emulator (API-Ebene 27) | 15.7.27625.0 | Empfohlen
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM), globale Installation | 15.6.27413.0 | Empfohlen
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | Empfohlen
Component.Xamarin.Inspector | Xamarin Workbooks | 15.0.26606.0 | Empfohlen
Component.Xamarin.Profiler | Xamarin Profiler | 15.0.27005.2 | Empfohlen
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Optional
Microsoft.Component.NetFX.Native | .NET systemeigen | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 15.7.27512.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 15.0.27005.2 | Optional
Microsoft.VisualStudio.Component.Graphics | Bild- und 3D-Modell-Editoren | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | UWP-Tools für Xamarin | 15.7.27617.1 | Optional

## <a name="aspnet-and-web-development"></a>ASP.NET und Webentwicklung

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Beschreibung:** Erstellen von Webanwendungen mit ASP.NET, ASP.NET Core, HTML/JavaScript und Containern einschließlich Docker-Unterstützung.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 15.0.26720.2 | Erforderlich
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Erforderlich
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.Net.Core.Component.SDK | .NET Core 2.0-Entwicklungstools | 15.6.27406.0 | Erforderlich
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 2.0-Entwicklungstools | 15.7.27617.1 | Erforderlich
Microsoft.NetCore.ComponentGroup.Web | .NET Core 2.0-Entwicklungstools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 1.10.50912.1 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Containerentwicklungstools – Buildtools | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 15.7.27604.0 | Erforderlich
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#-Sprachunterstützung für Webprojekte | 15.7.27703.1 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 15.6.27323.2 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 15.0.26621.2 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Erforderlich
Component.Microsoft.VisualStudio.Web.AzureFunctions | Microsoft Azure WebJobs-Tools | 15.7.27617.1 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 15.6.27406.0 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 15.6.27406.0 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.AspNet45 | Erweiterte ASP.NET-Features | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 15.0.26621.2 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 15.0.26621.2 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 15.6.27413.0 | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Momentaufnahmedebugger | 15.7.27625.0 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 15.7.27512.0 | Empfohlen
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6-Tools | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.6.27323.2 | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Empfohlen
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.7.27604.0 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Microsoft Azure WebJobs-Tools | 15.7.27617.1 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudtools für die Webentwicklung | 15.7.27520.0 | Empfohlen
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 – 1.1-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.NetCore.1x.ComponentGroup.Web | Entwicklungstools von .NET Core 1.0 – 1.1 für Web | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 15.0.27005.2 | Optional
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Tools für Webleistung und Auslastungstests | 15.7.27520.0 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Entwicklungszeit-IIS-Unterstützung | 15.7.27520.0 | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.6.27406.0 | Optional

## <a name="nodejs-development"></a>Node.js-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Node

**Beschreibung:** Erstellen Sie skalierbare Netzwerkanwendungen mit Node.js, einer asynchronen, ereignisgesteuerten JavaScript-Laufzeit.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.Node.Build | Node.js-Unterstützung | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Node.Tools | Node.js-Unterstützung | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.TestTools.Core | Testtools für Kernfeatures | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 1.10.50912.1 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Neueste v141-Tools in VC++ 2017, Version 15.7 v14.14 | 15.7.27625.0 | Optional

## <a name="officesharepoint-development"></a>Office/SharePoint-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Office

**Beschreibung:** Erstellen Sie Office- und SharePoint-Add-Ins, SharePoint-Lösungen und VSTO-Add-Ins mithilfe von C#, VB und JavaScript.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 15.0.26720.2 | Erforderlich
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Erforderlich
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 15.6.27406.0 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.Net.Core.Component.SDK | .NET Core 2.0-Entwicklungstools | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 1.10.50912.1 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Containerentwicklungstools – Buildtools | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 15.6.27323.2 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET-Desktopentwicklungstools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Erforderlich
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools für Visual Studio | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 15.0.26621.2 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.7.27604.0 | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.0.27005.2 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Erforderlich
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools für Office (VSTO) | 15.7.27625.0 | Empfohlen
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.6.27323.2 | Optional

## <a name="python-development"></a>Python-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Python

**Beschreibung:** Bearbeiten, Debuggen, interaktive Entwicklung und Quellcodeverwaltung für Python.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.PythonTools | Unterstützung der Sprache Python | 15.0.26823.1 | Erforderlich
Component.CPython3.x64 | Python 3 64-Bit (3.6.5) | 3.6.5 | Empfohlen
Microsoft.Component.CookiecutterTools | Unterstützung von Cookiecutter-Vorlagen | 15.0.26621.2 | Empfohlen
Microsoft.Component.PythonTools.Web | Webunterstützung für Python | 15.0.27005.2 | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 1.10.50912.1 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Empfohlen
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Empfohlen
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Empfohlen
Component.Anaconda2.x64 | Anaconda2 64-Bit (5.1.0) | 5.1.0 | Optional
Component.Anaconda2.x86 | Anaconda2 32-Bit (5.1.0) | 5.1.0 | Optional
Component.Anaconda3.x64 | Anaconda3 64-Bit (5.1.0) | 5.1.0 | Optional
Component.Anaconda3.x86 | Anaconda3 32-Bit (5.1.0) | 5.1.0 | Optional
Component.CPython2.x64 | Python 2 64-Bit (2.7.14) | 2.7.14 | Optional
Component.CPython2.x86 | Python 2 32-Bit (2.7.14) | 2.7.14 | Optional
Component.CPython3.x86 | Python 3 32-Bit (3.6.5) | 3.6.5 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 15.0.26720.2 | Optional
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Optional
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Optional
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Optional
Microsoft.Component.NetFX.Native | .NET systemeigen | 15.0.26208.0 | Optional
Microsoft.Component.PythonTools.UWP | Python IoT-Unterstützung | 15.0.26606.0 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Native Python-Entwicklungstools | 15.7.27617.1 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.7.27520.0 | Optional
Microsoft.Net.Core.Component.SDK | .NET Core 2.0-Entwicklungstools | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 15.6.27413.0 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | 15.7.27520.0 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services-Buildtools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 15.7.27512.0 | Optional
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 15.7.27520.0 | Optional
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Containerentwicklungstools – Buildtools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 15.0.27005.2 | Optional
Microsoft.VisualStudio.Component.Graphics | Bild- und 3D-Modell-Editoren | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafiktools Windows 8.1 SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.6.27323.2 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 15.7.27520.0 | Optional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 15.6.27323.2 | Optional
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | VC++ 2015.3, Version 14.00 (v140) – Toolset für Desktop | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Neueste v141-Tools in VC++ 2017, Version 15.7 v14.14 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 15.7.27520.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 15.7.27625.0 | Optional

## <a name="universal-windows-platform-development"></a>Entwicklung für die universelle Windows-Plattform

**ID:** Microsoft.VisualStudio.Workload.Universal

**Beschreibung:** Erstellen Sie Anwendungen für die universelle Windows-Plattform mit C#, VB, JavaScript oder optional mit C++.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Erforderlich
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Erforderlich
Microsoft.Component.NetFX.Native | .NET systemeigen | 15.0.26208.0 | Erforderlich
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Erforderlich
Microsoft.Net.Core.Component.SDK | .NET Core 2.0-Entwicklungstools | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 15.7.27512.0 | Erforderlich
Microsoft.VisualStudio.Component.Graphics | Bild- und 3D-Modell-Editoren | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.UWP.Support | UWP-Tools (Universelle Windows-Plattform) | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | UWP-Tools für Cordova | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native und .NET Standard | 15.7.27512.0 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | UWP-Tools für Xamarin | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Erforderlich
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.6.27323.2 | Empfohlen
Microsoft.Component.VC.Runtime.OSSupport | Visual C++ Runtime für UWP | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 15.0.27005.2 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafiktools Windows 8.1 SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Windows 10 Mobile-Emulator (Fall Creators Update) | 15.0.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Visual Studio C++-Compiler und -Bibliotheken für ARM | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Neueste v141-Tools in VC++ 2017, Version 15.7 v14.14 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) für UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) für UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | USB-Gerätekonnektivität | 15.7.27625.0 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | UWP-Tools für C++ | 15.7.27617.1 | Optional

## <a name="visual-studio-extension-development"></a>Entwicklung von Visual Studio-Erweiterungen

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Beschreibung:** Erstellen Sie Add-Ons und Extensions für Visual Studio, z.B. neue Befehle, Codeanalysen und Toolfenster.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 15.6.27406.0 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.0.27205.0 | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 15.0.26919.1 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Erforderliche Komponenten für die Visual Studio-Extensionentwicklung | 15.7.27625.0 | Erforderlich
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 15.7.27512.0 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.6.27323.2 | Empfohlen
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 15.0.26208.0 | Empfohlen
Component.Dotfuscator | PreEmptive Protection – Dotfuscator | 15.0.26208.0 | Optional
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK | 15.0.27323.2 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Visual C++ Runtime für UWP | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DslTools | SDK für Modellierung | 15.0.27005.2 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 15.0.27005.2 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++-ATL für x86 und x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++-MFC für x86 und x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Neueste v141-Tools in VC++ 2017, Version 15.7 v14.14 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 15.0.26208.0 | Optional

## <a name="mobile-development-with-javascript"></a>Mobile Entwicklung mit JavaScript

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Beschreibung:** Erstellen Sie Android-, iOS- und UWP-Apps mithilfe von Tools für Apache Cordova.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Cordova 6.3.1-Toolset | 15.7.27625.0 | Erforderlich
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Erforderlich
Microsoft.VisualStudio.Component.Cordova | Mobile-Entwicklung mit JavaScript-Kernfeatures | 15.0.26606.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript Project System und gemeinsam genutzte Tools | 15.0.26606.0 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 15.7.27520.0 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 15.0.27005.2 | Erforderlich
Component.Android.SDK23.Private | Android SDK-Setup (API-Ebene 23, lokale Installation für die Mobile-Entwicklung mit JavaScript/C++) | 15.7.27703.1 | Optional
Component.Google.Android.Emulator.API23.Private | Google Android-Emulator (API-Ebene 23), lokale Installation | 15.6.27413.0 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM), lokale Installation | 15.6.27413.0 | Optional
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | Optional
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.7.27520.0 | Optional
Microsoft.Component.NetFX.Native | .NET systemeigen | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 15.7.27512.0 | Optional
Microsoft.VisualStudio.Component.Git | Git für Windows | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics | Bild- und 3D-Modell-Editoren | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Windows 10 Mobile-Emulator (Fall Creators Update) | 15.0.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | UWP-Tools für Cordova | 15.7.27617.1 | Optional

## <a name="unaffiliated-components"></a>Nicht zugeordnete Komponenten

Dies sind Komponenten, die in keiner Arbeitsauslastung enthalten sind, jedoch als einzelne Komponenten ausgewählt werden können.

Komponenten-ID | name | Version
--- | --- | ---
Component.Android.Emulator | Visual Studio-Emulator für Android | 15.6.27413.0
Component.Android.NDK.R11C | Android NDK (R11C) | 11.3.13
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 Bit) | 11.3.15
Component.Android.SDK23 | Android SDK-Setup (API-Ebene 23), globale Installation | 15.6.27413.0
Component.Android.SDK25 | Android SDK-Setup (API-Ebene 25) | 15.6.27413.0
Component.GitHub.VisualStudio | GitHub-Erweiterung für Visual Studio | 2.2.0.10
Component.Google.Android.Emulator.API23.V2 | Google Android-Emulator (API-Ebene 23), globale Installation | 15.6.27413.0
Component.Google.Android.Emulator.API25 | Google Android-Emulator (API-Ebene 25) | 15.7.27604.0
Microsoft.Component.Blend.SDK.WPF | Blend für Visual Studio SDK für .NET | 15.6.27406.0
Microsoft.Component.HelpViewer | Help Viewer | 15.6.27323.2
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL-Tools | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 Mobile-Emulator (Anniversary Edition) | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Windows 10 Mobile-Emulator (Creators Update) | 15.6.27406.0
Microsoft.VisualStudio.Component.Runtime.Node.x86.6.4.0 | Runtime für Komponenten auf Grundlage von Node.js v6.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.Runtime.Node.x86.7.4.0 | Runtime für Komponenten auf Grundlage von Node.js v7.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Test der codierten UI | 15.0.26606.0
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript 2.6 SDK | 15.0.27520.0
Microsoft.VisualStudio.Component.TypeScript.2.7 | TypeScript 2.7 SDK | 15.0.27617.1
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | C++ Universal Windows Platform-Tools für ARM64 | 15.0.27617.1
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++-ATL für ARM mit Spectre-Entschärfungen | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++-ATL für ARM64 mit Spectre-Entschärfungen | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++-ATL (x86/x64) mit Spectre-Entschärfungen | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++-MFC für x86/x64 mit Spectre-Entschärfungen | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimentell) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Visual C++-MFC für ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++-MFC für ARM mit Spectre-Entschärfungen | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Visual C++-MFC für ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Visual C++-MFC-Unterstützung für ARM64 mit Spectre-Entschärfungen | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | Bibliotheken von VC++ 2017, Version 15.7 v14.14, für Spectre (ARM) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | Bibliotheken von VC++ 2017, Version 15.7 v14.14, für Spectre (ARM64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | Bibliotheken von VC++ 2017, Version 15.7 v14.14, für Spectre (x86 und x64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Tools.14.11 | VC++ 2017, Version 15.4, Toolset 14.11 | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | VC++ 2017, Version 15.5, Toolset v14.12 | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | VC++ 2017, Version 15.6, Toolset v14.13 | 15.0.27625.0
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Visual C++-Compiler und -Bibliotheken für ARM64 | 15.6.27309.0
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) für Desktop C++ [ARM und ARM64] | 15.6.27406.0

## <a name="get-support"></a>Support aufrufen

Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten und Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/) finden.
* Sie können auch über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen. (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Beispiele für Befehlszeilenparameter](command-line-parameter-examples.md)
* [Erstellen einer Offlineinstallation von Visual Studio](create-an-offline-installation-of-visual-studio.md)
