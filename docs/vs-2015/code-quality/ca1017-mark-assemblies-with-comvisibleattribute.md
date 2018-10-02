---
title: 'CA1017: Assemblys mit ComVisibleAttribute markieren | Microsoft-Dokumentation'
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
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 931965388bd48ade5a0c9f5045b0399bed40a207
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589644"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Assemblys mit ComVisibleAttribute markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1017: Assemblys mit ComVisibleAttribute markieren](https://docs.microsoft.com/visualstudio/code-quality/ca1017-mark-assemblies-with-comvisibleattribute).

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie die Assembly sichtbar sein soll, wenden Sie das Attribut, und setzen ihren Wert auf `true`.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Assembly, die <xref:System.Runtime.InteropServices.ComVisibleAttribute> Attribut angewendet, um zu verhindern, dass es für COM-Clients nicht angezeigt werden.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>Siehe auch
 [Interoperation mit nicht verwaltetem Code](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Qualifizieren von .NET-Typen für die Interoperation](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)



