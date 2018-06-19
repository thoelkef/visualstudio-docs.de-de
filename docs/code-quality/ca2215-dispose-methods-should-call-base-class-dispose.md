---
title: 'CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 0ce7e5de528e8b0c0a6f128fa9f7d68c1b9f385c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919803"
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