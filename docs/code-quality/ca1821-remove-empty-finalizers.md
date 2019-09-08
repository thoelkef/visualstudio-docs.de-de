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
ms.openlocfilehash: f616547738c7c58d61289b2be71c8e56a1a427c8
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766075"
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

Vermeiden Sie Finalizer, wenn dies möglich ist, da der zusätzliche Leistungs Aufwand bei der Nachverfolgung der Objekt Lebensdauer auftritt. Der Garbage Collector führt den Finalizer aus, bevor das Objekt erfasst wird. Dies bedeutet, dass mindestens zwei Auflistungen erforderlich sind, um das Objekt zu erfassen. Ein leerer Finalizer verursacht diesen zusätzlichen Aufwand ohne jeglichen Vorteil.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Entfernen Sie den leeren Finalizer. Wenn ein Finalizer für das Debuggen erforderlich ist, schließen Sie den gesamten Finalizer in `#if DEBUG / #endif` Direktiven ein.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Meldung von dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen leeren Finalizer, der entfernt werden soll, einen Finalizer, der in `#if DEBUG / #endif` -Direktiven eingeschlossen werden soll, und einen Finalizer, der die `#if DEBUG / #endif` -Direktiven ordnungsgemäß verwendet.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]
