---
title: "DA0001: StringBuilder f&#252;r Verkettungen verwenden | Microsoft Docs"
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
  - "vs.performance.DA0001"
  - "vs.performance.rules.DAUseStringBuilder"
  - "vs.performance.1"
  - "vs.performance.rules.DA0001"
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0001: StringBuilder f&#252;r Verkettungen verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0001|  
|Kategorie \(Category\)|.NET Framework\-Verwendung|  
|Profilerstellungsmethoden|Sampling<br /><br /> Instrumentation|  
|Meldung|Erwägen Sie, StringBuilder für Zeichenfolgenverkettungen zu verwenden|  
|Meldungstyp|Warnung|  
  
## Ursache  
 Aufrufe von "System.String.Concat" machen einen großen Teil der Profilerstellungsdaten aus.  Verwenden Sie ggf. die <xref:System.Text.StringBuilder>\-Klasse, um Zeichenfolgen aus mehreren Segmenten zu erstellen.  
  
## Regelbeschreibung  
 Ein <xref:System.String>\-Objekt ist unveränderlich.  Daher erstellt jede Änderung an der Zeichenfolge ein neues Zeichenfolgenobjekt und die Garbage Collection des Originals.  Dieses Verhalten ist das gleiche, ob Sie String.Concat explizit aufrufen oder die Zeichenfolgenverkettungsoperatoren wie \+ oder \+\= verwenden.  Die Programmleistung kann sich verringern, wenn diese Methoden häufig aufgerufen werden, z. B., wenn einer Zeichenfolge in einer dichten Schleife Zeichen hinzugefügt werden.  
  
 Die StringBuilder\-Klasse ist ein veränderbares Objekt, und im Gegensatz zu System.String geben die meisten der Methoden für StringBuilder, die eine Instanz dieser Klasse ändern, einen Verweis auf die gleiche Instanz zurück.  Sie können Zeichen einfügen oder Text an eine StringBuilder\-Instanz anfügen und Zeichen in der Instanz entfernen oder ersetzen, ohne eine neue Instanz zuordnen und die ursprüngliche Instanz löschen zu müssen.  
  
## Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie im Fenster "Fehlerliste" auf die Meldung, um zur [Funktionsdetailansicht](../profiling/function-details-view.md) der Samplingprofildaten zu navigieren.  Suchen Sie die Abschnitte des Programms, das Zeichenfolgenverkettungen am häufigsten verwendet.  Verwenden Sie die StringBuilder\-Klasse für komplexe Zeichenfolgenbearbeitungen, einschließlich häufiger Zeichenfolgenverkettungsoperationen.  
  
 Weitere Informationen zum Arbeiten mit Zeichenfolgen finden Sie im Abschnitt [Zeichenfolgenoperationen](http://go.microsoft.com/fwlink/?LinkId=177816) in [Kapitel 5 \- Verbessern der verwalteten Codeleistung](http://go.microsoft.com/fwlink/?LinkId=177817) der Microsoft\-Muster\- und Practices\-Bibliothek.