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
ms.openlocfilehash: 520c9a066a4a902d5e9243baf1a8d8dec1b78e29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542401"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Allgemeine Ausnahmetypen nicht auffangen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine allgemeine Ausnahme, z <xref:System.Exception?displayProperty=fullName> . b. oder <xref:System.SystemException?displayProperty=fullName> , wird in einer- `catch` Anweisung abgefangen, oder es wird eine allgemeine catch-Klausel wie `catch()` verwendet.

## <a name="rule-description"></a>Beschreibung der Regel
 Allgemeine Ausnahmen sollten nicht abgefangen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fangen Sie eine spezifischere Ausnahme ab, oder lösen Sie die allgemeine Ausnahme erneut als letzte Anweisung im- `catch` Block aus.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Durch das Abfangen allgemeiner Ausnahme Typen können Lauf Zeit Probleme beim Bibliotheks Benutzer ausgeblendet und das Debugging erschwert werden.

> [!NOTE]
> Ab werden vom [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] Common Language Runtime (CLR) keine beschädigten Zustands Ausnahmen mehr bereitstellt, die im Betriebssystem auftreten, und verwalteter Code (z. b. Zugriffs Verletzungen in), der [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] von verwaltetem Code behandelt werden soll. Wenn Sie eine Anwendung in oder höheren Versionen kompilieren [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] und die Behandlung von beschädigten Zustands Ausnahmen beibehalten möchten, können Sie das- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Attribut auf die Methode anwenden, die die Corrupted State Exception behandelt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt, und einen Typ, der den-Block ordnungsgemäß implementiert `catch` .

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2200: Erneut ausführen, um Stapeldetails beizubehalten.](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
