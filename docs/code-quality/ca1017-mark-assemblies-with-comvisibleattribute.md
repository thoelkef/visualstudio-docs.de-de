---
title: 'CA1017: Assemblys mit ComVisibleAttribute markieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e4c76efff009c85f9d607611d92d53cad5d2759
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Assemblys mit ComVisibleAttribute markieren
|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine Assembly verfügt nicht über die <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> angewendet werden.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die <xref:System.Runtime.InteropServices.ComVisibleAttribute> Attribut bestimmt, wie COM-Clients für verwalteten Code zugreifen. Gute Entwurfsprinzipien verlangen, dass die COM-Sichtbarkeit durch Assemblys explizit angegeben wird. COM-Sichtbarkeit kann für eine gesamte Assembly festgelegt und anschließend für einzelne Typen und Typmember überschrieben werden. Wenn das Attribut nicht vorhanden ist, ist der Inhalt der Assembly für COM-Clients sichtbar.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie das Attribut auf die Assembly hinzu. Wenn Sie nicht, dass die Assembly für COM-Clients sichtbar sein sollen möchten, wenden Sie das Attribut, und legen Sie dessen Wert auf `false`.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie die Assembly sichtbar sein soll, wenden Sie das Attribut, und legen Sie dessen Wert auf `true`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Assembly, die <xref:System.Runtime.InteropServices.ComVisibleAttribute> Attribut angewendet, um zu verhindern, dass er für COM-Clients nicht angezeigt.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [Interoperation mit nicht verwaltetem Code](/dotnet/framework/interop/index)   
 [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)