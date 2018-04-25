---
title: 'CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61cb33b8fb717914e109ca7ed43e01dd1c18edb6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
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
 Um einen Verstoß gegen diese Regel zu beheben, rufen `base`.<xref:System.IDisposable.Dispose%2A> in Ihrem <xref:System.IDisposable.Dispose%2A> Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn der Aufruf von `base`.<xref:System.IDisposable.Dispose%2A> Tritt auf, genauer gesagt aufrufenden als die Regel überprüft.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `TypeA` implementiert <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `TypeB` von Typ erbt `TypeA` und ordnungsgemäß ruft seine <xref:System.IDisposable.Dispose%2A> Methode.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Siehe auch
 <xref:System.IDisposable?displayProperty=fullName> [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)