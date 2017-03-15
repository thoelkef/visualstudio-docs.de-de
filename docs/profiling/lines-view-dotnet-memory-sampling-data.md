---
title: "Zeilenansicht - .NET-Speichersamplingdaten im Profiler | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Zeilenansicht"
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Zeilenansicht - .NET-Speichersamplingdaten im Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Zeilenansicht der Profilerstellungsdaten für die .NET\-Speicherbelegung, die die Samplingmethode verwenden, werden die Anweisungen angezeigt, die während der Profilerstellungsausführung Arbeitsspeicher belegt haben.  Die Spalten enthalten auch die Größe und die Anzahl von Zuordnungen.  
  
 In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten.  
  
 Eine Anweisung wird mit Folgendem identifiziert:  
  
-   Den Namen der Quelldatei, die diese Funktionsanweisung enthält.  
  
-   Die Funktion, die die Anweisung enthält.  
  
-   Die Quellzeile, in der die Anweisung beginnt.  
  
-   Das Zeichen in der Quellzeile, mit dem die Anweisung beginnt.  
  
-   Die Quellzeile, in der die Anweisung endet.  
  
-   Das Zeichen in der Quellzeile, mit dem die Anweisung endet.  
  
 Die Zeilennamenspalte stellt eine sortierbare Verkettung der Bezeichnerdaten bereit.  
  
 Laut Definition ruft eine Anweisung keine anderen Funktionen auf.  Daher sind nur exklusive Werte aufgeführt.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Anweisung enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält.|  
|**Quelldatei**|Der Name der Quelldatei, die diese Anweisung enthält.|  
|**Function Name**|Der Name der Funktion, die die Anweisung enthält.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Function Address**|Die Startadresse der Funktion.|  
|**Source Line Begin**|Die Startzeilennummer in der Quelldatei, bei der die Zuordnung aufgetreten ist.|  
|**Source Line End**|Die Endzeilennummer in der Quelldatei, bei der die Zuordnung aufgetreten ist.|  
|**Source Character Begin**|Der Offset des Startzeichens in der Quelldateizeile, bei dem die Zuordnung aufgetreten ist.|  
|**Source Character End**|Der Offset des Endzeichens in der Quelldateizeile, bei dem die Zuordnung aufgetreten ist.|  
|**Zeilenname**|Ein Profiler\-generierter Bezeichner der Zeile mit der folgenden Syntax:`Source File`**;\[**`Line Number Start`**,**`Character Start`**\]\-\>;\[**`Line Number Start,Character Start`**\]**|  
|**Exclusive Allocations**|Die Gesamtzahl von Objekten, die in dieser Zeile erstellt wurden.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller während der Profilerstellung erstellten Objekte, die in dieser Zeile zugeordnet wurden.|  
|**Exklusive Bytes**|Der Prozentsatz aller während der Profilerstellung belegten Bytes im Arbeitsspeicher, die in dieser Zeile zugeordnet wurden.|  
|**Exklusive Bytes in %**|Der Prozentsatz aller während der Profilerstellung belegten Bytes im Arbeitsspeicher, die in dieser Zeile zugeordnet wurden.|  
  
## Siehe auch  
 [Zeilenansicht](../profiling/lines-view-sampling-data.md)