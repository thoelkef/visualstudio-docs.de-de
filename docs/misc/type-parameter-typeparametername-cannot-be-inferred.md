---
title: "Der &lt;Typparametername&gt;-Typparameter kann nicht abgeleitet werden. | Microsoft Docs"
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
  - "bc36572"
  - "vbc36572"
helpviewer_keywords: 
  - "BC36572"
ms.assetid: 02264070-b055-4ab0-8d2a-eac4d90d9fdf
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der &lt;Typparametername&gt;-Typparameter kann nicht abgeleitet werden.
Eine generische Prozedur wird ohne Angabe einer Liste der Typargumente aufgerufen, und der Typrückschluss schlägt für eines der Typargumente fehl.  
  
 Wenn Sie eine generische Prozedur aufrufen, geben Sie normalerweise für jeden Typparameter, der von der Prozedur definiert wird, ein Typargument an. Alternativ können Sie vollständig auf die Liste der Typargumente verzichten. Dann versucht der Compiler, aus dem Kontext des Aufrufs Rückschlüsse auf den Typ der einzelnen Typargumente zu ziehen. Weitere Informationen finden Sie unter "Typrückschluss" in [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **Fehler\-ID:** BC36572  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die Typen der normalen Argumente dazu führen, dass der Typrückschluss konsistent mit den für die generische Prozedur deklarierten Typparametern ist.  
  
     \- oder \-  
  
-   Rufen Sie die generische Prozedur mit einer vollständigen Liste der Typargumente auf, sodass kein Typrückschluss erforderlich ist.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)