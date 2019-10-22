---
title: 'CA1031: allgemeine Ausnahme Typen nicht auffangen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2696446ee2b257b78559909c0cba672cded39943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661893"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Allgemeine Ausnahmetypen nicht auffangen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine allgemeine Ausnahme, wie z. b. <xref:System.Exception?displayProperty=fullName> oder <xref:System.SystemException?displayProperty=fullName>, wird in einer `catch`-Anweisung abgefangen, oder es wird eine allgemeine catch-Klausel wie `catch()` verwendet.

## <a name="rule-description"></a>Regelbeschreibung
 Allgemeine Ausnahmen sollten nicht abgefangen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fangen Sie eine spezifischere Ausnahme ab, oder lösen Sie die allgemeine Ausnahme erneut als letzte Anweisung im `catch`-Block aus.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Durch das Abfangen allgemeiner Ausnahme Typen können Lauf Zeit Probleme beim Bibliotheks Benutzer ausgeblendet und das Debugging erschwert werden.

> [!NOTE]
> Beginnend mit dem [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] werden vom Common Language Runtime (CLR) keine beschädigten Zustands Ausnahmen, die im Betriebssystem auftreten, und verwalteter Code (z. b. Zugriffs Verletzungen in [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]) nicht mehr von verwaltetem Code behandelt. Wenn Sie eine Anwendung in der [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] oder höheren Versionen kompilieren und die Behandlung von beschädigten Zustands Ausnahmen beibehalten möchten, können Sie das <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>-Attribut auf die Methode anwenden, die die Corrupted State Exception behandelt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt, und einen Typ, der den `catch`-Block ordnungsgemäß implementiert.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2200: Erneut ausführen, um Stapeldetails beizubehalten](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
