---
title: "DA0013: Umfangreiche Verwendung von String.Split oder String.Substring | Microsoft Docs"
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
  - "vs.performance.13"
  - "vs.performance.rules.DAAvoidStringSubstr"
  - "vs.performance.DA0013"
  - "vs.performance.rules.DA0013"
helpviewer_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DA0013"
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0013: Umfangreiche Verwendung von String.Split oder String.Substring
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0013|  
|Kategorie \(Category\)|.NET Framework\-Verwendungsleitfaden|  
|Profilerstellungsmethoden|Sampling|  
|Meldung|Sie sollten eine Reduzierung der String.Split\- und String.Substring\-Funktionen in Betracht ziehen.|  
|Regeltyp|Warnung|  
  
## Ursache  
 Aufrufe der System.String.Split\-Methode oder der System.String.Substring\-Methode machen einen großen Teil der Profilerstellungsdaten aus.  Verwenden Sie ggf. "System.String.IndexOf" oder "System.String.IndexOfAny", wenn Sie testen möchten, ob in einer Zeichenfolge eine Teilzeichenfolge vorhanden ist.  
  
## Regelbeschreibung  
 Die Split\-Methode wirkt auf ein Zeichenfolgenobjekt und gibt ein neues Zeichenfolgenarray zurück, das die Teilzeichenfolgen des Originals enthält.  Die Funktion belegt Speicher für das zurückgegebene Arrayobjekt und ordnet ein neues Zeichenfolgenobjekt für jedes Arrayelement zu, das es findet.  Auf ähnliche Weise behandelt die Substr\-Methode ein Zeichenfolgenobjekt und gibt eine neue Zeichenfolge zurück, die der Teilzeichenfolge, die angefordert wurde, entspricht.  
  
 Wenn die Verwaltung von Speicherbelegungen in der Anwendung wichtig ist, erwägen Sie, Alternativen zur String.Split\-Methode und String.Substr\-Methode zu verwenden.  Sie können eine bestimmte Teilzeichenfolge innerhalb einer Zeichenfolge suchen, ohne eine neue Instanz der Zeichenfolgenklasse zu erstellen, mithilfe entweder der IndexOf\-Methode oder der IndexOfAny\-Methode.  
  
## Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie im Fenster "Fehlerliste" auf die Meldung, um zur [Funktionsdetailansicht](../profiling/function-details-view.md) der Samplingprofildaten zu navigieren.  Untersuchen Sie die aufrufenden Funktionen, um Abschnitte des Programms zu suchen, die die System.String.Split\-Methode oder die System.String.Substr\-Methode am häufigsten verwenden.  Sie können nach Möglichkeit eine bestimmte Teilzeichenfolge innerhalb einer Zeichenfolge suchen, ohne eine neue Instanz der Zeichenfolgenklasse zu erstellen, mithilfe entweder der IndexOf\-Methode oder der IndexOfAny\-Methode.