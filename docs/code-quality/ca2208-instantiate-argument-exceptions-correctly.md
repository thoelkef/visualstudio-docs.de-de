---
title: 'CA2208: Argumentausnahmen korrekt instanziieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc4a13746182136e10cb550bb7235a8bad2528fd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Argumentausnahmen korrekt instanziieren
|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Mögliche Ursachen sind die folgenden Situationen:

-   Eine Puffermethode wurde der (parameterlose) Standardkonstruktor eines Ausnahmetyps wird, die ist oder davon abgeleitet wurde <xref:System.ArgumentException>.

-   Ein falsches Zeichenfolgenargument wird an einen parametrisierten Konstruktor eines Ausnahmetyps wird, die ist oder davon abgeleitet wurde übergeben <xref:System.ArgumentException>.

## <a name="rule-description"></a>Regelbeschreibung
 Statt den Standardkonstruktor aufrufen, rufen Sie die Konstruktorüberladung, die eine aussagekräftigere Ausnahmemeldung bereitgestellt werden können. Die Ausnahmemeldung sollte den Entwickler ausgerichtet und klar Fehlerzustand und das korrigieren oder die Ausnahme verhindern.

 Die Signaturen der Konstruktoren von mit einer oder zwei Zeichenfolgen <xref:System.ArgumentException> und die abgeleiteten Typen sind nicht konsistent in Bezug auf die `message` und `paramName` Parameter. Stellen Sie sicher, dass diese Konstruktoren mit den richtigen Zeichenfolgenargumenten aufgerufen werden. Die Signaturen lauten wie folgt:

 <xref:System.ArgumentException>(String `message`)

 <xref:System.ArgumentException>(String `message`, Zeichenfolge `paramName`)

 <xref:System.ArgumentNullException>(String `paramName`)

 <xref:System.ArgumentNullException>(String `paramName`, Zeichenfolge `message`)

 <xref:System.ArgumentOutOfRangeException>(String `paramName`)

 <xref:System.ArgumentOutOfRangeException>(String `paramName`, Zeichenfolge `message`)

 <xref:System.DuplicateWaitObjectException>(String `parameterName`)

 <xref:System.DuplicateWaitObjectException>(String `parameterName`, Zeichenfolge `message`)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie einen Konstruktor, der eine Meldung, einen Parameternamen ein oder beide akzeptiert und stellen Sie sicher, dass die Argumente für den Typ des richtigen <xref:System.ArgumentException> aufgerufen werden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, nur, wenn Sie ein parametrisierter Konstruktor mit den richtigen Zeichenfolgenargumenten aufgerufen wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Konstruktor, der eine Instanz des Typs ArgumentNullException nicht ordnungsgemäß instanziiert wird.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example"></a>Beispiel
 Im folgende Beispiel werden der oben genannten Verstoß durch den Wechsel Konstruktorargumente korrigiert.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]