---
title: "Zeilenansicht - Profiler-Konfliktdaten | Microsoft Docs"
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
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Zeilenansicht - Profiler-Konfliktdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Zeilenansicht für Konfliktdaten führt Leistungsdaten für die Anweisungen auf, die ausgeführt wurden, als die Samplings während der Profilerstellung gesammelt wurden.  In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten.  
  
 Eine Anweisung wird mit den folgenden Daten identifiziert:  
  
-   Den Namen der Quelldatei, die diese Funktionsanweisung enthält.  
  
-   Die Funktion, die die Anweisung enthält.  
  
-   Die Quellzeile, in der die Anweisung beginnt.  
  
-   Das Zeichen in der Quellzeile, mit dem die Anweisung beginnt.  
  
-   Die Quellzeile, in der die Anweisung endet.  
  
-   Das Zeichen in der Quellzeile, mit dem die Anweisung endet.  
  
 Die Zeilennamenspalte stellt eine sortierbare Verkettung der Bezeichnerdaten bereit.  
  
 In der folgenden Tabelle werden die Spalten des Zeilenansichtsberichts dargestellt.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Exklusive blockierte Zeit**|Die Zeit, in der die Anweisung aufgrund eines Konfliktereignisses keinen Code in der Anweisung ausführen konnte.  Blockierte Zeit in Funktionen, die von der Anweisung aufgerufen wurden, ist nicht enthalten.|  
|**Exklusive blockierte Zeit %**|Der Prozentsatz der blockierten Zeit im Prozess, der auf exklusive blockierte Zeit der Anweisung entfällt.|  
|**Exklusive Konflikte**|Angaben darüber, wie oft diese Anweisung aufgrund eines Konfliktereignisses keinen Code in der Anweisung ausführen konnte.  Konfliktereignisse in Funktionen, die von der Anweisung aufgerufen wurden, sind nicht eingeschlossen.|  
|**Exklusive Konflikte %**|Der Prozentsatz aller Konfliktereignisse im Prozess, der auf exklusive Konflikte dieser Anweisung entfällt.|  
|**Function Address**|Die Adresse der Funktion, die diese Anweisung enthält.|  
|**Function Name**|Der vollqualifizierte Name der Funktion, die diese Anweisung enthält.|  
|**Inklusive blockierte Zeit**|Die blockierte Zeit in dieser Anweisung und in Funktionen, die von dieser Anweisung aufgerufen wurden.|  
|**Inklusive blockierte Zeit %**|Der Prozentsatz der blockierten Zeit im Prozess, der auf inklusive blockierte Zeit der Anweisung entfällt.|  
|**Inklusive Konflikte**|Angaben darüber, wie oft diese Anweisung und Funktionen, die von dieser Anweisung aufgerufen wurden, für die Ausführung blockiert waren.|  
|**Inklusive Konflikte %**|Der Prozentsatz aller Konfliktereignisse im Prozess, der auf inklusive Konflikte dieser Anweisung entfällt.|  
|**Zeilenname**|Ein von einem Profiler generierter Bezeichner der Zeile.  Der Bezeichner verwendet die folgende Syntax:`SourceFile`**;\[**`LineNumberStart`**,**`CharacterStart`**\]\-\>;\[**`LineNumberEnd`**,**`CharacterEnd`**\]**|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Anweisung enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) des profilierten Prozesses.|  
|**Prozessname**|Der Prozessname.|  
|**Source Character Begin**|Der Offset des Startzeichens in der Quelldateizeile, an der diese Anweisung beginnt.|  
|**Source Character End**|Der Offset des Startzeichens in der Quelldateizeile, an der diese Anweisung endet.|  
|**Quelldatei**|Der Name der Quelldatei, die diese Funktionsanweisung enthält.|  
|**Source Line Begin**|Die Zeilennummer in der Quelldatei, mit der die Anweisung beginnt.|  
|**Source Line End**|Die Zeilennummer in der Quelldatei, mit der die Anweisung endet.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Zeilenansicht](../profiling/lines-view.md)   
 [Zeilenansicht \- Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Zeilenansicht](../profiling/lines-view-sampling-data.md)