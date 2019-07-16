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
ms.openlocfilehash: e9746119c746679817076c86e3d5a9080cec30d9
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744689"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Allgemeine Ausnahmetypen nicht auffangen.

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine allgemeine Ausnahme wie z. B. <xref:System.Exception?displayProperty=fullName> oder <xref:System.SystemException?displayProperty=fullName> in abgefangen eine `catch` -Anweisung oder eine allgemeine Catch-Klausel, z. B. `catch()` verwendet wird.

## <a name="rule-description"></a>Regelbeschreibung
 Allgemeine Ausnahmen sollten nicht abgefangen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, eine spezifischere Ausnahme abfangen und erneut auslösen, die allgemeine Ausnahme der letzten Anweisung in der `catch` Block.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel. Allgemeine Ausnahmetypen abfangen können blenden Sie aus, von dem Benutzer einer Bibliothek Probleme zur Laufzeit und können Sie das Debuggen erschwert.

> [!NOTE]
> Ab .NET Framework 4, bietet die common Language Runtime (CLR) nicht mehr hervorgerufenen Ausnahmen, die auftreten, in das Betriebssystem und verwalteten Code, z. B.-zugriffsverletzungen in [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], um die von verwaltetem Code behandelt werden. Wenn Sie die Kompilierung einer Anwendung in .NET Framework 4 oder höher möchten und Behandlung von Beschädigungen hervorgerufenen Ausnahmen beibehalten, können Sie übernehmen die <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> -Attribut auf die Methode, die die Ausnahme zu beschädigtem Zustand behandelt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein Typ, die gegen diese Regel verstößt und ein Typ, der ordnungsgemäß implementiert die `catch` Block.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2200: Erneut ausführen Sie, um Stapeldetails beizubehalten](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)