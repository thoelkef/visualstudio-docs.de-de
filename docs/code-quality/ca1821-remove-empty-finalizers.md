---
title: 'CA1821: Leere Finalizer entfernen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords: CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: afe1c05ff76a2b4c37296ef6a534e37a5d1229b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Leere Finalizer entfernen
|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|Kategorie|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Typ implementiert einen Finalizer, der leer ist, ruft nur die Finalizer des Basistyps oder nur bedingt ausgegebene Methoden aufruft.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Finalizer sollten möglichst vermieden werden, da durch Verfolgung der Objektlebensdauer zusätzliche Leistung beansprucht wird. Der Garbage Collector wird den Finalizer ausgeführt werden, bevor sie das Objekt erfasst. Dies bedeutet, dass zwei Sammlungen erforderlich, um das Objekt zu erfassen. Ein leerer Finalizer verursacht dieses zusätzlichen Mehraufwand ohne nutzen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Entfernen Sie den leeren Finalizer. Wenn ein Finalizer für das Debuggen erforderlich ist, schließen Sie den gesamten Finalizer in `#if DEBUG / #endif` Direktiven.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Meldung von dieser Regel. Der Abschluss unterdrückt, wird die Leistung verringert, und bietet keine Vorteile.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ein leerer Finalizer, die entfernt werden soll, einen Finalizer, der im eingeschlossen werden soll, `#if DEBUG / #endif` -Direktiven und einen Finalizer, bei der `#if DEBUG / #endif` Direktiven ordnungsgemäß.  
  
 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]