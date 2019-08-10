---
title: 'CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f3c118b097dbcd9eba8a5755672bde9c11cb13a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920306"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
Ein Typ, der <xref:System.IDisposable?displayProperty=fullName> implementiert, erbt von einem Typ, <xref:System.IDisposable>der ebenfalls implementiert. Die <xref:System.IDisposable.Dispose%2A> -Methode des erbenden Typs ruft nicht die <xref:System.IDisposable.Dispose%2A> -Methode des übergeordneten Typs auf.

## <a name="rule-description"></a>Regelbeschreibung
Wenn ein Typ von einem verwerfbaren Typ erbt, muss er die <xref:System.IDisposable.Dispose%2A> -Methode des Basistyps in seiner eigenen <xref:System.IDisposable.Dispose%2A> -Methode abrufen. Durch das Aufrufen der Methode für den Basistyp wird sichergestellt, dass alle vom Basistyp erstellten Ressourcen freigegeben werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, `base`wenden Sie an.<xref:System.IDisposable.Dispose%2A> in der <xref:System.IDisposable.Dispose%2A> -Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn `base`aufgerufen wird.<xref:System.IDisposable.Dispose%2A> Tritt auf einer tieferen Aufruf Ebene auf als die Regel Überprüfungen.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ `TypeA` , der <xref:System.IDisposable>implementiert.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ `TypeB` , der vom-Typ `TypeA` erbt und seine <xref:System.IDisposable.Dispose%2A> -Methode ordnungsgemäß aufruft.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)