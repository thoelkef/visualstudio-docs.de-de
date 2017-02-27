---
title: "Aufrufstrukturansicht - Profiler-Konfliktdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aufrufstrukturansicht"
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Aufrufstrukturansicht - Profiler-Konfliktdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Aufrufstrukturansicht zeigt die Funktionsausführungspfade an, die in der profilierten Anwendung durchlaufen wurden.  Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente.  Jeder Funktionsknoten führt Folgendes auf: Alle von ihm aufgerufenen Funktionen, wie oft die Funktion blockiert wurde und wie lange die Funktion blockiert war, weil sie mit anderen Threads oder Prozessen um eine Ressource konkurriert hat.  
  
 Die Werte in der Aufrufstrukturansicht beziehen sich auf die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden.  Prozentwerte werden berechnet, indem der Funktionsinstanzwert mit der Gesamtzahl der Konflikte in der Profilerstellungsausführung verglichen wird.  
  
## Hervorheben des langsamsten Ausführungspfads  
 Die Ansicht der Aufrufstruktur kann erweitert werden und den Ausführungspfad des Prozesses oder der Funktion hervorheben, die die meisten Konflikte verursacht hat.  
  
-   Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf den den Prozess oder die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.  
  
## Festlegen des Stammknotens der Aufrufstruktur  
 Jeder Prozess in der Profilerstellungsausführung wird als Stammknoten angezeigt.  Sie können den Startknoten der Aufrufstrukturansicht festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann **Stamm festlegen** auswählen.  
  
 Durch Festlegen des Stammknotens verhindern Sie, dass alle anderen Einträge außer der Teilstruktur des ausgewählten Knotens in der Ansicht angezeigt werden.  Um den Stammknoten auf den ursprünglichen Knoten zurückzusetzen, klicken Sie mit der rechten Maustaste auf die Aufrufstrukturansicht und dann auf **Stamm zurücksetzen**.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Exklusive blockierte Zeit**|Die Zeit, die Instanzen dieser Funktion in diesem Ausführungspfad davon abgehalten wurden, in der Profilerstellungsausführung ausgeführt zu werden.  Die Zeit schließt die blockierte Zeit von untergeordneten Funktionen nicht ein, die von der Funktion aufgerufen wurden.|  
|**Exklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit während der Profilerstellungsausführung, die auf die exklusive blockierte Zeit dieser Funktion in diesem Ausführungspfad entfällt.|  
|**Exklusive Konflikte**|Die Anzahl von Konflikten, die in Instanzen dieser Funktion in diesem Ausführungspfad aufgetreten sind.  Die Zahl schließt Konflikte untergeordneter Funktionen nicht ein, die von der Funktion aufgerufen wurden.|  
|**Exklusive Konflikte %**|Der Prozentsatz aller Konflikte während der Profilerstellungsausführung, die exklusive Konflikte der Instanzen dieser Funktion waren, die von der übergeordneten Funktion in dieser Aufrufstruktur aufgerufen wurden.|  
|**Function Address**|Die Adresse der Funktion.|  
|**Function Name**|Der vollqualifizierte Name der Funktion.|  
|**Inklusive blockierte Zeit**|Die Gesamtzeit, die Instanzen dieser Funktion in diesem Ausführungspfad davon abgehalten wurden, in der Profilerstellungsausführung ausgeführt zu werden.  Die Zeit schließt die blockierte Zeit untergeordneter Funktionen ein, die von der Funktion aufgerufen wurde.|  
|**Inklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit während der Profilerstellungsausführung, die auf die inklusive blockierte Zeit der Instanzen dieser Funktion in diesem Ausführungspfad entfällt.|  
|**Inklusive Konflikte**|Die Gesamtzahl von Konflikten, die Instanzen dieser Funktion in diesem Ausführungspfad blockiert haben.  Die Zahl schließt Konflikte untergeordneter Funktionen ein, die von der Funktion aufgerufen wurden.|  
|**Inklusive Konflikte %**|Der Prozentsatz aller Konflikte während der Profilerstellungsausführung, die inklusiven Konflikten der Instanzen dieser Funktion in diesem Ausführungspfad waren.|  
|**Ebene**|Die Ebene der Funktion in der Aufrufstruktur.  Nur in VSReport\-Befehlszeilenberichten.  Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view.md)   
 [Aufrufstrukturansicht \- Instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Aufrufstrukturansicht \- Sampling](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-instrumentation-data.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-sampling-data.md)