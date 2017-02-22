---
title: "DA0012: Starke Reflektion | Microsoft Docs"
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
  - "vs.performance.rules.DAReflection"
  - "vs.performance.12"
  - "vs.performance.rules.DA0012"
  - "vs.performance.DA0011"
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0012: Starke Reflektion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0012|  
|Kategorie \(Category\)|.NET Framework\-Verwendung|  
|Profilerstellungsmethoden|Sampling|  
|Meldung|Möglicherweise verwenden Sie Reflektion zu häufig.  Dieser Vorgang ist äußerst speicherintensiv.|  
|Regeltyp|Warnung|  
  
## Ursache  
 Aufrufe der System.Reflection\-Methoden \(beispielsweise "InvokeMember" oder "GetMember"\) oder der Type\-Methoden \(beispielsweise "MemberInvoke"\) machen einen großen Teil der Profilerstellungsdaten aus.  Ersetzen Sie diese Methoden, wenn möglich, durch eine frühe Bindung an Methoden abhängiger Assemblys.  
  
## Regelbeschreibung  
 Reflektion ist eine flexible Funktion von .NET Framework, die verwendet werden kann, um späte Bindung der Anwendung an eine abhängige Laufzeitassembly auszuführen oder neue Typen während der Laufzeit zu erstellen und dynamisch auszuführen.  Diese Verfahren können jedoch die Leistung verringern, wenn sie häufig verwendet oder in dichten Schleifen aufgerufen werden.  
  
 Weitere Informationen finden Sie im [Reflektion und späte Bindung](http://go.microsoft.com/fwlink/?LinkId=177826)\-Abschnitt von " 5 \- verwaltete Code\-Leistung im der Verbesserung .NET\-Anwendung Leistungs\- und Skalierbarkeitsvolume der Microsoft\-Muster verbessernd und arbeitet Bibliothek auf MSDN.  
  
## Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie im Fenster Fehlerliste auf die Meldung, um zur [Funktionsdetailansicht](../profiling/function-details-view.md) der Profilerstellungsdaten zu navigieren.  Untersuchen Sie die aufrufenden Funktionen der System.Type\-Methode oder der System.Reflection\-Methode, um Abschnitte des Programms zu suchen, die .NET\-Reflektions\-APIs am häufigsten verwenden.  Vermeiden Sie, Methoden zu verwenden, die Metadaten zurückgeben.  Wenn die Leistung der Anwendung wichtig ist, müssen Sie möglicherweise vermeiden, späte Bindung zu verwenden und Typen zur Laufzeit dynamisch zu erstellen.