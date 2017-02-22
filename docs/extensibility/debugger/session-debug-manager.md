---
title: "Session-Debug-Manager | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sitzung Debug-Manager zu Sitzung Ansichten"
  - "Sitzung Debug-Manager senden"
  - "Debuggen [Debugging-SDK] Sitzung Debug-Managers"
  - "Sitzung Debug-manager"
  - "Debuggen Sie Debug-Sitzungsmanager Engine multiplexing"
  - "Sitzung Debug-Manager delegieren"
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Session-Debug-Manager
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Debuginformationen Manager der Sitzung \(SDM\) verwaltet beliebig viele Module \(Debuggen\) DE eine beliebige Anzahl an mehreren Prozessen Programme auf einer beliebigen Anzahl von Computern.  Zusätzlich zum Debuggen mehrfachkoppler sich ein Modul stellt das SDM eine einheitliche Sicht der Debugsitzung zur IDE bereit.  
  
## Sitzungs\-Debuger Manager\-Vorgang  
 Der Debuginformationen Manager der Sitzung \(SDM\) verwaltet. DE  Es gibt potenziell mehrere Triebwerklauf Debuggen auf einem Computer gleichzeitig.  Um das den zu multiplexen, wird die umbrüche SDM mehrere Schnittstellen aus dem und der IDE als einzelne Schnittstelle aus.  
  
 Um die Leistung zu verbessern, können nicht mehrere Schnittstellen Multiplex.  Stattdessen werden sie direkt von DE verwendet und Aufrufe dieser Schnittstellen von SDM das nicht ausgeführt werden.  Beispielsweise sind die Schnittstellen, die Arbeitsspeicher, Code und Dokumenten kontexten Multiplex nicht verwendet werden, weil sie eine bestimmte Anweisung, um einen Speicher oder ein Dokument in einem bestimmten Programm verwiesen werden, die von bestimmten DE gedebuggt wird.  Kein anderes DE muss in dieser Ebene der Kommunikation beteiligten sein.  
  
 Dies ist nicht von allen Kontexten true.  Aufrufe der Ausdrucksauswertungs Elementkontext Oberfläche des ausgeführten SDM\).  Während der Ausdrucksauswertung umschließt das SDM die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)\-Schnittstelle, die es in der IDE vorhanden ist, da bei dieser Ausdruck ausgewertet wird, es sich bei dem mehrere Debugprogramme sind, die in demselben Prozess liefe, die sich im selben Thread.  
  
 Das SDM tritt normalerweise als Mechanismus für Delegierungs, sondern es tritt möglicherweise als Mechanismus für Übertragungs auf.  Zum Beispiel bei der Ausdrucksauswertung, tritt das SDM als Mechanismus für Übertragungs auf, um alle DES zu benachrichtigen, dass sie Code für einen bestimmten Thread ausführen können.  Auch wenn das SDM ein aufhörendes Ereignis empfängt, überträgt sie auf Alle Programme, dass sie nicht ausgeführt werden sollten.  Wenn ein Schritt aufgerufen wird, die auf Alle Programme SDM\-Übertragungen Ausführung fortsetzen können, dass sie.  Haltepunkte werden auch in jedem DE übertragen.  
  
 Das SDM verfolgt nicht das aktuelle Programm den Thread oder den Stapelrahmen.  Der Prozess, und das Programm wird der Thread Informationen werden an den SDM in Verbindung mit bestimmten Ereignissen Debuggen gesendet.  
  
## Siehe auch  
 [Debug\-Modul](../../extensibility/debugger/debug-engine.md)   
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)   
 [Debugger\-Kontexte](../../extensibility/debugger/debugger-contexts.md)