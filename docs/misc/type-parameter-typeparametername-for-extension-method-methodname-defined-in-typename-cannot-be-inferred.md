---
title: "Der Typparameter &quot;&lt;Typparametername&gt;&quot; f&#252;r die in &quot;&lt;Typname&gt;&quot; definierte Erweiterungsmethode &quot;&lt;Methodenname&gt;&quot; kann nicht abgeleitet werden. | Microsoft Docs"
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
  - "vbc36589"
  - "bc36589"
helpviewer_keywords: 
  - "BC36589"
ms.assetid: 4676a7a5-934b-4b74-b640-48065fc07e94
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Typparameter &quot;&lt;Typparametername&gt;&quot; f&#252;r die in &quot;&lt;Typname&gt;&quot; definierte Erweiterungsmethode &quot;&lt;Methodenname&gt;&quot; kann nicht abgeleitet werden.
Eine generische Erweiterungsmethode wird ohne Angabe einer Liste der Typargumente aufgerufen, und der Typrückschluss schlägt für eines der Typargumente fehl.  
  
 Wenn Sie eine generische Prozedur aufrufen, geben Sie normalerweise für jeden Typparameter, der von der Prozedur definiert wird, ein Typargument ein. Alternativ können Sie vollständig auf die Liste der Typargumente verzichten. Dann versucht der Compiler, aus dem Kontext des Aufrufs Rückschlüsse auf den Typ der einzelnen Typargumente zu ziehen. Weitere Informationen finden Sie unter "Typrückschluss" in [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **Fehler\-ID:** BC36589  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die Typen der normalen Argumente dazu führen, dass der Typrückschluss konsistent mit den für die generische Prozedur deklarierten Typparametern ist.  
  
     \- oder \-  
  
-   Rufen Sie die generische Prozedur mit einer vollständigen Liste der Typargumente auf, sodass ein Typrückschluss nicht erforderlich ist.  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)