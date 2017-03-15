---
title: "Aufrufstrukturansicht - .NET-Speichersamplingdaten im Profiler | Microsoft Docs"
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
  - "Aufrufstrukturansicht"
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aufrufstrukturansicht - .NET-Speichersamplingdaten im Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Aufrufstrukturansicht zeigt die Funktionsausführungspfade an, die in der profilierten Anwendung durchlaufen wurden.  Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente.  Jeder Funktionsknoten führt alle Funktionen, die er aufgerufen hat, sowie die Daten zur .NET\-Speicherbelegung über diese Funktionsaufrufe auf.  
  
 Die Werte in der Aufrufstrukturansicht beziehen sich auf die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden.  Prozentwerte werden berechnet, indem der Funktionsinstanzwert mit der Gesamtzahl oder der Größe der Zuordnungen während der Profilerstellung verglichen wird.  
  
## Hervorheben des langsamsten Ausführungspfads  
 Die Ansicht der Aufrufstruktur kann erweitert werden und den Ausführungspfad des Prozesses oder der Funktion hervorheben, die die größten oder die meisten Speicherobjekte erstellt hat.  Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf den den Prozess oder die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.  
  
## Festlegen des Stammknotens der Aufrufstruktur  
 Jeder Prozess in der Profilerstellungsausführung wird als Stammknoten angezeigt.  Sie können den Startknoten der Aufrufstrukturansicht für einen anderen Knoten festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann **Stamm festlegen** auswählen.  
  
 Durch Festlegen des Stammknotens verhindern Sie, dass alle anderen Einträge außer der Teilstruktur des ausgewählten Knotens in der Ansicht angezeigt werden.  Sie können den Stammknoten auf den Knoten zurücksetzen, den Sie angezeigt haben. Klicken Sie mit der rechten Maustaste in das Fenster mit der Aufrufstrukturansicht, und wählen Sie **Stamm zurücksetzen** aus.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Function Name**|Der vollqualifizierte Name der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Function Address**|Die Adresse der Funktion.|  
|**Ebene**|Die Tiefe der Funktion in der Aufrufstruktur.|  
|**Inclusive Allocations**|Die Anzahl der Objekte, die von den Instanzen dieser Funktion zugeordnet wurden, die von der in der Aufrufstruktur übergeordneten Funktion aufgerufen wurden.  Diese Zahl schließt in untergeordneten Funktionen vorgenommene Zuordnungen ein.|  
|**Inklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exclusive Allocations**|Die Anzahl der Objekte, die von den Instanzen dieser Funktion zugeordnet wurden, die von der in der Aufrufstruktur übergeordneten Funktion aufgerufen wurden.  Diese Zahl schließt keine in untergeordneten Funktionen erfolgten Zuweisungen ein.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller während der Profilerstellung erstellten Objekte, bei denen es sich um exklusive Zuordnungen der Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden, handelt.|  
|**Inklusive Bytes**|Die Anzahl der Bytes im Arbeitsspeicher, die von den Instanzen dieser Funktion zugeordnet wurden, die von der in der Aufrufstruktur übergeordneten Funktion aufgerufen wurden.  Diese Zahl schließt in untergeordneten Funktionen vorgenommene Zuordnungen ein.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exklusive Bytes**|Die Anzahl der Bytes im Arbeitsspeicher, die von den Instanzen dieser Funktion zugeordnet wurden, die von der in der Aufrufstruktur übergeordneten Funktion aufgerufen wurden.  Diese Zahl schließt keine in untergeordneten Funktionen erfolgten Zuweisungen ein.|  
|**Exklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und exklusive Belegungen dieser Funktion waren.|  
  
## Siehe auch  
 [Aufrufstrukturansicht \- Instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-sampling-data.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-instrumentation-data.md)