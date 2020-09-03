---
title: Registerkarte „Arbeitsspeicher“, Dialogfeld „Prozesseigenschaften“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b70c5a982da866cbeb9e9907859ad4d270d79bd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203308"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Registerkarte "Arbeitsspeicher", Dialogfeld "Prozesseigenschaften"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Über die Registerkarte **Arbeitsspeicher** können Sie anzeigen, wie Arbeitsspeicher von einem Prozess verwendet wird. Verschieben Sie den Fokus der Ansicht auf das Fenster [Prozessansicht](../debugger/processes-view.md), um das [Dialogfeld „Prozesseigenschaften“](../debugger/process-properties-dialog-box.md) anzuzeigen. Wählen Sie einen beliebigen Prozessknoten in der Struktur und anschließend im Menü **Ansicht** die Option **Eigenschaften** aus.  
  
 Auf der Registerkarte **Arbeitsspeicher** sind folgende Einstellungen verfügbar:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Virtuelle Bytes**|Die aktuelle Größe (in Bytes) des virtuellen Adressraums, der vom Prozess verwendet wird. Die Verwendung von virtuellem Adressraum bedeutet nicht unbedingt, dass auch entsprechend Datenträger- oder Hauptspeicherseiten verwendet werden. Virtueller Speicherplatz ist jedoch begrenzt, und eine zu hohe Speicherplatzauslastung kann zu Einschränkungen beim Laden von Bibliotheken führen.|  
|**Virtuelle Bytes max.**|Die maximale Anzahl von Bytes des vom Prozess jeweils verwendeten virtuellen Adressraums|  
|**Arbeitssatz**|Die Speicherseiten, die vor kurzem von den Threads im Prozesses verwendet wurden. Wenn der freie Speicher des Computers oberhalb des Schwellenwerts liegt, sind Seiten im Workingset eines Prozesses übrig, auch wenn sie nicht verwendet werden. Wenn der freie Arbeitsspeicher unter einen bestimmten Schwellenwert sinkt, werden Seiten aus dem Workingset gekürzt. Wenn die Seiten benötigt werden, werden sie vor dem Verlassen des Hauptspeichers in das Workingset zurückverschoben.|  
|**Arbeitssatz max.**|Die maximale Anzahl von Seiten im Workingset dieses Prozesses zu einem beliebigen Zeitpunkt|  
|**Auslagerbare Poolbytes**|Die aktuelle Größe des ausgelagerten Pools, die der Prozess zugeordnet hat. Ein ausgelagerter Pool ist ein Systemspeicherbereich, in dem Betriebssystemkomponenten Speicherplatz beim Ausführen der vorgesehenen Aufgaben erhalten. Seiten ausgelagerter Pools können in die Auslagerungsdatei ausgelagert werden, wenn vom System über einen längeren Zeitraum nicht darauf zugegriffen wird.|  
|**Nicht auslagerbare Poolbytes**|Die aktuelle Anzahl von Bytes im nicht ausgelagerten Pool, der vom Prozess zugeordnet wird. Ein nicht ausgelagerter Pool ist ein Systemspeicherbereich, in dem Betriebssystemkomponenten Speicherplatz beim Ausführen der vorgesehenen Aufgaben erhalten. Seiten nicht ausgelagerter Pools können nicht in die Auslagerungsdatei ausgelagert werden. Sie verbleiben im Hauptspeicher, solange sie zugeordnet sind.|  
|**Private Bytes**|Die aktuelle Anzahl von Bytes, die dem Prozess zugeordnet sind und die nicht mit anderen Prozessen geteilt werden können.|  
|**Freie Bytes**|Der gesamte nicht verwendete virtuelle Adressraum dieses Prozesses|  
|**Reservierte Bytes**|Die Gesamtmenge des virtuellen Arbeitsspeichers, der für die zukünftige Verwendung durch diesen Prozess reserviert ist|  
|**Freie Bytes des Images**|Der Umfang des virtuellen Adressraums, der nicht in Gebrauch ist oder durch Images innerhalb dieses Prozesses reserviert wird|  
|**Reservierte Bytes des Images**|Die Summe aller virtuellen Arbeitsspeicher, die von Images reserviert werden, die innerhalb dieses Prozesses ausgeführt werden|
