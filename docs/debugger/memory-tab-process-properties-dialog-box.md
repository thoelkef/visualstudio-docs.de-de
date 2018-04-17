---
title: Registerkarte "Arbeitsspeicher", Prozess-Eigenschaftendialogfeld | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd450ecf1dc93344adc0eadfebb6df05ab880d25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="memory-tab-process-properties-dialog-box"></a>Registerkarte "Arbeitsspeicher", Dialogfeld "Prozesseigenschaften"
Verwenden der **Arbeitsspeicher** Tab, um zu zeigen, wie ein Prozess Arbeitsspeicher verwendet. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), Verschieben des Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen sind verfügbar, auf die **Arbeitsspeicher** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Virtuelle Bytes**|Die aktuelle Größe (in Bytes) des virtuellen Adressraums des Prozesses verwendet. Die Verwendung des virtuellen Adressraums impliziert nicht unbedingt Nutzung von Festplatten- oder Hauptspeicher. Allerdings virtueller Speicherplatz ist endlich, und mit viel die Fähigkeit des Prozesses zum Laden von Bibliotheken beschränken kann.|  
|**Virtuelle Bytes max.**|Gleichzeitig wurde die maximale Anzahl von Bytes des virtuellen Adressraums des Prozesses verwendet.|  
|**Arbeitsseiten**|Der Satz von Speicherseiten, die vor kurzem von den Threads im Prozess berührt werden. Wenn der freie Speicher des Computers oberhalb des Schwellenwerts liegt, sind Seiten in den Arbeitsseiten eines Prozesses übrig, auch wenn sie nicht verwendet werden. Wenn der freie Speicher unter einen Schwellenwert fällt, werden Seiten aus den Arbeitsseiten entfernt. Wenn sie benötigt werden, werden sie wieder in die Workingsets zurückverschoben vor dem Verlassen des Hauptspeichers.|  
|**Max. Arbeitssatz**|Die maximale Anzahl von Seiten im Workingset dieses Prozesses zu einem beliebigen Zeitpunkt zeitlich.|  
|**Bytes von ausgelagertem Speicherpool**|Die aktuelle Größe des ausgelagerten Pools, der den Prozess reserviert wurde. Auslagerungspool ist ein System-Speicherbereich, in denen Komponenten des Betriebssystems Speicherplatz reservieren, wie sie ihre bezeichneten Aufgaben erledigen. Auslagerungspool Seiten können nicht in die Auslagerungsdatei, wenn das System für einen längeren Zeitraum nicht auf Sie zugegriffen ausgelagert werden.|  
|**Bytes des nicht ausgelagerten Pools**|Die aktuelle Anzahl der Bytes im nicht ausgelagerten Pools durch den Prozess zugeordnet. Der nicht ausgelagerte Pool ist eine System-Speicherbereich, auf dem Speicherplatz von Betriebssystemkomponenten abgerufen wird, wie sie ihre bezeichneten Aufgaben erledigen. Seiten des nicht ausgelagerten Pools können nicht in die Auslagerungsdatei ausgelagert werden; Sie bleiben im Hauptspeicher, solange sie zugewiesen sind.|  
|**Private Bytes**|Die aktuelle Anzahl der Bytes, die diesen Prozess reserviert wurde, kann nicht mit anderen Prozessen gemeinsam genutzt werden.|  
|**Freie Bytes**|Die Gesamtanzahl nicht verwendeten virtuellen Adressraums dieses Prozesses.|  
|**Reservierte Bytes**|Die Gesamtmenge des virtuellen Arbeitsspeichers, die von diesem Prozess für zukünftige Verwendung reserviert.|  
|**Freie Bytes des Images**|Die Menge des virtuellen Adressraums, die wird nicht verwendet oder reserviert wurden vom Bildern innerhalb dieses Prozesses.|  
|**Reservierte Bytes des Images**|Die Summe der gesamten virtuellen Arbeitsspeicher vom Bildern innerhalb dieses Prozesses reserviert.|