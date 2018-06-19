---
ms.technology: vs-ai-tools
ms.openlocfilehash: f11a66fd06a2b0b3b23d35c3153c5dd26fab282e
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
ms.locfileid: "29709830"
---
# <a name="view-recent-job-performance-and-details"></a>Anzeigen aktueller Auftragsergebnisse und Details
Sobald die Aufträge übermittelt wurden, können Sie die Liste der Aufträge einsehen, um deren Status, Dauer und vieles mehr anzuzeigen.

1. Erweitern Sie im **Server-Explorer** den bestimmten Computekontext.
1. Doppelklicken Sie auf **Aufträge**.
1. Die Liste der an diesen Computekontext übermittelten Aufträge wird angezeigt.
1. Wählen Sie einen bestimmten **Auftrag** in der Liste aus, um Details anzuzeigen.

![Überwachen von Aufträgen](media\job-details\monitor-jobs.png)

> Der an Linux-VMs übermittelte Auftragsverlauf wird auf der VM im Verzeichnis „/tmp“ gespeichert. Daher wird bei jedem Neustart der Auftragsverlauf gelöscht. Für eine permanente Aufzeichnung Ihres Auftragsverlaufs konfigurieren Sie Ihre VM als Computekontext in Azure Machine Learning, und bermitteln Sie dann den Auftrag an Azure Machine Learning (wählen Sie dabei Ihre VM als Computekontext aus).