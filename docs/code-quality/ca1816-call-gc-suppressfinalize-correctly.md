---
title: 'CA1816: GC.SuppressFinalize korrekt aufrufen.'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdd20df37586e50b5236872f1d84de48d08c87a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233529"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize korrekt aufrufen.

|||
|-|-|
|TypeName|Callgcsuppressfinalizecorrectly|
|CheckId|CA1816|
|Kategorie|Microsoft. Verwendung|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Verstöße gegen diese Regel können durch folgende Ursachen verursacht werden:

- Eine Methode, die eine Implementierung von <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> ist und keinen <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>aufruft.

- Eine Methode, bei der es sich nicht <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> um eine <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>Implementierung von handelt und aufruft.

- Eine Methode, die <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> einen anderen Vorgang als [thisC#()](/dotnet/csharp/language-reference/keywords/this) oder [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)aufruft und übergibt.

## <a name="rule-description"></a>Regelbeschreibung

Mit <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> der-Methode können Benutzer jederzeit Ressourcen freigeben, bevor das Objekt für Garbage Collection verfügbar wird. Wenn die <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> -Methode aufgerufen wird, gibt Sie Ressourcen des-Objekts frei. Dies macht die Finalisierung unnötig. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>sollte aufgerufen <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> werden, damit der Garbage Collector den Finalizer des Objekts nicht aufruft.

Um zu verhindern, dass abgeleitete Typen mit Finalizern neu implementiert <xref:System.IDisposable> und aufgerufen werden müssen, sollten unversiegelte Typen ohne Finalizer trotzdem <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>aufrufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

So beheben Sie einen Verstoß gegen diese Regel:

- Wenn die Methode eine Implementierung von <xref:System.IDisposable.Dispose%2A>ist, fügen Sie einen- <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>Rückruf hinzu.

- Wenn es sich bei der-Methode nicht <xref:System.IDisposable.Dispose%2A>um eine Implementierung von handelt, <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> entfernen Sie entweder den-Befehl, <xref:System.IDisposable.Dispose%2A> oder verschieben Sie ihn in die-Implementierung des Typs.

- Ändern Sie alle Aufrufe <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> von, um [thisC#()](/dotnet/csharp/language-reference/keywords/this) oder [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)zu übergeben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie eine Warnung aus dieser Regel nur, wenn Sie <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> absichtlich verwenden, um die Lebensdauer anderer Objekte zu steuern. Unterdrücken Sie keine Warnung aus dieser Regel, wenn eine <xref:System.IDisposable.Dispose%2A> Implementierung von <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>nicht aufruft. In dieser Situation wird die Leistung durch einen Fehler beim unterdrücken der Finalisierung beeinträchtigt und bietet keine Vorteile.

## <a name="example-that-violates-ca1816"></a>Beispiel, das gegen CA1816 verstößt

Dieser Code zeigt eine Methode an, <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>die aufruft, aber weder [thisC#()](/dotnet/csharp/language-reference/keywords/this) noch [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)übergibt. Dies führt dazu, dass dieser Code die Regel CA1816 verletzt.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Beispiel, das CA1816 erfüllt

Dieses Beispiel zeigt eine Methode, die korrekt <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> aufruft, indem Sie [thisC#()](/dotnet/csharp/language-reference/keywords/this) oder [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)übergibt.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA2215: Verwerfen-Methoden sollten Basisklassen Freigabe abrufen](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Siehe auch

- [Muster verwerfen](/dotnet/standard/design-guidelines/dispose-pattern)