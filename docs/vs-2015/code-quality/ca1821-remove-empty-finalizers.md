---
title: 'CA1821: Leere Finalizer entfernen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 8abb9f00e61c8c24e91921519c706356b6ded16c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589764"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Leere Finalizer entfernen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1821: Leere Finalizer entfernen](https://docs.microsoft.com/visualstudio/code-quality/ca1821-remove-empty-finalizers).

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



