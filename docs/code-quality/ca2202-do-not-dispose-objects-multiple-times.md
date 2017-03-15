---
title: "CA2202: Objekte nicht mehrmals verwerfen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2202"
  - "Do not dispose objects multiple times"
  - "DoNotDisposeObjectsMultipleTimes"
helpviewer_keywords: 
  - "CA2202"
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2202: Objekte nicht mehrmals verwerfen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methodenimplementierung enthält Codepfade, die möglicherweise mehrere Aufrufe von <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> oder einer Entsprechung von Dispose, z. B. einer Close\(\)\-Methode für bestimmte Typen, für dasselbe Objekt verursachen.  
  
## Regelbeschreibung  
 Eine ordnungsgemäß implementierte <xref:System.IDisposable.Dispose%2A>\-Methode kann mehrmals aufgerufen werden, ohne dass eine Ausnahme ausgelöst wird.  Da dies jedoch nicht gewährleistet ist, sollten Sie <xref:System.IDisposable.Dispose%2A> nicht mehr als einmal für ein Objekt aufrufen, um zu vermeiden, dass <xref:System.ObjectDisposedException?displayProperty=fullName> generiert wird.  
  
## Verwandte Regeln  
 [CA2000: Objekte verwerfen, bevor Bereich verloren geht](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Implementierung so, dass <xref:System.IDisposable.Dispose%2A> unabhängig vom Codepfad nur einmal für das Objekt aufgerufen wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Auch wenn bekannt ist, dass <xref:System.IDisposable.Dispose%2A> für das Objekt gefahrlos mehrfach aufgerufen werden kann, ist es möglich, dass die Implementierung sich zu einem späteren Zeitpunkt ändert.  
  
## Beispiel  
 Geschachtelte `using`\-Anweisungen \(`Using` in Visual Basic\) können Verletzungen der CA2202\-Warnung verursachen.  Wenn die IDisposable\-Ressource der geschachtelten inneren `using`\-Anweisung die Ressource der äußeren `using`\-Anweisung enthält, gibt die `Dispose`\-Methode der geschachtelten Ressource die enthaltene Ressource frei.  Wenn diese Situation auftritt, versucht die `Dispose`\-Methode der äußeren `using`\-Anweisung, ihre Ressource zu einem zweiten Mal freizugeben.  
  
 Im folgenden Beispiel wird ein <xref:System.IO.Stream>\-Objekt, das in einer äußeren using\-Anweisung erstellt wurde, am Ende der inneren using\-Anweisung in der Dispose\-Methode des <xref:System.IO.StreamWriter>\-Objekts freigegeben, das das `stream`\-Objekt enthält.  Am Ende der äußeren `using`\-Anweisung wird das `stream`\-Objekt ein zweites Mal freigegeben.  Die zweite Freigabe ist eine Verletzung von CA2202.  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## Beispiel  
 Um dieses Problem zu beheben, verwenden Sie einen `try`\/`finally`\-Block statt der äußeren `using`\-Anweisung.  Stellen Sie im `finally`\-Block sicher, dass die `stream`\-Ressource nicht NULL ist.  
  
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
  
## Siehe auch  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose\-Muster](../Topic/Dispose%20Pattern.md)