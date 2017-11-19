---
title: "CA1405: Für COM sichtbare Basistypen sollten sein COM sichtbar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 91634d5d46d63165874deded9c5ac67e7d4afa07
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Für COM sichtbare Basistypen sollten für COM sichtbar sein
|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|DependsOnFix|  
  
## <a name="cause"></a>Ursache  
 Ein sichtbarer Typ von Component Object Model (COM) ableitet, ein Typ, der nicht für COM sichtbar ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn ein für COM sichtbarer Typ in einer neuen Version Mitglieder hinzufügt, muss er Abbrüchen strikte Richtlinien zu vermeiden, dass die COM-Clients, die auf die aktuelle Version zu binden. Ein Typ, der nicht für COM sichtbar ist, wird davon ausgegangen, dass sie keinen diese COM-Versionsregeln folgen, wenn neue Elemente hinzugefügt. Wenn jedoch eine COM-sichtbaren Typ leitet sich von der COM-Typ nicht sichtbar und macht eine Klassenschnittstelle <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> oder <xref:System.Runtime.InteropServices.ClassInterfaceType> (Standard), alle öffentlichen Member des Basistyps (es sei denn, sie speziell als COM unsichtbar markiert sind, die wäre redundant) sind für COM verfügbar gemacht Wenn der Basistyp in einer späteren Version neue Member hinzufügt, können zur funktionsunfähigkeit von COM-Clients, die an die Klassenschnittstelle des abgeleiteten Typs binden. Für COM sichtbare Typen sollten nur für COM sichtbare Typen, um das Risiko der Unterbrechung von COM-Clients zu reduzieren abgeleitet sein.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, machen Sie die Basistypen COM sichtbar oder den abgeleiteten Typ für COM sichtbar.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der die Regel verletzt.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Einführung in die Klassenschnittstelle](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)