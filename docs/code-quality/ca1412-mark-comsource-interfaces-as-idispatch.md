---
title: 'CA1412: ComSource-Schnittstellen als IDispatch | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b2523397f59affa2d7e1e60e69e7ba2047438135
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: ComSource-Schnittstellen als IDispatch markieren
|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Typ ist markiert, mit der <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> Attribut und mindestens eine der angegebenen Schnittstellen ist nicht mit markiert die <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> -Attributsatz zur der `InterfaceIsDispatch` Wert.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>wird verwendet, um die Ereignisschnittstellen zu identifizieren, die eine Klasse, Component Object Model (COM)-Clients bereitstellt. Diese Schnittstellen müssen verfügbar gemacht werden, als `InterfaceIsIDispatch` Visual Basic 6-COM-Clients ereignisbenachrichtigungen erhalten können. Standardmäßig, wenn eine Schnittstelle nicht gekennzeichnet ist die <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> -Attribut, er wird als eine duale Schnittstelle verfügbar gemacht.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, hinzufügen oder Ändern der <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> Attribut, damit dessen Wert InterfaceIsIDispatch für alle Schnittstellen auf festgelegt ist, die mit angegeben sind die <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> Attribut.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einer Klasse, in denen eine der Schnittstellen die Regel verletzt.  
  
 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1408: AutoDual ClassInterfaceType nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)