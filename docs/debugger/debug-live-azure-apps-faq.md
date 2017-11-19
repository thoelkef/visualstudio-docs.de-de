---
title: "Häufig gestellte Fragen zur Momentaufnahme Debuggen | Microsoft Docs"
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c62269cacff6fc456d99219a5317de97c0a0ee0
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Häufig gestellte Fragen für die Momentaufnahme Debuggen in Visual Studio

Hier ist eine Liste von Fragen, die beim Debuggen von live Azure-Anwendungen, die mit dem Debugger Momentaufnahme auftreten kann.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Was ist die Leistungskosten für eine Momentaufnahme erstellen?

Wenn der Momentaufnahme-Debugger eine Momentaufnahme Ihrer App erfasst, Verzweigung der app-Prozess und bis zum Anhalten der verzweigter kopieren. Beim Debuggen einer Momentaufnahme werden Sie anhand der verzweigter Kopie des Prozesses Debuggen. Dieser Vorgang dauert nur 10 bis 20 Millisekunden jedoch nicht die vollständige Heap der app kopiert; Stattdessen wird nur auf die Seitentabelle kopiert und Seiten beim Schreiben kopiert. Wenn ein Teil der app-Objekte auf dem Heap geändert wird, werden die entsprechenden Seiten kopiert. Jede Momentaufnahme ist daher sehr kleine Kosten im Arbeitsspeicher (in der Größenordnung Hunderte von Kilobytes bei den meisten apps). 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Was geschieht, wenn ich eine dezentral skalierte Azure App Service (mehrere Instanzen der app) habe?

Wenn Sie mehrere Instanzen der app haben, erhalten Snappoints auf jede einzelne Instanz angewendet. Nur der erste Snappoint drückt, und geben Sie die Bedingungen angegeben, wird eine Momentaufnahme erstellt. Wenn Sie mehrere Snappoints haben, kommen nachfolgenden Momentaufnahmen über dieselbe Instanz, die die erste Momentaufnahme erstellt. Logpoints gesendet, um das Fenster "Ausgabe" zeigt nur Nachrichten von einer Instanz beim Senden von Nachrichten gesendet, um die Anwendungsprotokolle Logpoints aus jeder Instanz. 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Laden der Momentaufnahme-Debugger wie Symbole?

Der Momentaufnahme-Debugger erfordert, dass Sie der entsprechenden Symbole für Ihre Anwendung entweder lokal oder in Ihren Azure App Service (eingebettete PDB-Dateien sind derzeit nicht unterstützt) bereitgestellt. Der Momentaufnahme-Debugger wird automatisch Symbole aus Ihren Azure App Service heruntergeladen. Ab Visual Studio 2017 stellt Version 15.2, auch nach Azure App Service bereitstellen Ihrer app Symbole bereit.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Funktioniert der Momentaufnahme-Debugger für Releasebuilds meine Anwendung?

Ja – dient der Momentaufnahme-Debugger für Releasebuilds arbeiten. Wenn eine Snappoint in einer Funktion platziert wird, wird die Funktion an eine Debugversion somit debugfähig neu kompiliert. Wenn Sie den Momentaufnahme-Debugger beenden, werden die Funktionen an ihre Releasebuild zurückgegeben. 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Können Logpoints Nebeneffekte in der produktionsanwendung verursachen?

Nein – werden alle protokollmeldungen, die Sie Ihrer app hinzufügen praktisch ausgewertet. Sie können keine Nebeneffekte in der Anwendung führen. Allerdings können einige nativen Eigenschaften mit Logpoints nicht verfügbar. 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Funktioniert der Momentaufnahme-Debugger, wenn mein Server ausgelastet ist?

Ja, Momentaufnahme Debuggen für Server unter Last kann. Der Momentaufnahme-Debugger drosselt und erfasst keine Momentaufnahmen in Situationen, in dem eine niedrige Menge des freien Speicherplatzes auf dem Server vorhanden ist.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Wie deinstallieren kann ich den Momentaufnahme-Debugger?

Sie können die Snapshot-Debuggererweiterung Standort für Ihren App-Dienst mit den folgenden Schritten deinstallieren:

1. Deaktivieren Sie Ihren App Service entweder über die Cloud-Explorer in Visual Studio oder Azure-Portal.
1. Navigieren Sie zu Ihren Anwendungsdienst Kudu-Website (d. h. Yourappservice. **SCM**. azurewebsites.net) und navigieren Sie zu **Site Erweiterungen**.
1. Klicken Sie auf das X auf der Snapshot-Debugger websiteerweiterung um ihn zu entfernen.

## <a name="see-also"></a>Siehe auch

[Debuggen in Visual Studio](../debugger/index.md)  
[Debuggen von Livedaten ASP.NET-apps, die mit dem Momentaufnahme-Debugger](../debugger/debug-live-azure-applications.md)  
[Problembehandlung und bekannte Probleme für das Debuggen der Momentaufnahme](../debugger/debug-live-azure-apps-troubleshooting.md)
