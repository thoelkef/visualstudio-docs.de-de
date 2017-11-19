---
title: 'CA2215: Dispose-Methoden sollten Dispose der Basisklasse aufrufen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0659b9ec82353e3c658f1ba89f07fad197dd8670
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen
|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein Typ, der implementiert <xref:System.IDisposable?displayProperty=fullName> erbt von einem Typ, der auch implementiert <xref:System.IDisposable>. Die <xref:System.IDisposable.Dispose%2A> rufen Methode von der erbende Typ nicht die <xref:System.IDisposable.Dispose%2A> Methode des übergeordneten Typs.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn ein Typ von einem Typ erbt, rufen sie die <xref:System.IDisposable.Dispose%2A> Methode des Basistyps aus in einem eigenen <xref:System.IDisposable.Dispose%2A> Methode. Aufrufen der Methode des Basistyps gewährleistet Dispose an, dass alle Ressourcen erstellt, indem der Basistyp freigegeben werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen `base`.<xref:System.IDisposable.Dispose%2A> in Ihrer <xref:System.IDisposable.Dispose%2A> Methode.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn der Aufruf von `base`.<xref:System.IDisposable.Dispose%2A> tritt auf, genauer gesagt aufrufenden als die Regel überprüft.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ `TypeA` implementiert <xref:System.IDisposable>.  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ `TypeB` von Typ erbt `TypeA` und ordnungsgemäß ruft seine <xref:System.IDisposable.Dispose%2A> Methode.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)