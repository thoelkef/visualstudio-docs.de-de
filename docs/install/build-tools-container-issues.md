---
title: Bekannte Probleme bei Containern
description: Informationen zu bekannten Problemen, die bei der Installation von Visual Studio Build Tools 2017 in einem Windows-Container auftreten können.
ms.custom: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c94c6756e1272b08136f624e9cde63523d630b35
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "43139144"
---
# <a name="known-issues-for-containers"></a>Bekannte Probleme bei Containern

Es gibt einige Probleme bei der Installation von Visual Studio in einem Docker-Container.

## <a name="windows-container"></a>Windows-Container

Die folgenden bekannten Probleme treten auf, wenn Sie Visual Studio Build Tools 2017 in einem Windows-Container installieren.

* Sie können Visual Studio nicht in einem Container basierend auf dem Image microsoft/windowsservercore:10.0.14393.1593 installieren. Images, die mit Windows-Versionen gekennzeichnet sind, die älter oder neuer sind, sollten funktionieren.
* Sie können Windows SDK-Versionen, die älter als 10.0.14393 sind, nicht installieren. Einige Pakete können nicht installiert werden, und Workloads, die von diesen Paketen abhängig sind, funktionieren nicht.
* Übergeben Sie `-m 2GB` (oder mehr), wenn Sie das Image erstellen. Einige Workloads erfordern bei der Installation mehr Arbeitsspeicher als die standardmäßigen 1 GB.
* Sie müssen Docker konfigurieren, damit Sie Datenträger verwenden können, die größer als die standardmäßig festgelegten 20 GB sind.
* Übergeben Sie `--norestart` auf der Befehlszeile. Beim Versuch, einen Windows-Container von innerhalb des Container neu zu starten, wird `ERROR_TOO_MANY_OPEN_FILES` an den Host zurückgegeben (Stand: Veröffentlichung dieses Artikels).
* Wenn Sie Ihr Image direkt auf der Grundlage von microsoft/windowsservercore erstellen, wird .NET Framework möglicherweise nicht ordnungsgemäß installiert, ohne dass ein Installationsfehler ausgegeben wird. Es kann sein, dass verwalteter Code nach Abschluss der Installation nicht ausgeführt wird. Erstellen Sie Ihr Image stattdessen auf der Grundlage von [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) oder höher. Beispielsweise tritt der folgende Fehler auf, wenn Sie mit MSBuild einen Build erstellen:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): error MSB6003: The specified task executable "csc.exe" could not be run. Could not load file or assembly 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies. (Fehler MSB6003: Die angegebene ausführbare Datei des Tasks (csc.exe) konnte nicht ausgeführt werden. Die Datei oder Assembly 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a', oder eine Abhängigkeit davon, wurde nicht gefunden.) Die angegebene Datei wurde nicht gefunden.“

## <a name="build-tools-container"></a>Build Tools-Container

Die folgenden bekannten Probleme treten möglicherweise auf, wenn Sie einen Build Tools-Container verwenden. Um festzustellen, ob Probleme behoben wurden oder ob es andere bekannte Probleme gibt, besuchen Sie die Website https://developercommunity.visualstudio.com.

* IntelliTrace funktioniert [in einigen Szenarios](https://github.com/Microsoft/vstest/issues/940) innerhalb eines Containers möglicherweise nicht.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Build Tools in einem Container](build-tools-container.md)
* [Erweitertes Beispiel für Container](advanced-build-tools-container.md)
* [Workload- und Komponenten-IDs in Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
