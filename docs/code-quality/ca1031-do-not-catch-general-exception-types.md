---
title: 'CA1031: Allgemeine Ausnahmetypen nicht auffangen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7b1610d07e5e38632056df237d284b40b6f101c6
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922903"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Allgemeine Ausnahmetypen nicht auffangen.

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Eine <xref:System.Exception?displayProperty=fullName> allgemeine Ausnahme <xref:System.SystemException?displayProperty=fullName> ,z`catch` . b. oder, wird in einer-Anweisung abgefangen, oder eswirdeineallgemeinecatch-Klauselwieverwendet.`catch()`

## <a name="rule-description"></a>Regelbeschreibung
Allgemeine Ausnahmen sollten nicht abgefangen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, fangen Sie eine spezifischere Ausnahme ab, oder lösen Sie die allgemeine Ausnahme erneut als letzte `catch` Anweisung im-Block aus.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel. Durch das Abfangen allgemeiner Ausnahme Typen können Lauf Zeit Probleme beim Bibliotheks Benutzer ausgeblendet und das Debugging erschwert werden.

> [!NOTE]
> Ab .NET Framework 4 werden von der Common Language Runtime (CLR) keine beschädigten Zustands Ausnahmen mehr bereitstellt, die im Betriebssystem auftreten, und verwalteter Code, z. b [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]. Zugriffs Verletzungen in, der von verwaltetem Code behandelt werden soll. Wenn Sie eine Anwendung in der .NET Framework 4 oder einer höheren Version kompilieren und die Behandlung von beschädigten Zustands Ausnahmen beibehalten möchten, können Sie das <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> -Attribut auf die Methode anwenden, die die Corrupted State Exception behandelt.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt, und einen Typ, `catch` der den-Block ordnungsgemäß implementiert.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2200: Erneut auslösen, um Stapel Details beizubehalten](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)