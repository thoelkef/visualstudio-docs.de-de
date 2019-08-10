---
title: 'CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5014bfe809cb5d56a22e971833128d1f48d77319
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922964"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen.

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Eine öffentliche oder geschützte Methode in einem öffentlichen Typ weist mehr als drei Parameter auf, und die letzten drei Parameter weisen denselben Typ auf.

## <a name="rule-description"></a>Regelbeschreibung
Verwenden Sie ein Parameter Array anstelle von wiederholten Argumenten, wenn die genaue Anzahl der Argumente unbekannt ist und die Variablen Argumente denselben Typ aufweisen oder als derselbe Typ übergeben werden können. Die <xref:System.Console.WriteLine%2A> -Methode stellt z. b. eine allgemeine Überladung bereit, die ein Parameter Array verwendet, um <xref:System.Object> eine beliebige Anzahl von Argumenten zu akzeptieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie die wiederholten Argumente durch ein Parameter Array.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist immer sicher, eine Warnung aus dieser Regel zu unterdrücken. Dieser Entwurf kann jedoch Probleme mit der Benutzerfreundlichkeit verursachen.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

[!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]