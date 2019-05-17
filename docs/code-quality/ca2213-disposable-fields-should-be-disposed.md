---
title: 'CA2213: Verwerfbare Felder verwerfen.'
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b38157fcc23561b47a919151aa78a71f98b3909b
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65804997"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Verwerfbare Felder verwerfen.

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein Typ, der implementiert <xref:System.IDisposable?displayProperty=fullName> deklariert Felder von Typen, die ebenfalls implementieren <xref:System.IDisposable>. Die <xref:System.IDisposable.Dispose%2A> -Methode des Felds wird nicht aufgerufen, indem die <xref:System.IDisposable.Dispose%2A> -Methode des deklarierenden Typs.

## <a name="rule-description"></a>Regelbeschreibung

Ein Typ ist verantwortlich für das Verwerfen von alle nicht verwalteten Ressourcen. CA2213 überprüft, ob ein von einem verwerfbaren Typ auszuschließen (d. h. eine, die implementiert <xref:System.IDisposable>) `T` deklariert ein Feld `F` d. h. eine Instanz eines verwerfbaren Typs `FT`. Für jedes Feld `F` zugewiesen, die ein lokal erstelltes Objekt in den Methoden oder -Initialisierer des enthaltenden Typs `T`, der Regel wird versucht, einen Aufruf von `FT.Dispose`. Die Regel durchsucht, die vom aufgerufenen Methoden `T.Dispose` und die Ebene darunter (d. h. die Methoden, die aufgerufen werden, durch die Methoden aufgerufen werden, indem `T.Dispose`).

> [!NOTE]
> Anders als die [Sonderfälle](#special-cases), Regel CA2213 ausgelöst wird, nur für Felder, die lokal erstelltes verwerfbares Objekt innerhalb von Methoden und den Initialisierer des enthaltenden Typs zugewiesen werden. Wenn das Objekt erstellt wird, oder außerhalb von Typ zugewiesen `T`, die Regel wird nicht ausgelöst. Dies verringert Störungen für Fälle, in dem der enthaltende Typ die Verantwortung für das Verwerfen des Objekts besitzt.

### <a name="special-cases"></a>Sonderfälle

Regel CA2213 kann auch für Felder der folgenden Typen ausgelöst werden, auch wenn das Objekt, das sie zugewiesen sind nicht lokal erstellt wird:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Gibt ein Objekt von einem dieser Typen an einen Konstruktor zu übergeben, und klicken Sie dann auf ein Feld Zuweisen einer *dispose Übertragung des Abonnementbesitzes* in den neu erstellten Typ. Der neu erstellte Typ ist, also jetzt verantwortlich für das Verwerfen des Objekts. Wenn das Objekt nicht verworfen wird, tritt ein, zu eine Verletzung der CA2213.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, rufen <xref:System.IDisposable.Dispose%2A> für Felder, die Typen, die implementieren <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, falls:

- Der markierten Typ ist nicht verantwortlich für die Ressource freigegeben, die nach dem Feld gespeichert (d. h. der Typ verfügt nicht über *verwerfen Sie den Besitz*)
- Der Aufruf von <xref:System.IDisposable.Dispose%2A> tritt auf, auf einer tieferen aufrufenden Ebene als die regelüberprüfungen

## <a name="example"></a>Beispiel

Der folgende Codeausschnitt zeigt ein `TypeA` implementiert <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Der folgende Codeausschnitt zeigt ein `TypeB` , die verstößt gegen die Regel CA2213 durch das Deklarieren eines Feldes `aFieldOfADisposableType` als einem verwerfbaren Typ (`TypeA`) und nicht aufrufen <xref:System.IDisposable.Dispose%2A> für das Feld.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)