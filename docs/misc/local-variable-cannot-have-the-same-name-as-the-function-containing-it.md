---
title: "Eine lokale Variable darf nicht denselben Namen haben wie die Funktion, in der sie enthalten ist | Microsoft Docs"
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
  - "vbc30290"
  - "bc30290"
helpviewer_keywords: 
  - "BC30290"
ms.assetid: 34c38cff-fb9c-406d-82e8-ca251ee77104
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eine lokale Variable darf nicht denselben Namen haben wie die Funktion, in der sie enthalten ist
Eine `Dim`\-Anweisung gibt eine Variable mit demselben Namen wie die `Function`\-Prozedur an, die sie enthält.  
  
 **Fehler\-ID:** BC30290  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die Variablendeklaration, oder ändern Sie den Namen der Variablen.  
  
## Siehe auch  
 [NOTINBUILD: Auflösen eines Verweises bei mehreren Variablen mit gleichem Namen](http://msdn.microsoft.com/de-de/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [Function\-Prozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)