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
ms.openlocfilehash: 2c14f9ed8803c02d1570ac2a3dee82fbdfca5f01
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948536"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize korrekt aufrufen.

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategorie|Microsoft. Verwendung|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Verstöße gegen diese Regel können folgende Ursachen haben:

- Eine Methode, die eine Implementierung von <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> , und rufen Sie keine <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Eine Methode, die keine Implementierung des ist <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> und ruft <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Eine Methode, die Aufrufe <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> und übergibt Sie ein anderes Element als [diese (C#)](/dotnet/csharp/language-reference/keywords/this) oder [mich (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Regelbeschreibung

Die <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Methode ermöglicht Benutzern das Freigeben von Ressourcen zu einem beliebigen Zeitpunkt vor dem Objekt, das die aufgabenausführung verfügbar sind, für die Garbagecollection. Wenn die <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> -Methode aufgerufen wird, gibt das Objekt die Ressourcen frei. Dadurch wird die Beendigung nicht erforderlich. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sollten Aufrufen <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> , damit der Garbage Collector den Finalizer des Objekts nicht aufruft.

Um zu verhindern, dass abgeleitete Typen mit Finalizern erneut implementieren müssen <xref:System.IDisposable> und um es aufzurufen, nicht versiegelte Typen ohne Finalizer sollten dennoch aufrufen <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben:

- Wenn die Methode eine Implementierung von <xref:System.IDisposable.Dispose%2A>, fügen Sie einen Aufruf von <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Wenn die Methode keine Implementierung von <xref:System.IDisposable.Dispose%2A>, entfernen Sie den Aufruf von <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> oder verschieben Sie ihn in des Typs des <xref:System.IDisposable.Dispose%2A> Implementierung.

- Ändern Sie alle Aufrufe von <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> übergeben [diese (C#)](/dotnet/csharp/language-reference/keywords/this) oder [mich (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie nur eine Warnung dieser Regel auf, wenn Sie absichtlich verwenden <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> zur Steuerung der Lebensdauer von anderen Objekten. Unterdrücken Sie eine Warnung dieser Regel nicht, wenn eine Implementierung von <xref:System.IDisposable.Dispose%2A> Aufrufen nicht <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>. In diesem Fall wird die Leistung beeinträchtigt und bietet keine Vorteile Abschluss nicht unterdrückt.

## <a name="example-that-violates-ca1816"></a>Beispiel für die CA1816 verletzt

Dieser Code zeigt eine Methode, die Aufrufe <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, aber nicht übergeben [diese (C#)](/dotnet/csharp/language-reference/keywords/this) oder [mich (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). Dieser Code wird daher die Regel CA1816 verletzt.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Beispiel für die CA1816 erfüllt.

Dieses Beispiel zeigt eine Methode, die ordnungsgemäß Aufrufe <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> durch Übergabe [diese (C#)](/dotnet/csharp/language-reference/keywords/this) oder [mich (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA2215: Dispose-Methoden müssen die Dispose der Basisklasse aufrufen.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Siehe auch

- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)