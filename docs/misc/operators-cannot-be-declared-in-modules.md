---
title: "Operatoren k&#246;nnen nicht in Modulen deklariert werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33018"
  - "vbc33018"
helpviewer_keywords: 
  - "BC33018"
ms.assetid: 10a8fd2d-2af7-4f90-9f2a-50c07ebf7589
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operatoren k&#246;nnen nicht in Modulen deklariert werden.
In einer Moduldefinition befindet sich eine [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement).  
  
 Sie können einen Operator als Teil einer zu definierenden Klasse oder Struktur definieren. Der Operator muss diese Klasse oder Struktur als mindestens einen Operanden verwenden.  
  
 Ein Operator muss eine Instanz eines Programmierelements als einen Operanden verwenden, und nur Klassen und Strukturen verfügen über Instanzen. Daher können Sie einen Operator nicht als Teil eines anderen Programmierelements definieren.  
  
 **Fehler\-ID:** BC33018  
  
### So beheben Sie diesen Fehler  
  
-   Wenn ein Vorgang für das Modul benötigt wird, verwenden Sie eine [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement), um eine `Function`\-Prozedur zu definieren, die den Vorgang ausführt.  
  
-   Sie können auch eine Klasse oder Struktur innerhalb des Moduls und einen Operator für diese Klasse oder Struktur definieren. Der Operator muss eine Instanz dieser Klasse oder Struktur als mindestens einen Operanden verwenden.  
  
## Siehe auch  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)