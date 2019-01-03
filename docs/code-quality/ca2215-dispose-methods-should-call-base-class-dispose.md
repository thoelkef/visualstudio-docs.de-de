---
title: 'CA2215: Dispose-Methoden müssen die Dispose der Basisklasse aufrufen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 8531bfd8407415aa1868fb5e1f633be442ce9bc7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844222"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Dispose-Methoden müssen die Dispose der Basisklasse aufrufen.

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ, der implementiert <xref:System.IDisposable?displayProperty=fullName> erbt von einem Typ, der auch implementiert <xref:System.IDisposable>. Die <xref:System.IDisposable.Dispose%2A> Methode der erbende Typ ruft nicht die <xref:System.IDisposable.Dispose%2A> Methode des übergeordneten Typs.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn ein Typ von einem verwerfbaren Typ erbt, muss er Aufrufen der <xref:System.IDisposable.Dispose%2A> Methode des Basistyps von in eine eigene <xref:System.IDisposable.Dispose%2A> Methode. Aufrufen der Methode des Basistyps wird Dispose alle Ressourcen, die von den Basistyp erstellt freigegeben werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen `base`.<xref:System.IDisposable.Dispose%2A> in Ihrer <xref:System.IDisposable.Dispose%2A> Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, falls der Aufruf von `base`.<xref:System.IDisposable.Dispose%2A> Tritt auf, auf einer tieferen aufrufenden Ebene als die Regel überprüft.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein `TypeA` implementiert <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `TypeB` , die von Typ erbt `TypeA` und ordnungsgemäß ruft seine <xref:System.IDisposable.Dispose%2A> Methode.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)