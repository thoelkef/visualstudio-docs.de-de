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
ms.openlocfilehash: e285ead27b8d3d7c674a138d5f06c69a7e88d1fc
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55915607"
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
> Beginnend mit der [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], die common Language Runtime (CLR) bietet mehr hervorgerufenen Ausnahmen, die auftreten, in das Betriebssystem und verwalteten Code, z. B.-zugriffsverletzungen in [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], um die von verwaltetem Code behandelt werden. Sollten Sie Kompilieren einer Anwendung in der [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] oder höher und Verwalten von Beschädigungen hervorgerufenen Ausnahmen behandeln, können Sie anwenden der <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> -Attribut auf die Methode, die die Ausnahme zu beschädigtem Zustand behandelt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein Typ, die gegen diese Regel verstößt und ein Typ, der ordnungsgemäß implementiert die `catch` Block.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2200: Erneut ausführen Sie, um Stapeldetails beizubehalten](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)