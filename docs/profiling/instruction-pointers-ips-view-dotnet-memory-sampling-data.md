---
title: 'Anweisungszeigeransicht: .NET-Speichersamplingdaten | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 295dd3c490495f481ca9568524ee83eb0b1b59be
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966828"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Anweisungszeigeransicht: Samplingdaten zum .NET-Speicher
In der Anweisungszeigeransicht der Profilerstellungsdaten für die .NET-Speicherbelegung, die mithilfe der Samplingmethode erfasst wurden, werden die Assemblyanweisungen angezeigt, die während der Profilerstellungsausführung Arbeitsspeicher belegt haben. In den Spalten in der Ansicht werden auch die Größe und Anzahl der Zuordnungen aufgeführt.  
  
 Es sind nur exklusive Werte aufgeführt.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Anweisung enthält|  
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält|  
|**Quelldatei**|Die Quelldatei, die die Anweisung enthält|  
|**Funktionsname**|Der Name der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Funktionsadresse**|Die Startadresse der Funktion.|  
|**Quellanfangszeile**|Die Nummer der Anfangszeile in der Quelldatei, an der die Zuordnung aufgetreten ist.|  
|**Quellendzeile**|Die Nummer der Endzeile in der Quelldatei, an der die Zuordnung aufgetreten ist.|  
|**Quellanfangszeichen**|Das Offset des Startzeichens in der Quelldateizeile, an dem die Zuordnung aufgetreten ist.|  
|**Quellendzeichen**|Der Offset des Endzeichens der Quelldateizeile, an dem die Zuordnung aufgetreten ist.|  
|**Anweisungsadresse**|Die Adresse der Anweisung.|  
|**Exklusive Speicherbelegungen**|Die Gesamtanzahl der Objekte, die von dieser Anweisung erstellt wurden.|  
|**Exklusive Zuordnungen %**|Der Anteil aller Objekte, die während der Profilerstellung erstellt und von dieser Anweisung zugeordnet wurden.|  
|**Exklusive Bytes**|Die Anzahl von Bytes im Speicher, die während der Profilerstellung von der Anweisung zugeordnet wurden.|  
|**Exklusive Bytes %**|Der Anteil aller Bytes im Speicher, die während der Profilerstellung durch diese Anweisung zugeordnet wurden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Anweisungszeigeransicht](../profiling/instruction-pointers-ips-view-sampling-data.md)