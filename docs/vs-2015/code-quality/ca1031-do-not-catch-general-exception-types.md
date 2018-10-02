---
title: 'CA1031: Allgemeine Ausnahmetypen nicht auffangen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fee08bdc2b93687a5415fdbd137c48f816f4acbb
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589733"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Allgemeine Ausnahmetypen nicht auffangen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1031: Allgemeine Ausnahmetypen nicht auffangen](https://docs.microsoft.com/visualstudio/code-quality/ca1031-do-not-catch-general-exception-types).

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Allgemeine Ausnahmetypen abfangen können blenden Sie aus, von dem Benutzer einer Bibliothek Probleme zur Laufzeit und können Sie das Debuggen erschwert.

> [!NOTE]
>  Beginnend mit der [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], die common Language Runtime (CLR) bietet mehr hervorgerufenen Ausnahmen, die auftreten, in das Betriebssystem und verwalteten Code, z. B.-zugriffsverletzungen in [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], um die von verwaltetem Code behandelt werden. Sollten Sie Kompilieren einer Anwendung in der [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] oder höher und Verwalten von Beschädigungen hervorgerufenen Ausnahmen behandeln, können Sie anwenden der <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> -Attribut auf die Methode, die die Ausnahme zu beschädigtem Zustand behandelt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein Typ, die gegen diese Regel verstößt und ein Typ, der ordnungsgemäß implementiert die `catch` Block.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2200: Erneut ausführen, um Stapeldetails beizubehalten](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)



