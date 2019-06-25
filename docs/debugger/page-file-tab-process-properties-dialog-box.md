---
title: Registerkarte "Auslagerungsdatei", im Dialogfeld "Eigenschaften" Process | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25dc3b0aca1b58c18ae4038540c14fc4dbfe4036
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904106"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Registerkarte "Auslagerungsdatei", Dialogfeld "Prozesseigenschaften"
Verwenden der **Auslagerungsdatei** Tab, um die Auslagerungsdatei eines Prozesses zu untersuchen. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), verschieben Sie den Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.

 Die folgenden Einstellungen stehen auf der **Auslagerungsdatei** Registerkarte:

|Eingabe|Beschreibung|
|-----------|-----------------|
|**Bytes für Auslagerungsdatei**|Die aktuelle Anzahl der Seiten, die diesen Prozess in der Auslagerungsdatei verwendet wird. Die Auslagerungsdatei speichert Seiten mit Daten, die vom Prozess verwendet wird, aber nicht in anderen Dateien enthalten. Die Auslagerungsdatei wird von allen Prozessen verwendet, und nicht genügend Speicherplatz in der Auslagerungsdatei kann zu Fehlern führen, während andere Prozesse ausgeführt werden.|
|**Max. Bytes für Auslagerungsdatei**|Die maximale Anzahl der Seiten, die diesen Prozess in der Auslagerungsdatei verwendet wurde.|
|**Seitenfehler**|Die Anzahl der Seitenfehler durch die in diesem Prozess ausgeführten Threads. Ein Seitenfehler tritt auf, wenn ein Thread auf eine Seite im virtuellen Speicher verweist, die nicht seinem Arbeitssatz im Hauptspeicher ist. Daher wird die Seite nicht vom Datenträger abgerufen, ist dies auf der Standbyliste und somit bereits im Hauptspeicher befindet oder wenn sie von einem anderen verwendet wird verarbeitet, mit denen die Seite freigegeben ist.|