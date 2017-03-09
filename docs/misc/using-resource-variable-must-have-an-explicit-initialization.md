---
title: "Die Using-Ressourcenvariable muss &#252;ber eine explizite Initialisierung verf&#252;gen. | Microsoft Docs"
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
  - "vbc36011"
  - "bc36011"
helpviewer_keywords: 
  - "BC36011"
ms.assetid: 5db996a6-0802-4b67-91f1-4aa9c3dd6b09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Using-Ressourcenvariable muss &#252;ber eine explizite Initialisierung verf&#252;gen.
Eine `Using`\-Anweisung gibt mindestens eine Ressource an, die sie nicht mit einer `New`\-Klausel initialisiert.  
  
 Wenn Sie die Ressource nicht bereits abgerufen haben, bevor die Kontrolle an den `Using`\-Block übergeben wird, muss die Ressource von der `Using`\-Anweisung abgerufen werden. Zu diesem Zweck muss sie ein Objekt aus der angegebenen Klasse erstellen, die eine `New`\-Klausel erfordert.  
  
 **Fehler\-ID:** BC36011  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie die Ressource bereits abgerufen haben, verwenden Sie eine Verweisvariable oder einen Ausdruck in der `Using`\-Anweisung, die in die abgerufene Ressource ausgewertet wird.  
  
     `Dim newFont As New System.Drawing.Font`  
  
     `Using newFont`  
  
-   Wenn Sie die Ressource nicht bereits abgerufen haben, fügen Sie eine `New`\-Klausel zur `Using`\-Anweisung hinzu.  
  
     `Using newFont as`   `New`   `System.Drawing.Font`  
  
## Siehe auch  
 [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)