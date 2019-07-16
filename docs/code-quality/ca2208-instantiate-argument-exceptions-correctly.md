---
title: 'CA2208: Argumentausnahmen korrekt instanziieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2110a8d0b58d87a4554971cf00af6441d293aa91
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975893"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Argumentausnahmen korrekt instanziieren.

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Möglichen Ursachen gehören die folgenden Situationen:

- Wird aufgerufen, der (parameterlose) Standardkonstruktor eines Ausnahmetyps, der oder abgeleitet wird, <xref:System.ArgumentException>.

- Ein falsches Zeichenfolgenargument wird an einen parametrisierten Konstruktor eines Ausnahmetyps, der oder abgeleitet wird, übergeben <xref:System.ArgumentException>.

## <a name="rule-description"></a>Regelbeschreibung

Anstelle von Aufrufen des Standardkonstruktors, rufen Sie die Konstruktorüberladung, die eine aussagekräftigere Ausnahmemeldung bereitgestellt werden können. Die Ausnahmemeldung sollten als Ziel den Entwickler und stellen Sie klar die fehlerbedingung und Informationen zum Korrigieren oder die Ausnahme verhindern.

Die Signaturen der Konstruktoren von mit einem und zwei Zeichenfolgen <xref:System.ArgumentException> und seinen abgeleiteten Typen sind nicht konsistent in Bezug auf die Position `message` und `paramName` Parameter. Stellen Sie sicher, dass diese Konstruktoren mit den richtigen Argumenten aufgerufen werden. Die Signaturen lauten wie folgt aus:

- <xref:System.ArgumentException>(String `message`)
- <xref:System.ArgumentException>(String `message`, Zeichenfolge `paramName`)
- <xref:System.ArgumentNullException>(String `paramName`)
- <xref:System.ArgumentNullException>(String `paramName`, Zeichenfolge `message`)
- <xref:System.ArgumentOutOfRangeException>(String `paramName`)
- <xref:System.ArgumentOutOfRangeException>(String `paramName`, Zeichenfolge `message`)
- <xref:System.DuplicateWaitObjectException>(String `parameterName`)
- <xref:System.DuplicateWaitObjectException>(String `parameterName`, Zeichenfolge `message`)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, rufen einen Konstruktor, eine Meldung und/oder einen Parameternamen an, und stellen Sie sicher, dass die Argumente für den Typ des entsprechenden <xref:System.ArgumentException> aufgerufen wird.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, nur, wenn Sie ein parametrisierter Konstruktor mit den richtigen Argumenten aufgerufen wird.

## <a name="example"></a>Beispiel

Der folgende Code zeigt einen Konstruktor, der eine Instanz von nicht ordnungsgemäß instanziiert <xref:System.ArgumentNullException>.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

Der folgende Code wird der vorherige Verstoß durch den Wechsel der Konstruktorargumente korrigiert.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1507: Verwenden Sie "nameof" anstelle von Zeichenfolge](ca1507.md)