---
title: "Ressourcenkonfliktansicht – Profiler-Konfliktdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.resourcecontention"
helpviewer_keywords: 
  - "Ressourcenkonflikte (Ansicht)"
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Ressourcenkonfliktansicht – Profiler-Konfliktdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Ressourcenkonfliktansicht werden Konfliktdaten für diejenigen Ressourcen angezeigt, die Konfliktereignisse verursacht haben.  Ein Konfliktereignis tritt auf, wenn eine Funktion in einem Thread auf den Zugriff auf die Ressource warten muss, da eine Funktion in einem anderen Thread exklusiv auf die Ressource zugreift.  Jede Ressource ist der Stammknoten einer Aufrufstruktur, die die Ausführungspfade der Funktion anzeigt, aus denen sich die Konfliktereignisse ergeben.  
  
## Datenwerte  
  
### Ressourcenwerte  
 Die Daten in einer Ressourcenzeile zeigen an, wie lange der Zugriff auf eine Ressource in den Profilerstellungsdaten insgesamt blockiert war und wie viele Konfliktereignisse insgesamt aufgrund des Zugriffskonflikts für diese Ressource aufgetreten sind.  Die inklusiven und die exklusiven Werte einer Ressource sind immer dieselben.  
  
### Funktionswerte  
 Funktionswerte basieren auf den Instanzen der Funktion, die im in der Aufrufstruktur dargestellten Ausführungspfad ausgeführt wurden.  
  
-   Exklusive Werte basieren auf den Ereignissen, die bei der Ausführung von Anweisungen im Funktionstext aufgetreten sind.  Ereignisse in Funktionen, die von der Funktion aufgerufen wurden, sind in den exklusiven Werten nicht erfasst.  
  
-   Inklusive Werte basieren auf den Ereignissen, die beim Ausführen der Funktion oder beim Ausführen einer Funktion, die von der Funktion aufgerufen wurde, aufgetreten sind.  
  
### Prozentwerte  
 Prozentwerte basieren auf der Gesamtzeit oder den Konfliktereignissen in den Profilerstellungsdaten.  Wenn der Bericht oder die Ansicht der Profilerstellung gefiltert wird, werden nur die blockierte Zeit und die Konflikte in den gefilterten Daten als Gesamtwert verwendet.  
  
## Navigieren durch die Ressourcenzuordnungsansicht  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name der Ressource oder der Funktion.|  
|**Exklusive blockierte Zeit**|-   Bei einer Ressource die Gesamtzeit, die der Zugriff auf die Ressource blockiert war und ein Thread warten musste.<br />-   Bei einer Funktion die Zeit, in der diese Instanzen der Funktion nicht auf die übergeordnete Ressource zugreifen konnten, während die Funktion Code im Funktionstext ausgeführt hat.  Blockierte Zeit in Funktionen, die von der Funktion aufgerufen wurden, ist nicht eingeschlossen.|  
|**Exklusive blockierte Zeit %**|-   Bei einer Ressource der Prozentsatz der gesamten blockierten Zeit in den Profilerstellungsdaten, die auf die blockierte Zeit für diese Ressource entfällt.<br />-   Bei einer Funktion der Prozentsatz der gesamten blockierten Zeit in den Profilerstellungsdaten, die die Instanzen der Funktion exklusiv blockiert wurden.|  
|**Exklusive Konflikte**|-   Bei einer Ressource Angaben darüber, wie oft der Zugriff auf die Ressource blockiert war und ein Thread warten musste.<br />-   Bei einer Funktion Angaben darüber, wie oft diese Instanzen der Funktion nicht auf die übergeordnete Ressource zugreifen konnten, während die Funktion Code im Funktionstext ausgeführt hat.  Blockierereignisse in Funktionen, die von der Funktion aufgerufen wurden, sind nicht eingeschlossen.|  
|**Exklusive Konflikte %**|-   Bei einer Ressource der Prozentsatz aller Konfliktereignisse in den Profilerstellungsdaten, die beim Zugriff auf diese Ressource aufgetreten sind.<br />-   Bei einer Funktion der Prozentsatz aller Konfliktereignisse in den Profilerstellungsdaten, die exklusive Konfliktereignisse dieser Funktionsinstanzen für die übergeordnete Ressource gewesen sind.|  
|**Inklusive blockierte Zeit**|-   Bei einer Ressource die Gesamtzeit, die der Zugriff auf die Ressource blockiert war und ein Thread warten musste.<br />-   Bei einer Funktion die Zeit, in der diese Instanzen der Funktion oder andere von den Instanzen aufgerufene Funktionen nicht auf die übergeordnete Ressource zugreifen konnten, während die Funktion Code im Funktionstext ausgeführt hat.|  
|**Inklusive blockierte Zeit %**|-   Bei einer Ressource der Prozentsatz der gesamten blockierten Zeit in den Profilerstellungsdaten, die auf die blockierte Zeit für diese Ressource entfällt.<br />-   Bei einer Funktion der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, die auf die blockierte Zeit dieser Funktionsinstanzen entfällt.|  
|**Inklusive Konflikte**|-   Bei einer Ressource Angaben darüber, wie oft der Zugriff auf die Ressource blockiert war und ein Thread warten musste.<br />-   Bei einer Funktion der Prozentsatz aller Konfliktereignisse während der Profilerstellung, die inklusive Konfliktereignisse dieser Funktionsinstanzen für die übergeordnete Ressource gewesen sind.|  
|**Inklusive Konflikte %**|-   Bei einer Ressource der Prozentsatz aller Konfliktereignisse während der Profilerstellung, die beim Zugriff auf diese Ressource aufgetreten sind.<br />-   Bei einer Funktion Angaben darüber, wie oft diese Instanzen der Funktion nicht auf die übergeordnete Ressource zugreifen konnten, während die Funktion Code im Funktionstext ausgeführt hat.  Blockierereignisse in Funktionen, die von der Funktion aufgerufen wurden, sind nicht eingeschlossen.|  
|**Ebene**|Die Tiefe der Funktion in der Aufrufstruktur.  Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) des Prozesses, in dem die Funktion ausgeführt wurde.|  
|**Prozessname**|Der Prozessname.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|