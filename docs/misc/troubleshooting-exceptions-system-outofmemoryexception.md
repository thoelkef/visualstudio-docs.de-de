---
title: "Problembehandlung bei Ausnahmen: System.OutOfMemoryException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OutOfMemoryException-Klasse"
ms.assetid: eb16f008-964e-40a1-91f6-6ad25fa82d5a
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.OutOfMemoryException
Eine <xref:System.OutOfMemoryException>\-Ausnahme wird ausgelöst, wenn ein Versuch zur Belegung von Arbeitsspeicher fehlschlägt.  
  
## Tipps  
 **Stellen Sie beim Erstellen eines Arrays sicher, dass die Größe richtig ist.**  
 Visual Basic\-Benutzer finden weitere Informationen unter [Arrays](/dotnet/visual-basic/programming-guide/language-features/arrays/index).  
  
 C\#\-Benutzer finden weitere Informationen unter [Arrays](/dotnet/csharp/programming-guide/arrays/index).  
  
 **Stellen Sie sicher, dass genügend Arbeitsspeicher für interne Zwecke und neue verwaltete Objekte vorhanden ist.**  
 Wenn Sie in [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] programmieren, löst die Common Language Runtime diese Ausnahme aus, wenn nicht genügend Speicher für interne Zwecke oder neue verwaltete Objekte zur Verfügung steht. Um diese Ausnahme zu vermeiden, programmieren Sie keine umfangreichen Methoden, die 64 KB Speicher oder mehr beanspruchen.  
  
## Hinweise  
 Übermäßige Auslastung des verwalteten Speichers hat im Allgemeinen folgende Ursachen:  
  
-   Einlesen umfangreicher Datasets in den Arbeitsspeicher.  
  
-   Erstellen übermäßig vieler Cacheeinträge.  
  
-   Hoch\- oder Herunterladen großer Dateien.  
  
-   Übermäßige Verwendung von regulären Ausdrücken oder Zeichenfolgen während des Analysieren von Dateien.  
  
-   Umfangreicher Ansichtszustand.  
  
-   Zu viele Daten im Sitzungszustand oder zu viele Sitzungen.  
  
 Im Zusammenhang mit dieser Ausnahme wird möglicherweise zusätzlich die Meldung "Für diesen Vorgang ist nicht genügend Speicher verfügbar." ausgegeben. Diese Meldung wird angezeigt, wenn eine Methode an einem COM\-Objekt aufgerufen wird, die einen benutzerdefinierten Typ zurückgibt, der ein sicheres Array enthält \(ein Array, das keine feste Größe hat\). Dies liegt daran, dass .NET Framework ein Strukturfeld nicht mit einem sicheren Arraytyp marshallen kann.  
  
## Siehe auch  
 <xref:System.OutOfMemoryException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)