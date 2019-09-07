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
ms.openlocfilehash: 675206bb58e27110af79c46b1d61e9489f7661f2
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766084"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Verwerfbare Felder verwerfen.

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein Typ, der <xref:System.IDisposable?displayProperty=fullName> implementiert, deklariert Felder mit Typen, die ebenfalls <xref:System.IDisposable>implementieren. Die <xref:System.IDisposable.Dispose%2A> -Methode des-Felds wird nicht von der <xref:System.IDisposable.Dispose%2A> -Methode des deklarierenden Typs aufgerufen.

## <a name="rule-description"></a>Regelbeschreibung

Ein Typ ist für die Freigabe aller nicht verwalteten Ressourcen zuständig. Rule CA2213 prüft, ob ein verwerfbarer Typ (d. h. ein Typ <xref:System.IDisposable>, `T` der implementiert) `F` ein Feld deklariert, das eine Instanz eines `FT`verwerfbaren Typs ist. Für jedes Feld `F` , dem ein lokal erstelltes Objekt innerhalb der Methoden oder Initialisierer des enthaltenden Typs `T`zugewiesen wird, versucht die Regel, einen- `FT.Dispose`Rückruf zu suchen. Die-Regel durchsucht die Methoden `T.Dispose` , die von aufgerufen werden, und eine Ebene niedriger (d. h. die `T.Dispose`Methoden, die von den von aufgerufenen Methoden aufgerufen werden

> [!NOTE]
> Mit Ausnahme der [Sonderfälle](#special-cases)wird Regel CA2213 nur für Felder ausgelöst, denen ein lokal erstelltes verwerfbares Objekt innerhalb der Methoden und Initialisierer des enthaltenden Typs zugewiesen wird. Wenn das Objekt erstellt oder außerhalb des Typs `T`zugewiesen wird, wird die Regel nicht ausgelöst. Dies reduziert das Rauschen in Fällen, in denen der enthaltende Typ nicht die Verantwortung für die Freigabe des Objekts übernimmt.

### <a name="special-cases"></a>Sonderfälle

Regel CA2213 kann auch für Felder der folgenden Typen ausgelöst werden, auch wenn das Objekt, dem Sie zugewiesen sind, nicht lokal erstellt wurde:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Wenn Sie ein Objekt eines dieser Typen an einen Konstruktor übergeben und dann einem Feld zuweisen, wird eine Freigabe *Besitz Übertragung* an den neu erstellten Typ angegeben. Das heißt, der neu konstruierte Typ ist nun für das Freigeben des Objekts verantwortlich. Wenn das Objekt nicht verworfen wird, tritt ein Verstoß gegen CA2213 auf.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, <xref:System.IDisposable.Dispose%2A> müssen Sie für Felder mit Typen abrufen, <xref:System.IDisposable>die implementieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn Folgendes gilt:

- Der gekennzeichnete Typ ist nicht für die Freigabe der Ressource zuständig, die im Feld gehalten wird (d. h., der Typ hat keinen Freigabe *Besitz*).
- Der Aufruf von <xref:System.IDisposable.Dispose%2A> tritt auf einer tieferen Aufruf Ebene auf als die Regel Überprüfungen.

## <a name="example"></a>Beispiel

Der folgende Code Ausschnitt zeigt einen Typ `TypeA` , der <xref:System.IDisposable>implementiert.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Der folgende Code Ausschnitt zeigt einen Typ `TypeB` , der die Regel CA2213 verletzt, indem `aFieldOfADisposableType` er ein Feld als verwerfbaren Typ (`TypeA`) <xref:System.IDisposable.Dispose%2A> deklariert und nicht für das Feld aufgerufen wird.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

Um die Verletzung zu beheben, `Dispose()` müssen Sie für das verwerfbare Feld aufzurufen:

```csharp
protected virtual void Dispose(bool disposing)
{
   if (!disposed)
   {
      // Dispose of resources held by this instance.
      aFieldOfADisposableType.Dispose();

      disposed = true;

      // Suppress finalization of this disposed instance.
      if (disposing)
      {
          GC.SuppressFinalize(this);
      }
   }
}
```

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable?displayProperty=fullName>
- [Muster verwerfen](/dotnet/standard/design-guidelines/dispose-pattern)