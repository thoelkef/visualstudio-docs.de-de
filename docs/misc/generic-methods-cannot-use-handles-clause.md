---
title: "Generische Methoden k&#246;nnen die Handles-Klausel nicht verwenden. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32080"
  - "BC32080"
helpviewer_keywords: 
  - "BC32080"
ms.assetid: 88c62a1c-aee3-46b2-ad78-76790022c04c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Generische Methoden k&#246;nnen die Handles-Klausel nicht verwenden.
Die Deklaration einer generischen `Sub`\-Prozedur enthält eine [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)\-Klausel.  
  
 Eine `Handles`\-Klausel gibt eine Liste von Ereignissen an, die von der `Sub`\-Prozedur behandelt werden. Damit die `Sub`\-Prozedur als Ereignishandler verwendet werden kann, muss sie dieselbe Signatur wie jedes von ihr zu behandelnde Ereignis aufweisen. Eine generische Prozedur kann mehrmals erstellt werden, und zwar mit Signaturen, die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zur Kompilierzeit nicht vorhersehen kann. Daher kann [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nicht sicherstellen, dass eine Signatur bereitgestellt wird, die mit den Signaturen der Ereignisse in der `Handles`\-Klausel übereinstimmt.  
  
 **Fehler\-ID:** BC32080  
  
### So beheben Sie diesen Fehler  
  
-   Wenn die `Sub`\-Prozedur generisch sein muss, entfernen Sie die `Handles`\-Klausel aus ihrer Deklaration. Verwenden Sie die [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement), um diesen Ereignishandler einem Ereignis zuzuordnen.  
  
-   Wenn die `Sub`\-Prozedur Ereignisse mit der `Handles`\-Klausel zuordnen muss, entfernen Sie die [Of](/dotnet/visual-basic/language-reference/statements/of-clause)\-Klausel aus ihrer Deklaration. Sie müssen für `Handles` eine nicht generische Prozedur verwenden.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NICHT IM BUILD: Ereignisse und Ereignishandler](http://msdn.microsoft.com/de-de/95074a0d-1cbc-4221-a95a-964185c7f962)