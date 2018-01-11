---
title: Bekannte Probleme bei Containern | Microsoft-Dokumentation
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: heaths
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6edcc59a2d726fbd76fee86b750f21dc468b727e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="known-issues-for-containers"></a>Bekannte Probleme bei Containern

Es gibt einige Probleme bei der Installation von Visual Studio in einem Docker-Container.

## <a name="windows-container"></a>Windows-Container

Die folgenden bekannten Probleme treten auf, wenn Sie Visual Studio Build Tools 2017 in einem Windows-Container installieren.

* Sie können Visual Studio nicht in einem Container basierend auf dem Image microsoft/windowsservercore:10.0.14393.1593 installieren. Images, die mit Windows-Versionen gekennzeichnet sind, die älter oder neuer sind, sollten funktionieren.
* Sie können Windows SDK-Versionen, die älter als 10.0.14393 sind, nicht installieren. Einige Pakete können nicht installiert werden, und Workloads, die von diesen Paketen abhängig sind, funktionieren nicht.
* Sie müssen `-m 2GB` (oder mehr) übergeben, wenn Sie das Image erstellen. Einige Workloads erfordern bei der Installation mehr Arbeitsspeicher als die standardmäßigen 1 GB.
* Sie müssen Docker konfigurieren, damit Sie Datenträger verwenden können, die größer als die standardmäßigen 20 GB sind.
* Sie müssen `--norestart` über die Befehlszeile übergeben. Beim Versuch, einen Windows-Container von innerhalb des Container neu zu starten, wird `ERROR_TOO_MANY_OPEN_FILES` an den Host zurückgegeben (Stand: Veröffentlichung dieses Artikels).

## <a name="build-tools-container"></a>Build Tools-Container

Die folgenden bekannten Probleme treten möglicherweise auf, wenn Sie einen Build Tools-Container verwenden. Um festzustellen, ob Probleme behoben wurden oder ob es andere bekannte Probleme gibt, besuchen Sie die Website https://developercommunity.visualstudio.com.

* IntelliTrace funktioniert [in einigen Szenarios](https://github.com/Microsoft/vstest/issues/940) innerhalb eines Containers möglicherweise nicht.

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:
* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden.
* Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen.  (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

* [Installieren von Build Tools in einem Container](build-tools-container.md)
* [Erweitertes Beispiel für Container](advanced-build-tools-container.md)
* [Workload- und Komponenten-IDs in Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
