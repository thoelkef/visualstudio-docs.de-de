---
title: "&#39;&lt;Parametername&gt;&#39; ist bereits als Typparameter dieser Methode deklariert. | Microsoft Docs"
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
  - "bc32089"
  - "vbc32089"
helpviewer_keywords: 
  - "BC32089"
ms.assetid: 5e440b4b-f62b-4ff5-9148-2372d4752bf6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Parametername&gt;&#39; ist bereits als Typparameter dieser Methode deklariert.
Eine generische Prozedur definiert einen normalen Parameter oder eine lokale Variable mit demselben Namen wie einen Typparameter.  
  
 Jeder Parameter einer Prozedur, einschließlich jedes Typparameters einer generischen Prozedur, muss einen Namen besitzen, der sich von allen anderen Parametern unterscheidet. Da Prozedurparameter als lokale Variablen verwendet werden, muss auch jede lokale Variable, die innerhalb der Prozedur deklariert ist, einen Namen aufweisen, der sich von allen Parametern und Typparametern unterscheidet.  
  
 **Fehler\-ID:** BC32089  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Namen des normalen Parameter oder der lokalen Variablen.  
  
## Siehe auch  
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Parameter List](/dotnet/visual-basic/language-reference/statements/parameter-list)