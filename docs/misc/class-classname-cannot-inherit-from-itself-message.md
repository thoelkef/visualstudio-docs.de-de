---
title: "Die &lt;Klassenname&gt;-Klasse kann nicht von sich selbst erben: &lt;Meldung&gt; | Microsoft Docs"
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
  - "vbc30257"
  - "bc30257"
helpviewer_keywords: 
  - "BC30257"
ms.assetid: 03e3034c-a0fa-4619-84b9-5bc9aa0dfe80
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die &lt;Klassenname&gt;-Klasse kann nicht von sich selbst erben: &lt;Meldung&gt;
Eine [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) in einer Klassendefinition gibt ihre eigene Klasse an.  
  
 Eine Klasse kann von einer anderen Klasse erben, die ihr alle Member der Klasse zur Verfügung stellt, von der sie erbt. Daher müssen diese Member nicht erneut definiert werden. Eine solche Klasse wird als *abgeleitete Klasse* und die Klasse, von der sie erbt, als *Basisklasse* bezeichnet.  
  
 Es ergibt für eine Klasse keinen Sinn, von sich selbst zu erben, weil sie bereits alle ihre eigenen Member besitzt.  
  
 **Fehler\-ID:** BC30257  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise des Klassennamens in der `Inherits`\-Anweisung.  
  
2.  Wenn Sie nicht beabsichtigen, von einer anderen Klasse zu erben, entfernen Sie die `Inherits`\-Anweisung vollständig.  
  
3.  Überprüfen Sie die angegebene Meldung auf Vorschläge.  
  
## Siehe auch  
 [NICHT IM BUILD: Vererbung in Visual Basic](http://msdn.microsoft.com/de-de/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [NICHT im BUILD: Grundlegendes zu Klassen](http://msdn.microsoft.com/de-de/cc2355a2-cb98-4353-9440-736585aec46c)