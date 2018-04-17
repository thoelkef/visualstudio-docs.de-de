---
title: 'CA1405: Für COM sichtbare Basistypen sollten sein COM sichtbar | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8c1216d66ee6cb9218949547dfd33a189593f14
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)