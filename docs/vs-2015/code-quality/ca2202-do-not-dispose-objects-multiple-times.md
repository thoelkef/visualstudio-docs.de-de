---
title: 'CA2202: Objekte nicht mehrmals löschen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e0be715d8aea84fac53ea2a796e71850b961730c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667402"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Objekte nicht mehrmals verwerfen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Donotdisposeeobjectmultipletimes|
|CheckId|CA2202|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methoden Implementierung enthält Codepfade, die mehrere Aufrufe an <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> oder eine verwerfen-Entsprechung (z. b. eine Close ()-Methode für einige Typen) für dasselbe Objekt verursachen könnten.

## <a name="rule-description"></a>Regelbeschreibung
 Eine ordnungsgemäß implementierte <xref:System.IDisposable.Dispose%2A> Methode kann mehrmals aufgerufen werden, ohne eine Ausnahme auszulösen. Dies ist jedoch nicht garantiert, und um das Erstellen einer <xref:System.ObjectDisposedException?displayProperty=fullName> zu vermeiden, sollten Sie <xref:System.IDisposable.Dispose%2A> nicht mehr als einmal für ein Objekt aufzurufen.

## <a name="related-rules"></a>Verwandte Regeln
 [CA2000: Objekte verwerfen, bevor Bereich verloren geht](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Implementierung so, dass für das-Objekt unabhängig vom Codepfad <xref:System.IDisposable.Dispose%2A> nur einmal aufgerufen wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Auch wenn <xref:System.IDisposable.Dispose%2A> für das Objekt bekanntermaßen mehrmals sicher aufgerufen werden kann, kann sich die Implementierung in Zukunft ändern.

## <a name="example"></a>Beispiel
 Die `using`-Anweisungen (`Using` in Visual Basic) können zu Verstößen gegen die CA2202-Warnung führen. Wenn die iverwerf-Ressource der geschachtelten inneren `using`-Anweisung die Ressource der äußeren `using`-Anweisung enthält, gibt die `Dispose`-Methode der geschachtelten Ressource die enthaltene Ressource frei. Wenn diese Situation eintritt, versucht die `Dispose`-Methode der äußeren `using`-Anweisung, die Ressource ein zweites Mal zu verwerfen.

 Im folgenden Beispiel wird ein <xref:System.IO.Stream>-Objekt, das in einer äußeren using-Anweisung erstellt wird, am Ende der inneren using-Anweisung in der verwerfen-Methode des <xref:System.IO.StreamWriter>-Objekts freigegeben, das das `stream`-Objekt enthält. Am Ende der äußeren `using`-Anweisung wird das `stream`-Objekt ein zweites Mal freigegeben. Die zweite Version ist ein Verstoß gegen CA2202.

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
 Um dieses Problem zu beheben, verwenden Sie einen `try` / `finally` Block anstelle der äußeren `using` Anweisung. Stellen Sie im `finally`-Block sicher, dass die Ressource `stream` nicht NULL ist.

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
 <xref:System.IDisposable?displayProperty=fullName> Lösch [Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
