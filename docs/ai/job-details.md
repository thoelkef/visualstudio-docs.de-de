---
title: Anzeigen der zuletzt verwendeten Aufträge
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 55865e4907175664e8a8bfb8a813ff8d02c85b69
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638428"
---
# <a name="view-recent-job-performance-and-details"></a>Anzeigen aktueller Auftragsergebnisse und Details

Sobald die Aufträge übermittelt wurden, können Sie die Liste der Aufträge einsehen, um deren Status, Dauer und vieles mehr anzuzeigen.

1. Erweitern Sie im **Server-Explorer** den bestimmten Computekontext.
2. Doppelklicken Sie auf **Aufträge**.
3. Die Liste der an diesen Computekontext übermittelten Aufträge wird angezeigt.
4. Wählen Sie einen bestimmten **Auftrag** in der Liste aus, um Details anzuzeigen.

![Überwachen von Aufträgen](media/job-details/monitor-jobs.png)

> Der an Linux-VMs übermittelte Auftragsverlauf wird auf der VM im Verzeichnis „/tmp“ gespeichert. Daher wird bei jedem Neustart der Auftragsverlauf gelöscht. Für eine permanente Aufzeichnung Ihres Auftragsverlaufs konfigurieren Sie Ihre VM als Computekontext in Azure Machine Learning, und übermitteln Sie dann den Auftrag an Azure Machine Learning (wählen Sie dabei Ihre VM als Computekontext aus).
