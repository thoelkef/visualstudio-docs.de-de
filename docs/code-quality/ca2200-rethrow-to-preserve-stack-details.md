---
title: 'CA2200: Erneut ausführen, um Stapeldetails beizubehalten.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5cf7fc6e31b9250392fc3ea447a5b91225640a50
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231907"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Erneut ausführen, um Stapeldetails beizubehalten.

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird explizit in der `throw` Anweisung angegeben.

## <a name="rule-description"></a>Regelbeschreibung

Sobald eine Ausnahme ausgelöst wird, ist ein Teil der Informationen, die er enthält, die Stapel Überwachung. Die Stapel Überwachung ist eine Liste der Methoden Aufrufhierarchie, die mit der-Methode beginnt, die die Ausnahme auslöst und mit der-Methode endet, die die Ausnahme abfängt. Wenn eine Ausnahme erneut ausgelöst wird, indem die Ausnahme in der `throw` Anweisung angegeben wird, wird die Stapel Überwachung bei der aktuellen Methode neu gestartet, und die Liste der Methodenaufrufe zwischen der ursprünglichen Methode, die die Ausnahme ausgelöst hat, und der aktuellen Methode gehen verloren. Um die ursprünglichen Stapel Überwachungsinformationen mit der Ausnahme beizubehalten, verwenden Sie `throw` die-Anweisung, ohne die Ausnahme anzugeben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, lösen Sie die Ausnahme erneut aus, ohne die Ausnahme explizit anzugeben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode `CatchAndRethrowExplicitly`,, die gegen die Regel verstößt, und eine `CatchAndRethrowImplicitly`Methode,, die die Regel erfüllt.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]