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
ms.openlocfilehash: 06da94f4f2920aa7ce87822482a762a1451e9acb
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282495"
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

## <a name="get-support"></a>Support aufrufen

Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://visualstudio.microsoft.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten und Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/) finden.
* Sie können auch über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen. (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

* [Installieren von Build Tools in einem Container](build-tools-container.md)
* [Erweitertes Beispiel für Container](advanced-build-tools-container.md)
* [Workload- und Komponenten-IDs in Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
