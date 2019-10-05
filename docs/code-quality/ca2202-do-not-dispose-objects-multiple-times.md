---
title: 'CA2202: Objekte nicht mehrmals verwerfen.'
ms.date: 07/16/2019
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c7fa7756383426f990e18225995a768de9fefbd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231739"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Objekte nicht mehrmals verwerfen.

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Methoden Implementierung enthält Codepfade, die mehrere Aufrufe <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> von oder eine verwerfen-Entsprechung (z. b. eine Close ()-Methode für einige Typen) für dasselbe Objekt verursachen könnten.

## <a name="rule-description"></a>Regelbeschreibung

Eine ordnungsgemäß <xref:System.IDisposable.Dispose%2A> implementierte Methode kann mehrmals aufgerufen werden, ohne eine Ausnahme auszulösen. Dies ist jedoch nicht garantiert. um zu vermeiden, dass <xref:System.ObjectDisposedException?displayProperty=fullName> eine erstellt wird, <xref:System.IDisposable.Dispose%2A> sollten Sie nicht mehr als einmal für ein Objekt aufzurufen.

## <a name="related-rules"></a>Verwandte Regeln

- [CA2000: Objekte vor Verlust des Gültigkeits Bereichs verwerfen](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die-Implementierung so, dass unabhängig vom <xref:System.IDisposable.Dispose%2A> Codepfad nur einmal für das-Objekt aufgerufen wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel. Auch wenn <xref:System.IDisposable.Dispose%2A> für das Objekt bekannt ist, dass es mehrmals sicher aufgerufen werden kann, kann sich die Implementierung in Zukunft ändern.

## <a name="example"></a>Beispiel

`using` InVisualBasic)kanneszuVerstößengegendie`Using` CA2202-Warnung führen. Wenn die iverwerfbare Ressource der geschachtelten `using` inneren Anweisung die Ressource der äußeren `using` Anweisung enthält, gibt `Dispose` die-Methode der geschachtelten Ressource die enthaltene Ressource frei. Wenn diese Situation eintritt, versucht `Dispose` die-Methode der `using` äußeren Anweisung, die Ressource ein zweites Mal zu verwerfen.

Im folgenden Beispiel wird ein <xref:System.IO.Stream> -Objekt, das in einer äußeren using-Anweisung erstellt wird, am Ende der inneren using-Anweisung in der verwerfen-Methode <xref:System.IO.StreamWriter> des Objekts freigegeben, `stream` das das Objekt enthält. Am Ende der äußeren `using` Anweisung wird das `stream` Objekt ein zweites Mal freigegeben. Die zweite Version ist ein Verstoß gegen CA2202.

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Beispiel

Um dieses Problem zu beheben, verwenden `try` Sie anstelle der äußeren `using` -Anweisung einen / `finally` -Block. Stellen Sie im- `stream` Blocksicher,dassdieRessourcenichtNULList.`finally`

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    stream?.Dispose();
}
```

> [!TIP]
> Die `?.` obige Syntax ist der [null bedingte Operator](/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-).

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)