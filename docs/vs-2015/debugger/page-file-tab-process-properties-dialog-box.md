---
title: Registerkarte "Auslagerungsdatei", im Dialogfeld "Eigenschaften" Process | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fa1eba7af60638d82c791958af6bf66a3272242
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522019"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Registerkarte "Auslagerungsdatei", Dialogfeld "Prozesseigenschaften"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Seite Registerkarte "Datei", im Dialogfeld "Eigenschaften" Process](https://docs.microsoft.com/visualstudio/debugger/page-file-tab-process-properties-dialog-box).  
  
Verwenden der **Auslagerungsdatei** Tab, um die Auslagerungsdatei eines Prozesses zu untersuchen. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), verschieben Sie den Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen stehen auf der **Auslagerungsdatei** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Bytes für Auslagerungsdatei**|Die aktuelle Anzahl der Seiten, die diesen Prozess in der Auslagerungsdatei verwendet wird. Die Auslagerungsdatei speichert Seiten mit Daten, die vom Prozess verwendet wird, aber nicht in anderen Dateien enthalten. Die Auslagerungsdatei wird von allen Prozessen verwendet, und nicht genügend Speicherplatz in der Auslagerungsdatei kann zu Fehlern führen, während andere Prozesse ausgeführt werden.|  
|**Maximale Bytes für Auslagerungsdatei**|Die maximale Anzahl der Seiten, die diesen Prozess in der Auslagerungsdatei verwendet wurde.|  
|**Seitenfehler**|Die Anzahl der Seitenfehler durch die in diesem Prozess ausgeführten Threads. Ein Seitenfehler tritt auf, wenn ein Thread auf eine Seite im virtuellen Speicher verweist, die nicht seinem Arbeitssatz im Hauptspeicher ist. Daher wird die Seite nicht vom Datenträger abgerufen, ist dies auf der Standbyliste und somit bereits im Hauptspeicher befindet oder wenn sie von einem anderen verwendet wird verarbeitet, mit denen die Seite freigegeben ist.|



