---
title: 'CA2213: Verwerfbare Felder verwerfen'
ms.date: 11/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be06c9bf38ec360cedc858d92a84b1f89c662856
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220631"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Verwerfbare Felder verwerfen

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein Typ, der implementiert <xref:System.IDisposable?displayProperty=fullName> deklariert Felder von Typen, die ebenfalls implementieren <xref:System.IDisposable>. Die <xref:System.IDisposable.Dispose%2A> -Methode des Felds wird nicht aufgerufen, indem die <xref:System.IDisposable.Dispose%2A> -Methode des deklarierenden Typs.

## <a name="rule-description"></a>Regelbeschreibung

Ein Typ ist verantwortlich für das Verwerfen von alle nicht verwalteten Ressourcen. CA2213 überprüft, ob ein von einem verwerfbaren Typ auszuschließen (d. h. eine, die implementiert <xref:System.IDisposable>) `T` deklariert ein Feld `F` d. h. eine Instanz eines verwerfbaren Typs `FT`. Für jedes Feld `F` zugewiesen, die ein lokal erstelltes Objekt in den Methoden oder -Initialisierer des enthaltenden Typs `T`, der Regel wird versucht, einen Aufruf von `FT.Dispose`. Die Regel durchsucht, die vom aufgerufenen Methoden `T.Dispose` und die Ebene darunter (d. h. die Methoden, die aufgerufen werden, durch die Methoden aufgerufen werden, indem `FT.Dispose`).

> [!NOTE]
> CA2213 der Regel wird ausgelöst, nur für Felder, die lokal erstelltes verwerfbares Objekt innerhalb von Methoden und den Initialisierer des enthaltenden Typs zugewiesen werden. Wenn das Objekt erstellt wird, oder außerhalb von Typ zugewiesen `T`, die Regel wird nicht ausgelöst. Dies verringert Störungen für Fälle, in dem der enthaltende Typ die Verantwortung für das Verwerfen des Objekts besitzt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, rufen <xref:System.IDisposable.Dispose%2A> für Felder, die Typen, die implementieren <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicherer, die mit dieser Regel eine Warnung zu unterdrücken, wenn Sie nicht zuständig sind, für die Ressource freigegeben, die nach dem Feld gespeichert wird, oder wenn der Aufruf von <xref:System.IDisposable.Dispose%2A> tritt auf, auf einer tieferen aufrufenden Ebene als die Regel überprüft.

## <a name="example"></a>Beispiel

Der folgende Codeausschnitt zeigt ein `TypeA` implementiert <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Der folgende Codeausschnitt zeigt ein `TypeB` , die verstößt gegen die Regel CA2213 durch das Deklarieren eines Feldes `aFieldOfADisposableType` als einem verwerfbaren Typ (`TypeA`) und nicht aufrufen <xref:System.IDisposable.Dispose%2A> für das Feld.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)