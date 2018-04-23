---
title: Registerkarte "Auslagerungsdatei", Prozess-Eigenschaftendialogfeld | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 624be76badf8d57b060198c2ee910ead17b5efcb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Registerkarte "Auslagerungsdatei", Dialogfeld "Prozesseigenschaften"
Verwenden der **Auslagerungsdatei** Tab, um die Auslagerungsdatei eines Prozesses zu untersuchen. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), Verschieben des Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen sind verfügbar, auf die **Auslagerungsdatei** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Auslagerungsdatei-Bytes**|Die aktuelle Anzahl der Seiten, die diesen Prozess in der Auslagerungsdatei verwendet wird. Die Auslagerungsdatei speichert Datenseiten vom Prozess verwendet wird, aber nicht in anderen Dateien enthalten. Die Auslagerungsdatei wird von allen Prozessen verwendet, und nicht genügend Speicherplatz in der Auslagerungsdatei kann zu Fehlern führen, während andere Prozesse ausgeführt werden.|  
|**Peak Auslagerungsdatei Bytes**|Die maximale Anzahl der Seiten, die diesen Prozess in der Auslagerungsdatei verwendet hat.|  
|**Seitenfehler**|Die Anzahl der Seitenfehler durch die in diesem Prozess ausgeführten Threads. Ein Seitenfehler tritt auf, wenn ein Thread auf eine virtuelle Speicherseite verweist, die nicht in seinem Arbeitssatz im Hauptspeicher befindet. Daher wird die Seite nicht vom Datenträger abgerufen, ist er auf der Standbyliste und somit bereits im Hauptspeicher befindet oder wenn sie durch eine andere verwendet wird verarbeitet, mit denen die Seite freigegeben ist.|