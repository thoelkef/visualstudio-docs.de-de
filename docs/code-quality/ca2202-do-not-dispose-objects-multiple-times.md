---
title: 'CA2202: Objekte nicht mehrmals verwerfen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c7eb35e556e8edd6e840f2fbd6701e182895706
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920148"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Objekte nicht mehrmals verwerfen
|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine methodenimplementierung enthält Codepfade, die mehrere Aufrufe von verursachen können <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> oder einer Entsprechung von Dispose, z. B. einer Close()-Methode für bestimmte Typen, die für dasselbe Objekt.

## <a name="rule-description"></a>Regelbeschreibung
 Eine ordnungsgemäß implementierte <xref:System.IDisposable.Dispose%2A> Methode kann mehrfach aufgerufen werden, ohne eine Ausnahme auszulösen. Allerdings ist dies nicht garantiert und zum Generieren von vermeiden einer <xref:System.ObjectDisposedException?displayProperty=fullName> rufen Sie nicht <xref:System.IDisposable.Dispose%2A> mehr als ein Mal für ein Objekt.

## <a name="related-rules"></a>Verwandte Regeln
 [CA2000: Objekte verwerfen, bevor Bereich verloren geht](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Implementierung so, dass unabhängig von der Codepfad <xref:System.IDisposable.Dispose%2A> wird nur ein Mal für das Objekt aufgerufen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Auch wenn <xref:System.IDisposable.Dispose%2A> für das Objekt sicher aufgerufen werden können mehrere Male bekannt ist, die Implementierung kann sich in Zukunft ändern.

## <a name="example"></a>Beispiel
 Geschachtelte `using` Anweisungen (`Using` in Visual Basic) können dazu führen, dass Verstöße gegen die CA2202-Warnung. Wenn die IDisposable-Ressource der geschachtelten inneren `using` -Anweisung enthält, die Ressource des äußeren `using` -Anweisung, die `Dispose` Methode der geschachtelten Ressource frei, die der enthaltene Ressource. Wenn in diesem Fall die `Dispose` Methode des äußeren `using` Anweisung versucht, auf die Ressource ein zweites Mal freizugeben.

 Im folgenden Beispiel ein <xref:System.IO.Stream> -Objekt, das in einer äußeren erstellt wird mit-Anweisung am Ende der inneren using-Anweisung in der Dispose-Methode freigegeben ist die <xref:System.IO.StreamWriter> -Objekt, enthält die `stream` Objekt. Am Ende des äußeren `using` -Anweisung, die `stream` Objekt wird ein zweites Mal freigegeben. Die zweite Version ist eine Verletzung von CA2202.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}

```

## <a name="example"></a>Beispiel
 Verwenden Sie zum Beheben dieses Problems eine `try` / `finally` Block anstelle der äußeren `using` Anweisung. In der `finally` blockieren, stellen Sie sicher, dass die `stream` Ressource ist nicht null.

```
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
    if(stream != null)
        stream.Dispose();
}

```

## <a name="see-also"></a>Siehe auch
 <xref:System.IDisposable?displayProperty=fullName> [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)