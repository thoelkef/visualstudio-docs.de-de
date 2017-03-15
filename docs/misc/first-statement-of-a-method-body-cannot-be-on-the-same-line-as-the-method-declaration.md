---
title: "Die erste Anweisung eines Methodentexts darf sich nicht auf derselben Zeile wie die Methodendeklaration befinden. | Microsoft Docs"
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
  - "vbc30040"
  - "bc30040"
helpviewer_keywords: 
  - "BC30040"
ms.assetid: 27df3488-de77-499d-b9a6-08037d540cb0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die erste Anweisung eines Methodentexts darf sich nicht auf derselben Zeile wie die Methodendeklaration befinden.
Eine `Function`\-, `Sub`\-, `Get`\-, `Set`\- oder `Property`\-Anweisung muss sich allein in einer Quellcodezeile befinden.  
  
 **Fehler\-ID:** BC30040  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie alle Zeilenbezeichnungen vor der Deklaration der Prozedur.  
  
2.  Verschieben Sie alle Anweisungen vor der Deklaration der Prozedur in eine vorherige Quellcodezeile.  
  
3.  Verschieben Sie alle Anweisungen nach der Deklaration der Prozedur in eine nachfolgende Quellcodezeile.  
  
## Siehe auch  
 [Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/index)   
 [How to: Label Statements](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)