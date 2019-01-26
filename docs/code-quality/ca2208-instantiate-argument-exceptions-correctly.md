---
title: 'CA2208: Argumentausnahmen korrekt instanziieren.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 8ef4e23f0200f17c0f6d59789538352d9e1676ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980179"
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

- Wird aufgerufen, der (parameterlose) Standardkonstruktor eines Ausnahmetyps, der ist, oder davon abgeleitet <xref:System.ArgumentException>.

- Ein falsches Zeichenfolgenargument wird an einen parametrisierten Konstruktor eines Ausnahmetyps, der ist, oder davon abgeleitet übergeben <xref:System.ArgumentException>.

## <a name="rule-description"></a>Regelbeschreibung

Anstelle von Aufrufen des Standardkonstruktors, rufen Sie die Konstruktorüberladung, die eine aussagekräftigere Ausnahmemeldung bereitgestellt werden können. Die Ausnahmemeldung sollten als Ziel den Entwickler und stellen Sie klar die fehlerbedingung und Informationen zum Korrigieren oder die Ausnahme verhindern.

Die Signaturen der Konstruktoren von mit einem und zwei Zeichenfolgen <xref:System.ArgumentException> und seinen abgeleiteten Typen sind nicht konsistent in Bezug auf die `message` und `paramName` Parameter. Stellen Sie sicher, dass diese Konstruktoren mit den richtigen Argumenten aufgerufen werden. Die Signaturen lauten wie folgt aus:

 <xref:System.ArgumentException>(String `message`)

 <xref:System.ArgumentException>(String `message`, Zeichenfolge `paramName`)

 <xref:System.ArgumentNullException>(String `paramName`)

 <xref:System.ArgumentNullException>(String `paramName`, Zeichenfolge `message`)

 <xref:System.ArgumentOutOfRangeException>(String `paramName`)

 <xref:System.ArgumentOutOfRangeException>(String `paramName`, Zeichenfolge `message`)

 <xref:System.DuplicateWaitObjectException>(String `parameterName`)

 <xref:System.DuplicateWaitObjectException>(String `parameterName`, Zeichenfolge `message`)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen einen Konstruktor, eine Meldung und/oder einen Parameternamen an, und stellen Sie sicher, dass die Argumente für den Typ des entsprechenden <xref:System.ArgumentException> aufgerufen wird.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, nur, wenn Sie ein parametrisierter Konstruktor mit den richtigen Argumenten aufgerufen wird.

## <a name="example-1"></a>Beispiel 1
 Das folgende Beispiel zeigt einen Konstruktor, der eine Instanz des Typs "ArgumentNullException" nicht ordnungsgemäß instanziiert wird.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example-2"></a>Beispiel 2
 Im folgende Beispiel werden der oben genannten Verstoß korrigiert, durch den Wechsel der Konstruktorargumente.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]