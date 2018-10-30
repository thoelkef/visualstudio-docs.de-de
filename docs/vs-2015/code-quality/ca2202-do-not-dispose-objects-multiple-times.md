---
title: ': CA2202 Objekte nicht mit mehrmals | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: de3bc29e6d843532e4c15db1e33673d4f63c5179
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830716"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Objekte nicht mehrmals verwerfen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine methodenimplementierung enthält Codepfade, die mehrere Aufrufe verursachen könnten <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> oder einer Entsprechung von Dispose, z. B. einer Close()-Methode für bestimmte Typen, für das gleiche Objekt.

## <a name="rule-description"></a>Regelbeschreibung
 Eine ordnungsgemäß implementierte <xref:System.IDisposable.Dispose%2A> Methode kann mehrmals aufgerufen werden, ohne eine Ausnahme auszulösen. Allerdings ist dies nicht garantiert und Generieren von zu vermeiden einer <xref:System.ObjectDisposedException?displayProperty=fullName> sollte nicht aufgerufen werden <xref:System.IDisposable.Dispose%2A> mehr als einmal in einem Objekt.

## <a name="related-rules"></a>Verwandte Regeln
 [CA2000: Objekte verwerfen, bevor Bereich verloren geht](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Implementierung, also unabhängig des Codepfads, <xref:System.IDisposable.Dispose%2A> wird für das Objekt nur einmal aufgerufen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Auch wenn <xref:System.IDisposable.Dispose%2A> für das Objekt sicher auch mehrmals aufgerufen werden bekanntermaßen, möglicherweise in Zukunft die Implementierung ändern.

## <a name="example"></a>Beispiel
 Geschachtelte `using` Anweisungen (`Using` in Visual Basic) kann dazu führen, dass die CA2202 Warnung Verletzungen. Wenn die "IDisposable"-Ressource, der die geschachtelte innere `using` -Anweisung enthält, die Ressource des äußeren `using` -Anweisung, die `Dispose` -Methode der geschachtelten Ressource frei, die enthaltene Ressource. Wenn in diesem Fall die `Dispose` Methode des äußeren `using` Anweisung versucht, ihre Ressource ein zweites Mal freizugeben.

 Im folgenden Beispiel eine <xref:System.IO.Stream> -Objekt, das in eine äußere erstellt wird using-Anweisung wird am Ende des using-Anweisung in der Dispose-Methode der inneren veröffentlicht die <xref:System.IO.StreamWriter> -Objekt, enthält die `stream` Objekt. Am Ende der äußeren `using` -Anweisung, die `stream` Objekt ist ein zweites Mal freigegeben. Der zweite Version handelt es sich um einen Verstoß gegen CA2202.

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
 Um dieses Problem zu beheben, verwenden eine `try` / `finally` Block statt der äußeren `using` Anweisung. In der `finally` blockieren, stellen Sie sicher, dass die `stream` Ressource nicht null ist.

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
 <xref:System.IDisposable?displayProperty=fullName> [Dispose-Muster](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



