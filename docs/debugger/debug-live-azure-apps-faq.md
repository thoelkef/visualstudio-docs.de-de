---
title: Häufig gestellte Fragen zum Debuggen von Momentaufnahmen | Microsoft-Dokumentation
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0899b70ce4a917b0479a9ac6623e33ee8bcdbe22
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335102"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Häufig gestellte Fragen zum Debuggen von Momentaufnahmen in Visual Studio

Hier ist eine Liste der Fragen, die beim Debuggen von aktiver Azure-Anwendungen, die mit dem Momentaufnahmedebugger kommen kann.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Was ist die Leistungseinbußen durch eine Momentaufnahme?

Bei der Snapshot-Debugger eine Momentaufnahme Ihrer App erfasst, forken den Prozess der app und das Anhalten der verzweigten Kopiervorgangs. Wenn Sie eine Momentaufnahme Debuggen, sind Sie mit der fork des Prozesses Debuggen. Dieser Vorgang dauert nur 10 bis 20 Millisekunden, aber nicht die vollständige Heapinformationen der app kopiert. Stattdessen wird nur die Seitentabelle kopiert und Seiten beim Schreiben kopiert. Wenn einige Ihrer app-Objekte, auf dem Heap geändert wird, werden die entsprechenden Seiten kopiert. Jede Momentaufnahme ist daher eine kleine in-Memory-Kosten (in der Größenordnung Hunderte von Kilobytes, die für die meisten apps). 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Was geschieht, wenn ich auf einer horizontal hochskalierten Azure App Service (mehrere Instanzen meiner App) habe?

Wenn Sie mehrere Instanzen Ihrer app haben, werden die andockpunkte auf jede einzelne Instanz angewendet. Nur der erste andockpunkt erreicht wird, mit der angegebenen Bedingungen wird eine Momentaufnahme erstellt. Wenn Sie mehrere andockpunkte haben, stammen nachfolgende Momentaufnahmen der gleichen Instanz, die die erste Momentaufnahme erstellt. Protokollpunkte gesendet, um das Fenster "Ausgabe" werden nur Nachrichten von einer Instanz angezeigt, während protokollpunkte gesendet, um die Anwendungsprotokolle von jeder Instanz Nachrichten zu senden. 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Laden der Momentaufnahmedebugger wie Symbole?

Die Snapshot-Debugger erfordert, dass Sie der entsprechenden Symbole in Ihrer Azure App Service für Ihre Anwendung entweder lokal oder bereitgestellt haben. (Eingebettete PDB-Dateien werden derzeit nicht unterstützt.) Der Momentaufnahmedebugger lädt automatisch die Symbole von Azure App Service. Ab Visual Studio 2017 stellt Version 15.2, auch in Azure App Service bereitstellen Ihrer app-Symbole bereit.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Werden der Momentaufnahmedebugger kann für Releasebuilds meiner Anwendung verwendet?

Ja, soll den Momentaufnahmedebugger Releasebuilds entgegenwirken. Wenn Sie ein andockpunkt in einer Funktion platziert wird, wird die Funktion an eine Debugversion, somit Debugfähige neu kompiliert werden. Wenn Sie die Snapshot-Debugger beenden, werden die Funktionen an ihre Releasebuild zurückgegeben. 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Können protokollpunkte in meiner produktionsanwendung Nebeneffekte verursachen?

Nein – werden alle Meldungen, die Sie Ihrer app hinzufügen, praktisch ausgewertet. Sie können nicht dazu führen, dass keine Nebeneffekte in Ihrer Anwendung. Allerdings können einige nativen Eigenschaften mit protokollpunkte nicht zugreifen. 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Werden der Momentaufnahmedebugger kann verwendet, wenn mein Server ausgelastet ist?

Ja, Debuggen von Momentaufnahmen für Server unter Last kann. Der Momentaufnahmedebugger drosselt und Momentaufnahmen unter Umständen nicht erfasst, wenn eine geringe Menge des freien Speicherplatzes auf dem Server vorhanden ist.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Wie deinstalliere ich den Momentaufnahmedebugger?

Sie können die websiteerweiterung des Momentaufnahmedebuggers in Ihrem App Service mit den folgenden Schritten deinstallieren:

1. Deaktivieren Sie Ihre App Service über den Cloud-Explorer in Visual Studio oder Azure-Portal.
1. Navigieren Sie zu Ihrer App Service Kudu-Website (d. h. Yourappservice. **SCM**. azurewebsites.net) und navigieren Sie zu **Websiteerweiterungen**.
1. Klicken Sie auf das X auf der websiteerweiterung des Momentaufnahmedebuggers, um ihn zu entfernen.

## <a name="see-also"></a>Siehe auch

[Debuggen in Visual Studio](../debugger/index.md)  
[Debug live ASP.NET-Apps, die mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md)  
[Debug live ASP.NET Azure virtuelle Machines\Virtual Computer Skalierungsgruppen mit der Snapshot-Debugger](../debugger/debug-live-azure-virtual-machines.md)  
[Debug live ASP.NET-Azure-Kubernetes, die mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-kubernetes.md)  
[Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-troubleshooting.md)
