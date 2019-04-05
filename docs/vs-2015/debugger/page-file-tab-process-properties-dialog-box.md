---
title: Registerkarte "Auslagerungsdatei", im Dialogfeld "Eigenschaften" Process | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24fdba37be2373623d94f03e45dc5e8a41a74b84
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958561"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Registerkarte "Auslagerungsdatei", Dialogfeld "Prozesseigenschaften"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden der **Auslagerungsdatei** Tab, um die Auslagerungsdatei eines Prozesses zu untersuchen. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), verschieben Sie den Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen stehen auf der **Auslagerungsdatei** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Bytes für Auslagerungsdatei**|Die aktuelle Anzahl der Seiten, die diesen Prozess in der Auslagerungsdatei verwendet wird. Die Auslagerungsdatei speichert Seiten mit Daten, die vom Prozess verwendet wird, aber nicht in anderen Dateien enthalten. Die Auslagerungsdatei wird von allen Prozessen verwendet, und nicht genügend Speicherplatz in der Auslagerungsdatei kann zu Fehlern führen, während andere Prozesse ausgeführt werden.|  
|**Max. Bytes für Auslagerungsdatei**|Die maximale Anzahl der Seiten, die diesen Prozess in der Auslagerungsdatei verwendet wurde.|  
|**Seitenfehler**|Die Anzahl der Seitenfehler durch die in diesem Prozess ausgeführten Threads. Ein Seitenfehler tritt auf, wenn ein Thread auf eine Seite im virtuellen Speicher verweist, die nicht seinem Arbeitssatz im Hauptspeicher ist. Daher wird die Seite nicht vom Datenträger abgerufen, ist dies auf der Standbyliste und somit bereits im Hauptspeicher befindet oder wenn sie von einem anderen verwendet wird verarbeitet, mit denen die Seite freigegeben ist.|
