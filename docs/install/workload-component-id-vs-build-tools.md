---
title:
- Arbeitsauslastungs- und Komponenten-IDs in Visual Studio Build Tools 2017 | Microsoft-Dokumentation
description: Verwenden von Arbeitsauslastungs- und Komponenten-IDs in Visual Studio zum Erstellen klassischer Windows-basierter Anwendungen
keywords: 
author:
- TerryGLee
ms.author:
- tglee
manager:
- ghogen
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
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
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
ms.openlocfilehash: 230d04f93e8e857fc0dbaf018e56567259ac6c38
ms.lasthandoff: 03/07/2017

---

# <a name="visual-studio-build-tools-2017-component-directory"></a>Visual Studio Build Tools 2017-Komponentenverzeichnis

In den Tabellen auf dieser Seite sind die IDs aufgeführt, die Sie verwenden können, um Visual Studio über die Befehlszeile zu installieren. Beachten Sie, dass weitere Komponenten hinzugefügt werden, wenn wir Updates für Visual Studio veröffentlichen.

Beachten Sie zudem Folgendes im Hinblick auf diese Seite:

* Für jede Arbeitsauslastung gibt es einen eigenen Abschnitt, gefolgt von der Arbeitsauslastungs-ID und einer Tabelle der Komponenten, die für die Arbeitsauslastung zur Verfügung stehen.
* Die **erforderlichen** Komponenten werden standardmäßig bei der Installation der Arbeitsauslastung installiert. Bei Bedarf können Sie auch die **empfohlenen** und **optionalen** Komponenten installieren.
* Wir haben auch einen Abschnitt hinzugefügt, in dem die zusätzlichen Komponenten aufgeführt sind, die keiner Arbeitsauslastung zugeordnet sind.

Weitere Informationen zur Verwendung dieser IDs finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Eine Liste der Arbeitsauslastungs- und Komponenten-IDs für andere Produkte finden Sie auf der Seite [Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017](workload-and-component-ids.md).

## <a name="msbuild-tools"></a>MSBuild-Tools

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**Beschreibung:** Stellt die erforderlichen Tools zum Erstellen von MSBuild-basierten Anwendungen bereit.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Erforderlich
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools, Core | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | Erforderlich


## <a name="visual-c-build-tools"></a>Visual C++ Build Tools

**ID:** Microsoft.VisualStudio.Workload.VCTools

**Beschreibung:** Erstellen Sie klassische Windows-basierte Anwendungen mit dem leistungsfähigen Visual C++-Toolset, ATL und optionalen Features wie MFC und C++/CLI.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Visual C++ Build Tools Kernfunktionen | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | Erforderlich
Microsoft.VisualStudio.Component.VC.CMake.Project | Visual C++-Tools für CMake | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Empfohlen
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++-ATL-Unterstützung | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC- und ATL-Unterstützung (x86 und x64) | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimentell) | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++-/CLI-Unterstützung | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++-Kernfeatures | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Standardbibliotheksmodule | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141-Toolset (x86, x64) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK und UCRT SDK | Optional


## <a name="web-development-build-tools"></a>Development Build

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**Beschreibung:** MSBuild-Aufgaben und -Ziele zum Erstellen von Webanwendungen.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Abhängigkeitstyp
--- | --- | ---
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Development Build | Erforderlich
## <a name="unaffiliated-components"></a>Nicht zugeordnete Komponenten

Dies sind Komponenten, die in keiner Arbeitsauslastung enthalten sind, jedoch als einzelne Komponenten ausgewählt werden können.

Komponenten-ID | Name
--- | ---
n/v | n/v


## <a name="see-also"></a>Siehe auch

* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
* [Administratorhandbuch für Visual Studio](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Erstellen einer Offlineinstallation von Visual Studio](create-an-offline-installation-of-visual-studio.md)

