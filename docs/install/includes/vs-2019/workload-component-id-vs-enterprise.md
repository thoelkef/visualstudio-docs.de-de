---
title: Workload- und Komponenten-IDs in Visual Studio Enterprise 2019
titleSuffix: ''
description: Verwenden Sie Arbeitsauslastungs- und Komponenten-IDs, um Visual Studio über die Befehlszeile zu installieren oder um sie als Abhängigkeit in einem VSIX-Manifest anzugeben
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 05/30/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: a9677097757650c3af66452a22ae3abd0dd4fe18
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68177656"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2019"></a>Visual Studio-Kern-Editor (in Visual Studio Enterprise 2019 enthalten)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Beschreibung:** Die Shell-Kernbenutzeroberfläche von Visual Studio, die syntaxfähige Codebearbeitung, Quellcodeverwaltung und Arbeitselementverwaltung bereitstellt.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio-Kern-Editor | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Visual Studio-Startseite für C++-Benutzer | 16.0.28315.86 | Optional

## <a name="azure-development"></a>Azure-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Azure

**Beschreibung:** Azure SDKs, Tools und Projekte zum Entwickeln von Cloud-Apps und für das Erstellen von Ressourcen und Containern (einschließlich Docker-Unterstützung).

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Erforderlich
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs-Tools | 16.0.28714.129 | Erforderlich
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.1.28811.260 | Erforderlich
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28516.191 | Erforderlich
Microsoft.NetCore.ComponentGroup.Web.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 16.1.28810.153 | Erforderlich
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#-Sprachunterstützung für Webprojekte | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Erforderliche Komponenten für die Azure-Entwicklung | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs-Tools | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.1.28812.146 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Erforderlich
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake und Stream Analytics-Tools | 16.1.28916.169 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 16.0.28516.191 | Empfohlen
Microsoft.VisualStudio.Component.AspNet45 | Erweiterte ASP.NET-Features | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio-Tools für Kubernetes | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager-Kerntools | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric-Tools | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services-Buildtools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Momentaufnahmedebugger | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Time Travel Debugger | 16.0.28714.129 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Cloud Services-Tools | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager-Tools | 16.0.28528.71 | Empfohlen
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional

## <a name="data-storage-and-processing"></a>Datenspeicherung und -verarbeitung

**ID:** Microsoft.VisualStudio.Workload.Data

**Beschreibung:** Hiermit werden Datenlösungen mit SQL Server, Azure Data Lake oder Hadoop verbunden, entwickelt und getestet.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Empfohlen
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Empfohlen
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake und Stream Analytics-Tools | 16.1.28916.169 | Empfohlen
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Empfohlen
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.1.28811.260 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 16.0.28516.191 | Empfohlen
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 16.1.28810.153 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services-Buildtools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.1.28811.260 | Empfohlen
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.0.28621.142 | Empfohlen
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.1.28811.260 | Empfohlen
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.1.28812.146 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Empfohlen
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | F#-Desktopsprachunterstützung | 16.0.28315.86 | Optional

## <a name="data-science-and-analytical-applications"></a>Data Science und analytische Anwendungen

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Beschreibung:** Sprachen und Tools zum Erstellen von Data Science-Anwendungen (einschließlich Python und F#).

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.PythonTools | Unterstützung der Sprache Python | 16.0.28625.61 | Empfohlen
Microsoft.Component.PythonTools.Minicondax64 | Python-Miniconda | 16.0.28625.61 | Empfohlen
Microsoft.Component.PythonTools.Web | Webunterstützung für Python | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.FSharp.Desktop | F#-Desktopsprachunterstützung | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.1.28811.260 | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Empfohlen
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Native Python-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 – VS 2015: C++-Buildtools (v14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional

## <a name="net-desktop-development"></a>.NET-Desktopentwicklung

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Beschreibung:** Erstellen von WPF-, Windows Forms- und Konsolenanwendungen mithilfe von C#, Visual Basic und F#.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.1.28811.260 | Erforderlich
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET-Desktopentwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Empfohlen
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 16.0.28516.191 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time-Debugger | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6-Tools | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Empfohlen
Component.Dotfuscator | PreEmptive Protection – Dotfuscator | 16.0.28528.71 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | F#-Desktopsprachunterstützung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.1.28811.260 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.1.28811.260 | Optional
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.1.28812.146 | Optional
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Optional

## <a name="game-development-with-unity"></a>Spieleentwicklung mit Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Beschreibung:** Erstellen Sie 2D- und 3D-Spiele mit Unity, einer leistungsfähigen plattformübergreifenden Entwicklungsumgebung.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5-Entwicklungstools | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools für Unity | 16.0.28315.86 | Erforderlich
Component.UnityEngine.x64 | Unity 2018.3-Editor (64 Bit) | 16.1.28810.153 | Empfohlen
Component.UnityEngine.x86 | Unity 5.6-Editor (32 Bit) | 16.1.28811.260 | Empfohlen

## <a name="linux-development-with-c"></a>Linux-Entwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Beschreibung:** Erstellen und debuggen Sie Anwendungen, die in einer Linux-Umgebung ausgeführt werden.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.MDD.Linux | C++ für die Linux-Entwicklung | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Erforderlich
Component.Linux.CMake | C++-CMake-Tools für Linux | 16.1.28916.169 | Empfohlen
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21) | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Empfohlen
Component.MDD.Linux.GCC.arm | Embedded-Tools und Tools für die IoT-Entwicklung | 16.1.28916.169 | Optional

## <a name="desktop-development-with-c"></a>Desktopentwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Beschreibung:** Erstellen Sie Windows-Desktopanwendungen mit dem Microsoft C++-Toolset, ATL oder MFC.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | 16.0.28528.71 | Erforderlich
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 Redistributable-Update | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Architekturtools für C++ | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Wichtige C++-Desktopfeatures | 16.1.28916.169 | Erforderlich
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time-Debugger | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.VC.ATL | C++-ATL für v142-Buildtools (x86 & x64) | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.VC.CMake.Project | C++-CMake-Tools für Windows | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Testadapter für Boost.Test | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Testadapter für Google Test | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21) | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Empfohlen
Component.Incredibuild | IncrediBuild – Buildbeschleunigung | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 – VS 2015: C++-Buildtools (v14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | C++ MFC für v142-Buildtools (x86 & x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.21) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.VC.Llvm.Clang | Clang-Compiler für Windows | 16.1.28916.169 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | C++-Module für v142-Buildtools (x64/x86 – experimentell) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86-Buildtools (v14.16) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional

## <a name="game-development-with-c"></a>Spieleentwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Beschreibung:** Verwenden Sie die volle Leistung von C++, um professionelle Spiele zu erstellen, die von DirectX, Unreal oder Cocos2D unterstützt werden.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 Redistributable-Update | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21) | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Empfohlen
Component.Android.NDK.R16B | Android NDK (R16B) | 16.1.28916.169 | Optional
Component.Android.SDK25.Private | Android SDK-Setup (API-Ebene 25, lokale Installation für die Mobile-Entwicklung mit C++) | 16.0.28625.61 | Optional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Optional
Component.Cocos | Cocos | 16.0.28315.86 | Optional
Component.Incredibuild | IncrediBuild – Buildbeschleunigung | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Component.MDD.Android | C++ Android-Entwicklungstools | 16.0.28517.75 | Optional
Component.OpenJDK | OpenJDK (Microsoft-Distribution) | 16.1.28811.260 | Optional
Component.Unreal | Unreal Engine-Installer | 16.1.28810.153 | Optional
Component.Unreal.Android | Unterstützung der Android-IDE für die Unreal-Engine | 16.1.28810.153 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.1.28811.260 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet-Ziele und Buildtasks | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional

## <a name="mobile-development-with-c"></a>Mobile Entwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Beschreibung:** Erstellen Sie mit C++ plattformübergreifende Anwendungen für iOS, Android oder Windows.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Android.SDK25.Private | Android SDK-Setup (API-Ebene 25, lokale Installation für die Mobile-Entwicklung mit C++) | 16.0.28625.61 | Erforderlich
Component.OpenJDK | OpenJDK (Microsoft-Distribution) | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.0.28625.61 | Erforderlich
Component.Android.NDK.R16B | Android NDK (R16B) | 16.1.28916.169 | Empfohlen
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Empfohlen
Component.MDD.Android | C++ Android-Entwicklungstools | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32 Bit) | 16.1.28916.169 | Optional
Component.Google.Android.Emulator.API25.Private | Google Android-Emulator (API-Ebene 25) (lokale Installation) | 16.1.28810.153 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM), lokale Installation | 16.0.28528.71 | Optional
Component.Incredibuild | IncrediBuild – Buildbeschleunigung | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Component.MDD.IOS | C++ iOS-Entwicklungstools | 16.0.28517.75 | Optional

## <a name="net-core-cross-platform-development"></a>Plattformübergreifende .NET Core-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Beschreibung:** Hiermit erstellen Sie plattformübergreifende Anwendungen mit .NET Core, ASP.NET Core, HTML, JavaScript und Containern mit Docker-Unterstützung.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Erforderlich
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.1.28811.260 | Erforderlich
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28516.191 | Erforderlich
Microsoft.NetCore.ComponentGroup.Web.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#-Sprachunterstützung für Webprojekte | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.1.28812.146 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Erforderlich
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Empfohlen
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs-Tools | 16.0.28714.129 | Empfohlen
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 16.1.28810.153 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Momentaufnahmedebugger | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Time Travel Debugger | 16.0.28714.129 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Empfohlen
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs-Tools | 16.0.28621.142 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudtools für die Webentwicklung | 16.0.28621.142 | Empfohlen
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Entwicklungszeit-IIS-Unterstützung | 16.0.28315.86 | Optional

## <a name="mobile-development-with-net"></a>Mobile Entwicklung mit .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Beschreibung:** Erstellen Sie mit Xamarin plattformübergreifende Anwendungen für iOS, Android oder Windows.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (Microsoft-Distribution) | 16.1.28811.260 | Erforderlich
Component.Xamarin | Xamarin | 16.1.28810.153 | Erforderlich
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.0.28315.86 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.1.28811.260 | Erforderlich
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28516.191 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.Merq | Häufig verwendete interne Xamarin-Tools | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.MonoDebugger | Mono-Debugger | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET-Vorlagen-Engine | 16.0.28315.86 | Erforderlich
Component.Android.SDK27 | Android SDK-Setup (API-Ebene 27) | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen

## <a name="aspnet-and-web-development"></a>ASP.NET und Webentwicklung

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Beschreibung:** Hiermit erstellen Sie Webanwendungen mit ASP.NET, ASP.NET Core, HTML, JavaScript und Container mit Docker-Unterstützung.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Erforderlich
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.1.28811.260 | Erforderlich
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28516.191 | Erforderlich
Microsoft.NetCore.ComponentGroup.Web.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#-Sprachunterstützung für Webprojekte | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.1.28812.146 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Erforderlich
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Empfohlen
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs-Tools | 16.0.28714.129 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 16.0.28516.191 | Empfohlen
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Empfohlen
Microsoft.VisualStudio.Component.AspNet45 | Erweiterte ASP.NET-Features | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 16.1.28810.153 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Momentaufnahmedebugger | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Time Travel Debugger | 16.0.28714.129 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6-Tools | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs-Tools | 16.0.28621.142 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudtools für die Webentwicklung | 16.0.28621.142 | Empfohlen
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | .NET Core 2.2-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Tools für Webleistung und Auslastungstests | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Zusätzliche Projektvorlagen (frühere Versionen) | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Entwicklungszeit-IIS-Unterstützung | 16.0.28315.86 | Optional

## <a name="nodejs-development"></a>Node.js-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Node

**Beschreibung:** Erstellen Sie skalierbare Netzwerkanwendungen mithilfe von Node.js, einer asynchronen, ereignisgesteuerten JavaScript-Runtime. 

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.Node.Tools | Node.js-Entwicklungstools | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Erforderlich
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21) | 16.1.28829.92 | Optional

## <a name="officesharepoint-development"></a>Office/SharePoint-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Office

**Beschreibung:** Erstellen Sie Office- und SharePoint-Add-Ins, SharePoint-Lösungen und VSTO-Add-Ins mithilfe von C#, VB und JavaScript.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Erforderlich
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.1.28811.260 | Erforderlich
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET-Desktopentwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools für Visual Studio | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.1.28812.146 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools für Office (VSTO) | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Optional
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Optional

## <a name="python-development"></a>Python-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Python

**Beschreibung:** Bearbeiten, Debuggen, interaktive Entwicklung und Quellcodeverwaltung für Python.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.PythonTools | Unterstützung der Sprache Python | 16.0.28625.61 | Erforderlich
Component.CPython3.x64 | Python 3 64-Bit (3.7.3) | 3.7.3 | Empfohlen
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Empfohlen
Microsoft.Component.PythonTools.Minicondax64 | Python-Miniconda | 16.0.28625.61 | Empfohlen
Microsoft.Component.PythonTools.Web | Webunterstützung für Python | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.1.28811.260 | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.0.28621.142 | Empfohlen
Component.CPython2.x64 | Python 2, 64 Bit (2.7.16) | 2.7.16 | Optional
Component.CPython2.x86 | Python 2, 32 Bit (2.7.16) | 2.7.16 | Optional
Component.CPython3.x86 | Python 3, 32 Bit (3.7.3) | 3.7.3 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Optional
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Native Python-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.1.28811.260 | Optional
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 16.1.28810.153 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services-Buildtools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.1.28811.260 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 – VS 2015: C++-Buildtools (v14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.1.28812.146 | Optional

## <a name="universal-windows-platform-development"></a>Entwicklung für die universelle Windows-Plattform

**ID:** Microsoft.VisualStudio.Workload.Universal

**Beschreibung:** Hiermit erstellen Sie Anwendungen für die Universelle Windows-Plattform mit C#, VB oder optional C++.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET systemeigen | 16.0.28315.86 | Erforderlich
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Erforderlich
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Entwicklungstools | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Erforderlich
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.Graphics | Bild- und 3D-Modell-Editoren | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native und .NET Standard | 16.0.28516.191 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.Support | UWP-Tools (Universelle Windows-Plattform) | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | UWP-Tools für Xamarin | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Empfohlen
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | 16.0.28528.71 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | C++-Unterstützung für die Universelle Windows-Plattform für v142-Buildtools (ARM64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 Redistributable-Update | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 - VS 2019: C++-ARM-Buildtools (v14.21) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 - VS 2019 C++ ARM64-Buildtools (v14.21) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 - VS 2017 C++ ARM-Buildtools (v14.16) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ ARM64-Buildtools (v14.16) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86-Buildtools (v14.16) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | USB-Gerätekonnektivität | 16.0.28320.51 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Architekturtools für C++ | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Wichtige C++-Desktopfeatures | 16.1.28916.169 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | UWP-Tools (Universelle Windows-Plattform) für C++ (v142) | 16.1.28811.260 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | UWP-Tools (Universelle Windows-Plattform) für C++ (v141) | 16.1.28810.153 | Optional

## <a name="visual-studio-extension-development"></a>Entwicklung von Visual Studio-Erweiterungen

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Beschreibung:** Erstellen Sie Add-Ons und Erweiterungen für Visual Studio, z. B. neue Befehle, Codeanalysetools und Toolfenster.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Erforderliche Komponenten für die Visual Studio-Extensionentwicklung | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Empfohlen
Component.Dotfuscator | PreEmptive Protection – Dotfuscator | 16.0.28528.71 | Optional
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK | 16.0.28625.61 | Optional
Microsoft.Component.VC.Runtime.OSSupport | C++-Runtime für die Universelle Windows-Plattform für v142-Buildtools | 16.1.28811.260 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | 16.0.28528.71 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DslTools | SDK für Modellierung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATL | C++-ATL für v142-Buildtools (x86 & x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | C++ MFC für v142-Buildtools (x86 & x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 16.0.28621.142 | Optional

## <a name="unaffiliated-components"></a>Nicht zugeordnete Komponenten

Dies sind Komponenten, die in keiner Arbeitsauslastung enthalten sind, jedoch als einzelne Komponenten ausgewählt werden können.

Komponenten-ID | name | Version
--- | --- | ---
Component.GitHub.VisualStudio | GitHub-Erweiterung für Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 16.0.28707.177
Microsoft.Component.HelpViewer | Help Viewer | 16.0.28625.61
Microsoft.NetCore.1x.ComponentGroup.Web | Entwicklungstools von .NET Core 1.0 – 1.1 für Web | 16.0.28621.142
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Azure DevOps-Integration in Office | 16.0.28625.61
Microsoft.VisualStudio.Component.Git | Git für Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL-Tools | 16.0.28625.61
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Test der codierten UI | 16.0.28327.66
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ ARM-Buildtools (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - VS 2019: C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ ARM64-Buildtools (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - VS 2019: C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL | C++ v14.20 ATL für v142-Buildtools (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | C++ v14.20 ATL für v142-Buildtools (ARM) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | C++ v14.20 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | C++ v14.20 ATL für v142-Buildtools (ARM64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | C++ v14.20 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | C++ v14.20 ATL für v142-Buildtools mit Spectre-Entschärfungen (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.MFC | C++ v14.20 MFC für v142-Buildtools (x86 & x64) | 16.1.28916.169
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | C++ v14.20 MFC für v142-Buildtools (ARM) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | C++ v14.20 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | C++ v14.20 MFC für v142-Buildtools (ARM64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | C++ v14.20 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | C++ v14.20 MFC für v142-Buildtools mit Spectre-Entschärfungen (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.ATL.ARM | C++-ATL für v142-Buildtools (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | C++-ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | C++-ATL für v142-Buildtools (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C++-ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++-ATL für v142-Buildtools mit Spectre-Entschärfungen (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++ MFC für v142-Buildtools mit Spectre-Entschärfungen (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM | C++ MFC für v142-Buildtools (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++ MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++ MFC für v142-Buildtools (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C++ MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Redist.MSM | C++ 2019 Redistributable-MSMs | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 - VS 2019: C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.21) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 - VS 2019: C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.21) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 - VS 2019: C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.21)  | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 - VS 2017: C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 - VS 2017: C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.ATL | C++-ATL für v141-Buildtools (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | C++-ATL für v141-Buildtools (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | C++-ATL für v141-Buildtools mit Spectre-Entschärfungen (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | C++-ATL für v141-Buildtools (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | C++-ATL für v141-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | C++-ATL für v141-Buildtools mit Spectre-Entschärfungen (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | C++-/CLI-Unterstützung für v141-Buildtools (14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.MFC | C++ MFC für v141-Buildtools (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | C++ MFC für v141-Buildtools (ARM) | 16.1.28916.169
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | C++ MFC für v141-Buildtools mit Spectre-Entschärfungen (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++ MFC für v141-Buildtools (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | C++ MFC für v141-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | C++ MFC für v141-Buildtools mit Spectre-Entschärfungen (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 - VS 2017: C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | C++-Windows XP-Unterstützung für Tools in VS 2017 (v141) [veraltet] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
