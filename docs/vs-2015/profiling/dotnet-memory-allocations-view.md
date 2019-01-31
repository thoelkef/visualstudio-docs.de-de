---
title: .NET-Speicherbelegungsansicht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 563826c63d851e412b7c74a99f5b8a9ad1c1556e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798806"
---
# <a name="net-memory-allocations-view"></a>.NET-Speicherbelegungsansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Speicherbelegungsansicht werden die Typen aufgelistet, die während der Profilerstellung erstellt wurden. Jeder Typ ist der Stammknoten einer Aufrufstruktur, die Ausführungspfade der Funktion anzeigt, anhand derer die Speicherbelegung des Typs bestimmt wurde.  
  
 Die Daten in einem Zeilentyp geben die Gesamtanzahl der Objekte des Typs an, die bei der Profilerstellung erstellt wurden, und der dem Objekt für diesen Typ zugeordneten Bytes. Inklusive und exklusive Werte für einen Typ sind immer gleich.  
  
- Inklusive Werte gelten für Objekte, die in den Instanzen der Funktion erstellt wurden, und für deren untergeordnete Funktionen, die von der übergeordneten Funktion in der Aufrufliste aufgerufen wurden.  
  
- Exklusive Werte gelten für Objekte, die von der Funktion direkt erstellt wurden, als sie von der übergeordneten Funktion aufgerufen wurden. Objekte, die in untergeordneten Funktionen erstellt werden, werden nicht berücksichtigt.  
  
  In den Daten einer Funktion wird die Anzahl der erstellten Objekte sowie der dem Objekt des übergeordneten Typs zugeordneten Bytes angezeigt.  
  
## <a name="highlighting-the-execution-hot-path"></a>Hervorheben des langsamsten Ausführungspfads  
 Sie können den Ausführungspfad der Aufrufliste ermitteln, der die meisten Objekte des übergeordneten Typs erstellt hat.  
  
-   Klicken Sie mit der rechten Maustaste auf den Typ oder die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**, um den aktivsten Pfad anzuzeigen.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Name**|Der Name des zugeordneten Typs oder der zugeordneten Funktion.|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das den Typ oder die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das den Typ oder die Funktion enthält.|  
|**Quelldatei**|Die Quelldatei, die die Definition des Typs oder der Funktion enthält.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Typdefinition oder der Funktion in der Quelldatei.|  
|**Ebene**|Gibt an, ob die Daten für einen Typ oder eine Funktion gelten.|  
|**Inklusive Speicherbelegungen**|– Bei einer Funktion die Gesamtzahl von Objekten des übergeordneten Typs, die von der Funktion erstellt wurden. Diese Zahl schließt auch Objekte mit ein, die in untergeordneten Funktionen erstellt wurden.<br />– für einen Typ: die Gesamtzahl der Instanzen des Typs, die erstellt wurden.|  
|**Inklusive Speicherbelegungen in %**|– Bei einer Funktion der Anteil aller Objekte, die während der Profilerstellung erstellt wurden und inklusive Belegungen des übergeordneten Typs dieser Funktion waren.<br />– für einen Typ: der Anteil der Gesamtzahl der Objekte, die bei der Profilerstellung erstellt wurden und Instanzen dieses Typs sind.|  
|**Exklusive Speicherbelegungen**|– Bei einer Funktion die Anzahl von Objekten, die während der Ausführung der Funktion ab Anfang der Aufrufliste erstellt wurden. Diese Zahl schließt die Objekte nicht mit ein, die in untergeordneten Funktionen erstellt wurden.<br />– für einen Typ: die Gesamtzahl der Instanzen des Typs, die erstellt wurden.|  
|**Exklusive Zuordnungen %**|– Bei einer Funktion der Anteil aller Objekte, die während der Profilerstellung erstellt wurden und exklusive Belegungen des übergeordneten Typs dieser Funktion waren.<br />– für einen Typ: der Anteil der Gesamtzahl der Objekte, die bei der Profilerstellung erstellt wurden und Instanzen dieses Typs sind.|  
|**Inklusive Bytes in %**|– für eine Funktion: die Anzahl der Bytes im Arbeitsspeicher, die von der Funktion dem Objekt des übergeordneten Typs zugeordnet wurden. Diese Zahl schließt den Arbeitsspeicher mit ein, der von seinen untergeordneten Funktionen zugeordnet wurde.<br />– Bei einem Typ die Gesamtanzahl der Bytes, die der Profilerstellung für die Instanzen des Typs zugeordnet wurden.|  
|**Inklusive Bytes in %**|– Bei einer Funktion der Anteil des insgesamt bei der Profilerstellung zugeordneten Speicherplatzes, der inklusive Belegungen des übergeordneten Typs dieser Funktion war.<br />– für einen Typ: der Anteil des insgesamt bei der Profilerstellung zugeordneten Speicherplatzes, der den Instanzen des Typs zugeordnet war.|  
|**Exklusive Bytes**|– für eine Funktion: die Anzahl der Bytes im Arbeitsspeicher, die von der Funktion dem Objekt des übergeordneten Typs zugeordnet wurden. Diese Zahl schließt den Arbeitsspeicher mit nicht ein, der von seinen untergeordneten Funktionen zugeordnet wurde.<br />– Bei einem Typ die Gesamtanzahl von Bytes, die bei der Profilerstellung für die Instanzen des Typs zugeordnet waren.|  
|**Exklusive Bytes %**|– Bei einer Funktion der Anteil des insgesamt bei der Profilerstellung zugeordneten Speicherplatzes, der exklusive Belegungen des übergeordneten Typs dieser Funktion war.<br />– für einen Typ: der Anteil des insgesamt bei der Profilerstellung zugeordneten Speicherplatzes, der den Instanzen des Typs zugeordnet war.|
