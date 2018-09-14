---
title: 'CA2200: Erneut ausführen, um Stapeldetails beizubehalten'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1cc85931ed51bcd3df3a044452af59a530746805
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550885"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Erneut ausführen, um Stapeldetails beizubehalten

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird explizit angegeben, der `throw` Anweisung.

## <a name="rule-description"></a>Regelbeschreibung

Sobald eine Ausnahme ausgelöst wird, ist Teil der Informationen, die es enthält die stapelüberwachung. Die stapelüberwachung ist eine Liste von der Methode Aufrufhierarchie, die mit der Methode beginnt, die die Ausnahme auslöst, und endet mit der Methode, die die Ausnahme abgefangen. Wenn eine Ausnahme erneut ausgelöst wird, durch Angeben der Ausnahme in der `throw` -Anweisung, die stapelüberwachung auf die aktuelle Methode neu gestartet wird und die Liste der Methodenaufrufe zwischen der ursprünglichen Methode, die die Ausnahme ausgelöst hat und die aktuelle Methode geht verloren. Um die ursprüngliche Stapelüberwachungsinformationen mit der Ausnahme zu halten, verwenden Sie die `throw` -Anweisung ohne Angabe der Ausnahme.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, auslösen Sie Ausnahme erneut, ohne die Ausnahme explizit anzugeben.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode, `CatchAndRethrowExplicitly`, die gegen die Regel und eine Methode, `CatchAndRethrowImplicitly`, die die Regel erfüllt.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]