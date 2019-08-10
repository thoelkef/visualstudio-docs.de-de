---
title: 'CA1821: Leere Finalizer entfernen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c8c4d4ca04c7a9a21cd1e80e4dc06e8d5a92c2f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921376"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Leere Finalizer entfernen.

|||
|-|-|
|TypeName|Removeemptyfinalizers|
|CheckId|CA1821|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Ein Typ implementiert einen Finalizer, der leer ist, nur den Basistyp Finalizer aufruft oder nur bedingt ausgegebene Methoden aufruft.

## <a name="rule-description"></a>Regelbeschreibung
Finalizer sollten möglichst vermieden werden, da durch Verfolgung der Objektlebensdauer zusätzliche Leistung beansprucht wird. Der Garbage Collector führt den Finalizer aus, bevor das Objekt erfasst wird. Dies bedeutet, dass zwei Auflistungen erforderlich sind, um das Objekt zu erfassen. Ein leerer Finalizer verursacht diesen zusätzlichen Aufwand ohne jeglichen Vorteil.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Entfernen Sie den leeren Finalizer. Wenn ein Finalizer für das Debuggen erforderlich ist, schließen Sie den gesamten Finalizer in `#if DEBUG / #endif` Direktiven ein.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Meldung von dieser Regel. Wenn die Finalisierung nicht unterdrückt wird, verringert sich die Leistung und bietet keine Vorteile.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen leeren Finalizer, der entfernt werden soll, einen Finalizer, der in `#if DEBUG / #endif` -Direktiven eingeschlossen werden soll, und einen Finalizer, der die `#if DEBUG / #endif` -Direktiven ordnungsgemäß verwendet.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]