---
title: 'CA1017: Assemblys mit ComVisibleAttribute markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 505e5780b8a50113aaf98ea7dbac767d280bebb6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662066"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Assemblys mit ComVisibleAttribute markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Auf eine Assembly wird das <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>-Attribut nicht angewendet.

## <a name="rule-description"></a>Regelbeschreibung
 Das <xref:System.Runtime.InteropServices.ComVisibleAttribute>-Attribut bestimmt, wie com-Clients auf verwalteten Code zugreifen. Gute Entwurfsprinzipien verlangen, dass die COM-Sichtbarkeit durch Assemblys explizit angegeben wird. Die COM-Sichtbarkeit kann für eine gesamte Assembly festgelegt und dann für einzelne Typen und Typmember überschrieben werden. Wenn das Attribut nicht vorhanden ist, ist der Inhalt der Assembly für com-Clients sichtbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Fügen Sie der Assembly das-Attribut hinzu, um einen Verstoß gegen diese Regel zu beheben. Wenn Sie nicht möchten, dass die Assembly für com-Clients sichtbar ist, wenden Sie das-Attribut an, und legen Sie dessen Wert auf `false` fest.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie möchten, dass die Assembly sichtbar ist, wenden Sie das-Attribut an, und legen Sie dessen Wert auf `true` fest.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Assembly, für die das <xref:System.Runtime.InteropServices.ComVisibleAttribute>-Attribut angewendet wurde, um zu verhindern, dass Sie für com-Clients sichtbar ist.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>Siehe auch
 Interoperabilität [mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [qualifizieren von .NET-Typen für die Interoperation](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
