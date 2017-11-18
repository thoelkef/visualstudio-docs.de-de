---
title: Registerkarte "Auslagerungsdatei", Prozess-Eigenschaftendialogfeld | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bf5215e7a6d4c4a4a0dac37a9bde2b15fb8f19a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Registerkarte "Auslagerungsdatei", Dialogfeld "Prozesseigenschaften"
Verwenden der **Auslagerungsdatei** Tab, um die Auslagerungsdatei eines Prozesses zu untersuchen. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), Verschieben des Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen sind verfügbar, auf die **Auslagerungsdatei** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Auslagerungsdatei-Bytes**|Die aktuelle Anzahl der Seiten, die diesen Prozess in der Auslagerungsdatei verwendet wird. Die Auslagerungsdatei speichert Datenseiten vom Prozess verwendet wird, aber nicht in anderen Dateien enthalten. Die Auslagerungsdatei wird von allen Prozessen verwendet, und nicht genügend Speicherplatz in der Auslagerungsdatei kann zu Fehlern führen, während andere Prozesse ausgeführt werden.|  
|**Peak Auslagerungsdatei Bytes**|Die maximale Anzahl der Seiten, die diesen Prozess in der Auslagerungsdatei verwendet hat.|  
|**Seitenfehler**|Die Anzahl der Seitenfehler durch die in diesem Prozess ausgeführten Threads. Ein Seitenfehler tritt auf, wenn ein Thread auf eine virtuelle Speicherseite verweist, die nicht in seinem Arbeitssatz im Hauptspeicher befindet. Daher wird die Seite nicht vom Datenträger abgerufen, ist er auf der Standbyliste und somit bereits im Hauptspeicher befindet oder wenn sie durch eine andere verwendet wird verarbeitet, mit denen die Seite freigegeben ist.|