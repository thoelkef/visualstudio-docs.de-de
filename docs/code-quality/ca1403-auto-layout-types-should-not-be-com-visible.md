---
title: 'CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e590514247444d32d0d9a31b2bbc409434cf53c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234831"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein.

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Component Object Model (com) sichtbarer Werttyp ist mit <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> dem-Attribut <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>gekennzeichnet, das auf festgelegt ist.

## <a name="rule-description"></a>Regelbeschreibung

<xref:System.Runtime.InteropServices.LayoutKind>Layouttypen werden vom Common Language Runtime verwaltet. Das Layout dieser Typen kann sich Zwischenversionen von .net ändern, wodurch com-Clients, die ein bestimmtes Layout erwarten, unterbrochen werden. Wenn das <xref:System.Runtime.InteropServices.StructLayoutAttribute> -Attribut nicht angegeben wird, C#geben die-, C++ Visual Basic-und-Compiler [LayoutKind. Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) für Werttypen an.

Sofern nicht anders gekennzeichnet, sind alle öffentlichen, nicht generischen Typen für com sichtbar, und alle nicht öffentlichen und generischen Typen sind für com nicht sichtbar. Um falsch positive Ergebnisse zu reduzieren, erfordert diese Regel jedoch, dass die COM-Sichtbarkeit des Typs explizit angegeben wird. Die <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> enthaltende Assembly muss mit dem auf festgelegten festgelegt werden, `false` und der Typ muss <xref:System.Runtime.InteropServices.ComVisibleAttribute> mit dem `true`auf festgelegten Wert gekennzeichnet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Wert <xref:System.Runtime.InteropServices.StructLayoutAttribute> des Attributs in [LayoutKind. explizit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) oder [LayoutKind. Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), oder machen Sie den Typ für COM unsichtbar.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt, und einen Typ, der die Regel erfüllt.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1408: AutoDual classinterfaketype nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Siehe auch

- [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)