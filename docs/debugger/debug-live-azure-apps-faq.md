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
ms.openlocfilehash: 7ea593ad5f88ba29f6b1c0d7c64a129b8f71c7f5
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857073"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Häufig gestellte Fragen zum Debuggen von Momentaufnahmen in Visual Studio

Hier ist eine Liste der Fragen, die beim Debuggen aktiver Azure-Anwendungen mit dem Momentaufnahmedebugger aufkommen könnten.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Wie hoch sind die Leistungseinbußen bei einer Momentaufnahme?

Wenn der Momentaufnahmedebugger eine Momentaufnahme Ihrer App erfasst, verzweigt er den Prozess der App und setzt die verzweigte Kopie aus. Wenn Sie eine Momentaufnahme debuggen, debuggen Sie die verzweigte Kopie des Prozesses. Dieser Vorgang dauert nur 10 bis 20 Millisekunden, kopiert aber nicht den vollständigen Heap der App. Stattdessen kopiert er nur die Seitentabelle und legt Seiten für das Kopieren beim Schreibvorgang fest. Wenn einige Ihrer App-Objekte auf dem Heap geändert werden, werden die entsprechenden Seiten kopiert. Darum beansprucht jede Momentaufnahme etwas Arbeitsspeicher (bei den meisten Apps in der Größenordnung von ein paar hundert Kilobytes).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Was geschieht, wenn ich einen horizontal hochskalierten Azure App Service habe (mehrere Instanzen meiner App)?

Wenn Sie mehrere Instanzen Ihrer App haben, werden die Andockpunkte auf jede einzelne Instanz angewendet. Nur der erste mit den angegebenen Bedingungen zu erreichende Andockpunkt erstellt eine Momentaufnahme. Wenn Sie mehrere Andockpunkte haben, stammen spätere Momentaufnahmen von der gleichen Instanz, die die erste Momentaufnahme erstellt hat. An das Ausgabefenster gesendete Protokollpunkte zeigen nur Meldungen von einer Instanz an, während an Anwendungsprotokolle gesendete Protokollpunkte Meldungen von jeder Instanz senden.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Wie lädt der Momentaufnahmedebugger Symbole?

Der Momentaufnahmedebugger erfordert, dass Sie die entsprechenden Symbole für Ihre Anwendung entweder lokal oder für Ihren Azure App Service bereitgestellt haben. (Eingebettete PDB-Dateien werden derzeit nicht unterstützt.) Der Momentaufnahmedebugger lädt automatisch Symbole von Ihrem Azure App Service. Ab Visual Studio 2017 Version 15.2 werden mit der Bereitstellung für Azure App Service auch die Symbole Ihrer App bereitgestellt.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Arbeitet der Momentaufnahmedebugger mit Releasebuilds meiner Anwendung?

Ja, der Momentaufnahmedebugger soll mit Releasebuilds arbeiten. Wenn ein Andockpunkt in einer Funktion platziert wird, wird die Funktion zu einer Debugversion neu kompiliert und damit debugfähig. Beim Beenden des Momentaufnahmedebuggers werden die Funktionen auf die Version des Releasebuilds zurückgesetzt.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Können Protokollpunkte in meiner Produktionsanwendung Nebeneffekte verursachen?

Nein – jegliche Meldungen, die Sie Ihrer App hinzufügen, werden virtuell ausgewertet. Sie können keine Nebeneffekte in Ihrer Anwendung auslösen. Allerdings ist der Zugriff auf einige native Eigenschaften mit Protokollpunkten vielleicht nicht möglich.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Funktioniert der Momentaufnahmedebugger, wenn mein Server unter Last steht?

Ja, das Momentaufnahmedebuggen kann bei Servern unter Last funktionieren. Wenn nur eine geringe Menge freien Arbeitsspeichers auf dem Server vorhanden ist, wird der Momentaufnahmedebugger gedrosselt und erfasst keine Momentaufnahmen.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Wie deinstalliere ich den Momentaufnahmedebugger?

Sie können die Momentaufnahmedebugger-Websiteerweiterung mit den folgenden Schritten in Ihrem App Service deinstallieren:

1. Deaktivieren Sie Ihren App Service entweder über den Cloud-Explorer in Visual Studio oder im Azure-Portal.
1. Navigieren Sie zur Kudu-Website Ihres App Service (d.h. yourappservice.**scm**.azurewebsites.net), und navigieren Sie zu **Websiteerweiterungen**.
1. Klicken Sie auf das X der Momentaufnahmedebugger-Websiteerweiterung, um sie zu entfernen.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Warum werden während einer Momentaufnahmedebugger-Sitzung Ports geöffnet?

Der Momentaufnahmedebugger muss einen Satz von Ports öffnen, um die in Azure erstellten Momentaufnahmen zu debuggen. Hierbei handelt es sich um die gleichen Ports, die für das Remotedebuggen erforderlich sind. [Hier finden Sie die Liste der Ports](../debugger/remote-debugger-port-assignments.md).

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.md)
- [Debuggen von aktiven ASP.NET-Apps mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md)
- [Debuggen von aktiven ASP.NET Azure-VMs\-VMSS, die den Momentaufnahmedebugger verwenden](../debugger/debug-live-azure-virtual-machines.md)
- [Debuggen von aktiven ASP.NET Azure Kubernetes Services mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-kubernetes.md)
- [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-troubleshooting.md)