---
title: 'CA1821: Leere Finalizer entfernen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2e704202773447e353f041df66b05cb5f648c00
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545352"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Leere Finalizer entfernen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|Removeemptyfinalizers|
|CheckId|CA1821|
|Category|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ implementiert einen Finalizer, der leer ist, nur den Basistyp Finalizer aufruft oder nur bedingt ausgegebene Methoden aufruft.

## <a name="rule-description"></a>Beschreibung der Regel
 Finalizer sollten möglichst vermieden werden, da durch Verfolgung der Objektlebensdauer zusätzliche Leistung beansprucht wird. Der Garbage Collector führt den Finalizer aus, bevor das Objekt erfasst wird. Dies bedeutet, dass zwei Auflistungen erforderlich sind, um das Objekt zu erfassen. Ein leerer Finalizer verursacht diesen zusätzlichen Aufwand ohne jeglichen Vorteil.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie den leeren Finalizer. Wenn ein Finalizer für das Debuggen erforderlich ist, schließen Sie den gesamten Finalizer in `#if DEBUG / #endif` Direktiven ein.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Meldung von dieser Regel. Wenn die Finalisierung nicht unterdrückt wird, verringert sich die Leistung und bietet keine Vorteile.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen leeren Finalizer, der entfernt werden soll, einen Finalizer, der in- `#if DEBUG / #endif` Direktiven eingeschlossen werden soll, und einen Finalizer, der die- `#if DEBUG / #endif` Direktiven ordnungsgemäß verwendet.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
