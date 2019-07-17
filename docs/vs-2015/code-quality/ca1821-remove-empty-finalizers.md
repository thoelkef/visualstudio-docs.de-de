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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5a6175871e74bf3cb99610dce0926f0982f331d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201671"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Leere Finalizer entfernen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ implementiert einen Finalizer, der leer ist, nur den Basistypfinalizer aufruft, oder ruft nur bedingt ausgegebene Methoden.

## <a name="rule-description"></a>Regelbeschreibung
 Finalizer sollten möglichst vermieden werden, da durch Verfolgung der Objektlebensdauer zusätzliche Leistung beansprucht wird. Der Garbage Collector wird den Finalizer ausgeführt werden, bevor das Objekt freigegeben. Dies bedeutet, dass zwei Sammlungen erforderlich, um das Objekt gesammelt werden. Ein leerer Finalizer verursacht dies zusätzlichen Mehraufwand ohne nutzen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie die leeren Finalizer. Wenn ein Finalizer für das Debuggen erforderlich ist, schließen Sie den gesamten Finalizer in `#if DEBUG / #endif` Anweisungen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Meldung von dieser Regel. Abschluss nicht unterdrückt wird die Leistung verringert, und bietet keine Vorteile.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein leerer Finalizer, der entfernt werden soll, einen Finalizer, der in eingeschlossen werden soll `#if DEBUG / #endif` -Direktiven und einen Finalizer, der verwendet die `#if DEBUG / #endif` Direktiven ordnungsgemäß.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
