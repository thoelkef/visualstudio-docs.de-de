---
title: 'CA1031: Allgemeine Ausnahmetypen nicht auffangen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab2b235037e68d7c824d144d29dfb58ac8c5c066
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Allgemeine Ausnahmetypen nicht auffangen
|||  
|-|-|  
|TypeName|DoNotCatchGeneralExceptionTypes|  
|CheckId|CA1031|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine allgemeine Ausnahme wie z. B. <xref:System.Exception?displayProperty=fullName> oder <xref:System.SystemException?displayProperty=fullName> aufgetreten ist, in eine `catch` -Anweisung oder einer allgemeinen Catch-Klausel, z. B. `catch()` verwendet wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Allgemeine Ausnahmen sollten nicht abgefangen werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fangen Sie eine spezifischere Ausnahme oder der letzten Anweisung in die allgemeine Ausnahme erneut ausgelöst der `catch` Block.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel. Allgemeine Ausnahmetypen abfangen können zur Laufzeit Probleme aus der Bibliotheksbenutzer ausblenden und können Debuggen erschweren.  
  
> [!NOTE]
>  Beginnend mit der [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], die common Language Runtime (CLR) bietet mehr beschädigten Zustandsausnahmen, die auftreten, in das Betriebssystem und verwalteten Code, z. B. zugriffsverletzungen in [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], von verwaltetem Code behandelt werden. Wenn Sie eine Anwendung kompilieren möchten die [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] oder höheren Versionen und Verwalten von Behandlung von beschädigten Zustandsausnahmen die, Sie anwenden können die <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> -Attribut auf die Methode, die beschädigten Zustandsausnahme verarbeitet.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ein Typ, der mit dieser Regel verletzt und einen Typ, ordnungsgemäß implementiert, die `catch` Block.  
  
 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2200: Erneut ausführen, um Stapeldetails beizubehalten](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)