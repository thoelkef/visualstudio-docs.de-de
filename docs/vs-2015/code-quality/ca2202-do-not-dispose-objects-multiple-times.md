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
ms.openlocfilehash: 31bf7fe33aa59c3a713d2da81ddbd11ed6899723
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546288"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Objekte nicht mehrmals verwerfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|Donotdisposeeobjectmultipletimes|
|CheckId|CA2202|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methoden Implementierung enthält Codepfade, die mehrere Aufrufe von <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> oder eine verwerfen-Entsprechung (z. b. eine Close ()-Methode für einige Typen) für dasselbe Objekt verursachen könnten.

## <a name="rule-description"></a>Beschreibung der Regel
 Eine ordnungsgemäß implementierte <xref:System.IDisposable.Dispose%2A> Methode kann mehrmals aufgerufen werden, ohne eine Ausnahme auszulösen. Dies ist jedoch nicht garantiert. um zu vermeiden, dass eine erstellt wird, <xref:System.ObjectDisposedException?displayProperty=fullName> sollten Sie nicht <xref:System.IDisposable.Dispose%2A> mehr als einmal für ein Objekt aufzurufen.

## <a name="related-rules"></a>Verwandte Regeln
 [CA2000: Objekte verwerfen, bevor Bereich verloren geht.](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die-Implementierung so, dass unabhängig vom Codepfad <xref:System.IDisposable.Dispose%2A> nur einmal für das-Objekt aufgerufen wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Auch wenn <xref:System.IDisposable.Dispose%2A> für das Objekt bekannt ist, dass es mehrmals sicher aufgerufen werden kann, kann sich die Implementierung in Zukunft ändern.

## <a name="example"></a>Beispiel
 `using` `Using` In Visual Basic) kann es zu Verstößen gegen die CA2202-Warnung führen. Wenn die iverwerfbare Ressource der geschachtelten inneren `using` Anweisung die Ressource der äußeren `using` Anweisung enthält, gibt die-Methode der geschachtelten `Dispose` Ressource die enthaltene Ressource frei. Wenn diese Situation eintritt, versucht die- `Dispose` Methode der äußeren Anweisung, die `using` Ressource ein zweites Mal zu verwerfen.

 Im folgenden Beispiel wird ein- <xref:System.IO.Stream> Objekt, das in einer äußeren using-Anweisung erstellt wird, am Ende der inneren using-Anweisung in der verwerfen-Methode des Objekts freigegeben, <xref:System.IO.StreamWriter> das das `stream` Objekt enthält. Am Ende der äußeren `using` Anweisung `stream` wird das Objekt ein zweites Mal freigegeben. Die zweite Version ist ein Verstoß gegen CA2202.

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
 Um dieses Problem zu beheben, verwenden Sie `try` / `finally` anstelle der äußeren-Anweisung einen-Block `using` . `finally`Stellen Sie im-Block sicher, dass die `stream` Ressource nicht NULL ist.

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

## <a name="see-also"></a>Weitere Informationen
 <xref:System.IDisposable?displayProperty=fullName> [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
