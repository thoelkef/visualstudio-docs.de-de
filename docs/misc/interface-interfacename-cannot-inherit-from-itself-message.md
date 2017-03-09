---
title: "Die Schnittstelle &lt;Schnittstellenname&gt; kann nicht von sich selbst erben: &lt;Meldung&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30296"
  - "BC30296"
helpviewer_keywords: 
  - "BC30296"
ms.assetid: a5bc1ae2-2083-4e26-b8a4-3c4dd951fd27
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Schnittstelle &lt;Schnittstellenname&gt; kann nicht von sich selbst erben: &lt;Meldung&gt;
Eine [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) in einer Schnittstellendefinition gibt die eigene Schnittstelle an.  
  
 Eine Schnittstelle kann von einer anderen Schnittstelle erben, die ihr alle Member der Schnittstelle zur Verfügung stellt, von der sie erbt. Daher müssen diese Member nicht erneut definiert werden. Eine solche Schnittstelle wird als eine *abgeleitete Schnittstelle* bezeichnet, und die Schnittstelle, von der sie erbt, heißt *Basisschnittstelle*.  
  
 Es ergibt für eine Schnittstelle keinen Sinn, von sich selbst zu erben, weil sie bereits alle ihre eigenen Member besitzt.  
  
 **Fehler\-ID:** BC30296  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise des Schnittstellennamens in der `Inherits`\-Anweisung.  
  
2.  Wenn Sie nicht beabsichtigen, von einer anderen Schnittstelle zu erben, entfernen Sie die `Inherits`\-Anweisung vollständig.  
  
3.  Überprüfen Sie die angegebene Meldung auf Vorschläge.  
  
## Siehe auch  
 [NICHT IM BUILD: Vererbung in Visual Basic](http://msdn.microsoft.com/de-de/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)