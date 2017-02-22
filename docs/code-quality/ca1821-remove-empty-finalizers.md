---
title: "CA1821: Leere Finalizer entfernen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RemoveEmptyFinalizers"
  - "CA1821"
helpviewer_keywords: 
  - "CA1821"
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1821: Leere Finalizer entfernen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ implementiert einen Finalizer, der leer ist, ruft nur den Finalizer des Basistyps oder nur bedingt ausgegebene Methoden auf.  
  
## Regelbeschreibung  
 Finalizer sollten möglichst vermieden werden, da durch Verfolgung der Objektlebensdauer zusätzliche Leistung beansprucht wird.  Der Garbage Collector führt den Finalizer aus, bevor das Objekt freigegeben wird.  Dies bedeutet, dass zwei Auflistungen erforderlich sind, um das Objekt zu erfassen.  Ein leerer Finalizer verursacht diesen zusätzlichen Verwaltungsaufwand ohne irgendeinen Nutzen.  
  
## Behandeln von Verstößen  
 Entfernen Sie den leeren Finalizer.  Wenn ein Finalizer für das Debuggen erforderlich ist, schließen Sie den gesamten Finalizer in `#if DEBUG / #endif`\-Direktiven ein.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Meldung dieser Regel.  Wird der Abschluss nicht unterdrückt, beeinträchtigt dies die Leistung, und es ergeben sich keine Vorteile.  
  
## Beispiel  
 Das folgende Beispiel enthält einen leeren Finalizer, der entfernt werden sollte, einen Finalizer, der in `#if DEBUG / #endif`\-Direktiven eingeschlossen werden sollte, und einen Finalizer, bei dem die `#if DEBUG / #endif`\-Direktiven ordnungsgemäß eingesetzt werden.  
  
 [!code-cs[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]