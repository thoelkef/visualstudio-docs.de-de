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
ms.openlocfilehash: 9f9425ab1ea9eadd3bd06d950118ce83ba5c35f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231648"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Argumentausnahmen korrekt instanziieren.

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Zu den möglichen Ursachen gehören die folgenden Situationen:

- Der standardmäßige (parameterlose) Konstruktor eines Ausnahme Typs, der oder von <xref:System.ArgumentException>abgeleitet ist, wird aufgerufen.

- Ein falsches Zeichen folgen Argument wird an einen parametrisierten Konstruktor eines Ausnahme Typs übergeben, der oder von <xref:System.ArgumentException>abgeleitet ist.

## <a name="rule-description"></a>Regelbeschreibung

Anstatt den Standardkonstruktor aufzurufen, rufen Sie eine der Konstruktorüberladungen auf, die eine aussagekräftigere Ausnahme Meldung bereitstellen lassen. Die Ausnahme Meldung sollte den Entwickler als Ziel haben und die Fehlerbedingung und die Vorgehensweise zur Behebung oder Vermeidung der Ausnahme eindeutig erläutern.

Die Signaturen der einen und zwei zeichenfolgenkonstruktoren von <xref:System.ArgumentException> und der abgeleiteten Typen sind in Bezug auf die Position `paramName` `message` und die Parameter nicht konsistent. Stellen Sie sicher, dass diese Konstruktoren mit den richtigen Zeichen folgen Argumenten aufgerufen werden. Die Signaturen lauten wie folgt:

- <xref:System.ArgumentException>(Zeichen `message`Folge)
- <xref:System.ArgumentException>(Zeichen `message`Folge, `paramName`Zeichenfolge)
- <xref:System.ArgumentNullException>(Zeichen `paramName`Folge)
- <xref:System.ArgumentNullException>(Zeichen `paramName`Folge, `message`Zeichenfolge)
- <xref:System.ArgumentOutOfRangeException>(Zeichen `paramName`Folge)
- <xref:System.ArgumentOutOfRangeException>(Zeichen `paramName`Folge, `message`Zeichenfolge)
- <xref:System.DuplicateWaitObjectException>(Zeichen `parameterName`Folge)
- <xref:System.DuplicateWaitObjectException>(Zeichen `parameterName`Folge, `message`Zeichenfolge)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, müssen Sie einen Konstruktor aufrufen, der eine Nachricht, einen Parameternamen oder beides annimmt, und sicherstellen, dass die Argumente für <xref:System.ArgumentException> den aufgerufenen Typ ordnungsgemäß sind.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel nur zu unterdrücken, wenn ein parametrisierter Konstruktor mit den richtigen Zeichen folgen Argumenten aufgerufen wird.

## <a name="example"></a>Beispiel

Der folgende Code zeigt einen Konstruktor, der eine Instanz von <xref:System.ArgumentNullException>falsch instanziiert.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

Mit dem folgenden Code wird der vorherige Verstoß korrigiert, indem die Konstruktorargumente gewechselt werden.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1507: Nameof anstelle der Zeichenfolge verwenden](ca1507.md)