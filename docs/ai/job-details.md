---
title: Anzeigen der zuletzt verwendeten Aufträge
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 79b396946666077dcdedb3ee2a5ab891c2bb4fb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "72777396"
---
# <a name="view-recent-job-performance-and-details"></a>Anzeigen aktueller Auftragsergebnisse und Details

Sobald die Aufträge übermittelt wurden, können Sie die Liste der Aufträge einsehen, um deren Status, Dauer und vieles mehr anzuzeigen.

1. Erweitern Sie im **Server-Explorer** den bestimmten Computekontext.
2. Doppelklicken Sie auf **Aufträge**.
3. Die Liste der an diesen Computekontext übermittelten Aufträge wird angezeigt.
4. Wählen Sie einen bestimmten **Auftrag** in der Liste aus, um Details anzuzeigen.

![Überwachen von Aufträgen](media/job-details/monitor-jobs.png)

> Der an Linux-VMs übermittelte Auftragsverlauf wird auf der VM im Verzeichnis „/tmp“ gespeichert. Daher wird bei jedem Neustart der Auftragsverlauf gelöscht. Für eine permanente Aufzeichnung Ihres Auftragsverlaufs konfigurieren Sie Ihre VM als Computekontext in Azure Machine Learning, und übermitteln Sie dann den Auftrag an Azure Machine Learning (wählen Sie dabei Ihre VM als Computekontext aus).
