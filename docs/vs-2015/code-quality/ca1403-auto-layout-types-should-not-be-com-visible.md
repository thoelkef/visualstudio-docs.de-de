---
title: 'CA1403: Typen mit automatischem Layout sollten nicht sein COM sichtbar | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 807ea553a4e4cf9c1ec349058dbaa6d025075538
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248767"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Werttyp der Component Object Model (COM) sichtbar ist mit markiert die <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> -Attributsatz auf <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Runtime.InteropServices.LayoutKind> Layouttypen werden von der common Language Runtime verwaltet. Das Layout dieser Typen kann zwischen Versionen von .NET Framework ändern, die COM-Clients unterbrochen wird, die ein bestimmtes Layout erwarten. Beachten Sie, dass bei der <xref:System.Runtime.InteropServices.StructLayoutAttribute> Attribut nicht angegeben ist, der C#-, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], und geben Sie die C++-Compiler die <xref:System.Runtime.InteropServices.LayoutKind> Layout für Werttypen.

 Sofern nicht anders markiert ist, werden alle öffentliche nicht generische Typen für COM sichtbar; alle nicht öffentliche und generische Typen sind für COM nicht sichtbar Um falsch positive Ergebnisse zu reduzieren, erfordert mit dieser Regel jedoch die COM-Sichtbarkeit des Typs explizit angegeben werden; die übergeordnete Assembly muss markiert sein, mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> festgelegt `false` und der Typ markiert werden muss, mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute> festgelegt `true`.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Wert von der <xref:System.Runtime.InteropServices.StructLayoutAttribute> Attribut <xref:System.Runtime.InteropServices.LayoutKind> oder <xref:System.Runtime.InteropServices.LayoutKind>, oder ändern Sie den Typ für COM nicht sichtbar

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein Typ, der gegen die Regel verstößt und ein Typ, der die Regel erfüllt.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1408: AutoDual ClassInterfaceType nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Siehe auch
 [Einführung in die Klassenschnittstelle](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) [Qualifizieren von .NET-Typen für die Interoperation](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [Interoperation mit nicht verwaltetem Code](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



