---
title: 'CA2111: Zeiger sollten nicht sichtbar sein | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce027b8e6bcf39623e07a862d4f9fb23c33b9967
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Zeiger sollten nicht sichtbar sein.
|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder geschützter <xref:System.IntPtr?displayProperty=fullName> oder <xref:System.UIntPtr?displayProperty=fullName> Feld ist schreibgeschützt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 <xref:System.IntPtr> und <xref:System.UIntPtr> Zeigertypen, die verwendet werden, auf nicht verwalteten Speicher zugegriffen werden. Wenn ein Zeiger nicht privat, intern oder schreibgeschützt ist, kann schädlichen Code den Wert des Zeigers, potenziell Zugriffe auf beliebige Speicherbereiche ermöglichen oder Anwendungs- bzw. Systemfehler verursachen ändern.  
  
 Wenn Sie zum Absichern des Zugriffs auf den Typ, die die Zeigerfeld enthält beabsichtigen, finden Sie unter [CA2112: gesicherte Typen sollten keine Felder verfügbar](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Sichern Sie den Zeiger, indem Sie somit schreibgeschützt, intern oder privat.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie nicht auf den Wert des Zeigers angewiesen sind.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zeigt, Zeiger, die gegen die verstoßen und die Regel eingehalten wird. Beachten Sie, dass der Zeiger nicht privaten auch diese Regel verletzen [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>