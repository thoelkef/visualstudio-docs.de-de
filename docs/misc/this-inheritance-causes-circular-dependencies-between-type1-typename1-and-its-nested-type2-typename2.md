---
title: "Diese Vererbung verursacht Ringabh&#228;ngigkeiten zwischen &lt;Type&gt; &quot;&lt;Typname1&gt;&quot; und &lt;Typ2&gt; &quot;&lt;Typname2&gt;&quot; (geschachtelt). | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30907"
  - "bc30907"
helpviewer_keywords: 
  - "BC30907"
ms.assetid: 17d4f938-5895-4d33-943e-8abf0ceacdc9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diese Vererbung verursacht Ringabh&#228;ngigkeiten zwischen &lt;Type&gt; &quot;&lt;Typname1&gt;&quot; und &lt;Typ2&gt; &quot;&lt;Typname2&gt;&quot; (geschachtelt).
Eine Vererbungsstruktur führt zu einer zirkulären Abhängigkeit zwischen geschachtelten Klassen, das heißt, zwei Klassen erben voneinander.  
  
 Diese Fehlermeldung kann durch folgenden Code generiert werden.  
  
```  
Public Class c1 Inherits c3.c4 Public Class c2 End Class End Class Public Class c3 Inherits c1.c2 Public Class c4 End Class End Class  
```  
  
 Im vorangehenden Code erbt Klasse `c1` von der Klasse `c4`, aber `c4` ist in `c3` geschachtelt, die von `c2` erbt, die in `c1` geschachtelt ist.  
  
 **Fehler\-ID:** BC30907  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Vererbungsstruktur, sodass keine zirkuläre Abhängigkeit vorhanden ist.  
  
## Siehe auch  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)