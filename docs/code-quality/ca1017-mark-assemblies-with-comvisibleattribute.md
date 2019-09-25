---
title: 'CA1017: Assemblys mit ComVisibleAttribute markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 073332738a01cb299b2b185c6fca20131222f981
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236253"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Assemblys mit ComVisibleAttribute markieren.

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Auf eine Assembly wird das <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> -Attribut nicht angewendet.

## <a name="rule-description"></a>Regelbeschreibung
Das <xref:System.Runtime.InteropServices.ComVisibleAttribute> -Attribut bestimmt, wie com-Clients auf verwalteten Code zugreifen. Gute Entwurfsprinzipien verlangen, dass die COM-Sichtbarkeit durch Assemblys explizit angegeben wird. Die COM-Sichtbarkeit kann für eine gesamte Assembly festgelegt und dann für einzelne Typen und Typmember überschrieben werden. Wenn das Attribut nicht vorhanden ist, ist der Inhalt der Assembly für com-Clients sichtbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Fügen Sie der Assembly das-Attribut hinzu, um einen Verstoß gegen diese Regel zu beheben. Wenn Sie nicht möchten, dass die Assembly für com-Clients sichtbar ist, wenden Sie das-Attribut an, `false`und legen Sie dessen Wert auf fest.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie möchten, dass die Assembly sichtbar ist, wenden Sie das-Attribut an, `true`und legen Sie dessen Wert auf fest.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Assembly, für die <xref:System.Runtime.InteropServices.ComVisibleAttribute> das-Attribut angewendet wurde, um zu verhindern, dass Sie für com-Clients sichtbar ist.

[!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
[!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Siehe auch

- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)
- [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)