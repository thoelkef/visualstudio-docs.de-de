---
title: ".NET-Speicherbelegungsansicht | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.allocation"
helpviewer_keywords: 
  - "Zuordnungsansicht"
  - "Leistungsberichte, Zuordnungsansicht"
  - "Berichte für Profilerstellungstools, Zuordnungsansicht"
  - "Profilerstellungstools, Zuordnungsansicht"
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# .NET-Speicherbelegungsansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Speicherbelegungsansicht werden die Typen angezeigt, die während der Profilerstellungsausführung erstellt wurden.  Jeder Typ stellt den Stammknoten einer Aufrufstruktur da, die die Funktionsausführungspfade anzeigt, aus denen sich die Speicherbelegungen des Typs ergeben.  
  
 Die Daten in einer Typzeile zeigen die Gesamtzahl von Objekten des Typs an, die bei der Profilerstellungsausführung erstellt wurden, und die Gesamtzahl von Bytes, die durch Objekte dieses Typs belegt wurden.  Die inklusiven und exklusiven Werte für einen Typ sind immer dieselben.  
  
-   Die inklusiven Werte beschreiben die Objekte, die in den Instanzen der Funktion und der untergeordneten Funktionen erstellt wurden, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden.  
  
-   Die exklusiven Werte beschreiben Objekte, die direkt von der Funktion beim Aufruf durch die übergeordnete Funktion erstellt wurden.  In untergeordneten Funktionen erstellte Objekte sind nicht eingeschlossen.  
  
 Die Daten für eine Funktion zeigen die Anzahl von Objekten und die Speicherbelegung in Bytes durch Objekte des übergeordneten Typs an.  
  
## Hervorheben des langsamsten Ausführungspfads  
 Sie können den Ausführungspfad der Aufrufstruktur suchen, durch den die meisten Objekte des übergeordneten Typs erstellt wurden.  
  
-   Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf den Typ oder die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name des Typs oder der Funktion.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das den Typ oder die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das den Typ oder die Funktion enthält.|  
|**Quelldatei**|Die Quelldatei, die die Definition für den Typ oder die Funktion enthält.|  
|**Funktionszeilennummer**|Die Zeilennummer in der Quelldatei, bei der die Typdefinition oder Funktion beginnt.|  
|**Ebene**|Gibt an, ob die Daten für einen Typ oder eine Funktion sind.|  
|**Inclusive Allocations**|-   Bei einer Funktion die Gesamtzahl von Objekten des übergeordneten Typs, die von der Funktion erstellt wurden.  Diese Zahl schließt in untergeordneten Funktionen erstellte Objekte ein.<br />-   Bei einem Typ die Gesamtzahl von Instanzen dieses Typs, die erstellt wurden.|  
|**Inklusive Zuordnungen in %**|-   Bei einer Funktion der Prozentsatz aller während der Profilerstellungsausführung erstellten Objekte, bei denen es sich um inklusive Zuordnungen des übergeordneten Typs durch die Funktion handelte.<br />-   Bei einem Typ der Prozentsatz aller während der Profilerstellungsausführung erstellten Objekte, bei denen es sich um Instanzen des Typs handelte.|  
|**Exclusive Allocations**|-   Bei einer Funktion die Anzahl der Objekte, die während der direkten Ausführung der Funktion auf der obersten Ebene der Aufrufliste erstellt wurden.  Diese Zahl schließt keine in untergeordneten Funktionen erstellten Objekte ein.<br />-   Bei einem Typ die Gesamtzahl von Instanzen dieses Typs, die erstellt wurden.|  
|**Exklusive Zuordnungen in %**|-   Bei einer Funktion der Prozentsatz aller während der Profilerstellungsausführung erstellten Objekte, bei denen es sich um exklusive Zuordnungen des übergeordneten Typs durch die Funktion handelte.<br />-   Bei einem Typ der Prozentsatz aller während der Profilerstellungsausführung erstellten Objekte, bei denen es sich um Instanzen des Typs handelte.|  
|**Inklusive Bytes**|-   Bei einer Funktion der gesamte Speicher in Bytes, der von der Funktion für Objekte des übergeordneten Typs belegt wurde.  Diese Zahl schließt den Speicher ein, der von untergeordneten Funktionen belegt wurde.<br />-   Bei einem Typ der gesamte Speicher in Bytes, der während der Profilerstellungsausführung durch Instanzen des Typs belegt wurde.|  
|**Inklusive Bytes in %**|-   Bei einer Funktion der Prozentsatz des von der Funktion belegten Speichers, der während der Profilerstellungsausführung durch inklusive Zuordnungen des übergeordneten Typs belegt wurde.<br />-   Bei einem Typ der Prozentsatz des belegten Speichers, der während der Profilerstellungsausführung durch Instanzen des Typs belegt wurde.|  
|**Exklusive Bytes**|-   Bei einer Funktion der gesamte Speicher in Bytes, der von der Funktion für Objekte des übergeordneten Typs belegt wurde.  Diese Zahl schließt nicht den Speicher ein, der von untergeordneten Funktionen belegt wurde.<br />-   Bei einem Typ der gesamte Speicher in Bytes, der während der Profilerstellungsausführung durch Instanzen des Typs belegt wurde.|  
|**Exklusive Bytes in %**|-   Bei einer Funktion der Prozentsatz des von der Funktion belegten Speichers, der während der Profilerstellungsausführung durch exklusive Zuordnungen des übergeordneten Typs belegt wurde.<br />-   Bei einem Typ der Prozentsatz des belegten Speichers, der während der Profilerstellungsausführung durch Instanzen des Typs belegt wurde.|