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
ms.openlocfilehash: 648c59e2660c0509edfcf65ac50bf8791bc5896e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920118"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Assemblys mit ComVisibleAttribute markieren.

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Assembly verfügt nicht über die <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> angewendet werden.

## <a name="rule-description"></a>Regelbeschreibung
 Die <xref:System.Runtime.InteropServices.ComVisibleAttribute> Attribut bestimmt, wie COM-Clients für verwalteten Code zugreifen. Gute Entwurfsprinzipien verlangen, dass die COM-Sichtbarkeit durch Assemblys explizit angegeben wird. COM-Sichtbarkeit für eine gesamte Assembly festgelegt, und klicken Sie dann für einzelne Typen und Typmember überschrieben werden kann. Wenn das Attribut nicht vorhanden ist, sind die Inhalte der Assembly für COM-Clients sichtbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie das Attribut auf die Assembly ein. Wenn Sie nicht, dass die Assembly für COM-Clients sichtbar ist möchten, wenden Sie das Attribut, und setzen ihren Wert auf `false`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie die Assembly sichtbar sein soll, wenden Sie das Attribut, und setzen ihren Wert auf `true`.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Assembly, die <xref:System.Runtime.InteropServices.ComVisibleAttribute> Attribut angewendet, um zu verhindern, dass es für COM-Clients nicht angezeigt werden.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Siehe auch

- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)
- [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)