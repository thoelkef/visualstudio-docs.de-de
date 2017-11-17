---
title: 'CA1403: Typen mit automatischem Layout sollten nicht COM sichtbar sein | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e5f8617b7ed5f0bec9ecaa2f4fbca1653cee46f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein
|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein sichtbar Werttyp Component Object Model (COM) wird gekennzeichnet, mit der <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> -Attributsatz zur <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 <xref:System.Runtime.InteropServices.LayoutKind>Layout-Typen werden von der common Language Runtime verwaltet. Das Layout dieser Typen kann zwischen verschiedenen Versionen von .NET Framework geändert, was die COM-Clients unterbrochen wird, die ein bestimmtes Layout erwarten. Beachten Sie, dass bei der <xref:System.Runtime.InteropServices.StructLayoutAttribute> Attribut nicht angegeben wird, die C#-, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], und geben Sie die C++-Compiler die <xref:System.Runtime.InteropServices.LayoutKind> Layout für Werttypen.  
  
 Sofern nicht anders markiert ist, sind alle öffentliche, nicht generische Typen für COM sichtbar. alle nicht öffentliche und generischen Typen sind nicht für COM sichtbar Allerdings erfordert diese Regel um falsch positive Ergebnisse zu reduzieren, die COM-Sichtbarkeit des Typs explizit angegeben werden; die enthaltende Assembly muss mit dem gekennzeichnet werden die <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> festgelegt `false` und der Typ muss markiert sein, mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute> festgelegt `true`.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Wert von der <xref:System.Runtime.InteropServices.StructLayoutAttribute> -Attribut <xref:System.Runtime.InteropServices.LayoutKind> oder <xref:System.Runtime.InteropServices.LayoutKind>, oder machen Sie den Typ für COM nicht sichtbar  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Typ, der die Regel verletzt und ein Typ, der die Regel erfüllt.  
  
 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1408: AutoDual ClassInterfaceType nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Einführung in die Klassenschnittstelle](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)