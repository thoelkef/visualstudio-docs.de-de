---
title: "System.Void kann nur in einem GetType-Ausdruck verwendet werden. | Microsoft Docs"
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
  - "bc31422"
  - "vbc31422"
helpviewer_keywords: 
  - "BC31422"
ms.assetid: 84e45194-cb46-41f6-8420-a1498baeaaba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Void kann nur in einem GetType-Ausdruck verwendet werden.
Ein Ausdruck in einer Anweisung oder Deklaration verwendet <xref:System.Void> als Typ einer Variablen, eines Prozedurparameters, einer Funktionsrückgabe oder eines Typargument.  
  
 Die <xref:System.Void>\-Struktur ist ein spezieller Typ, der intern von .NET Framework und insbesondere von Visual C\# und Visual C\+\+ verwendet wird. Die Struktur stellt einen Rückgabewerttyp für eine Methode dar, die keinen Wert zurückgibt. Visual Basic verwendet eine `Sub`\-Prozedur, wenn kein Wert zurückgegeben wird, und eine `Function`\-Prozedur, wenn ein Wert zurückgegeben wird.  
  
 Sie können eine Verweisvariable mit dem [GetType Operator](/dotnet/visual-basic/language-reference/operators/gettype-operator) testen, um festzustellen, ob die Variable den Laufzeittyp <xref:System.Void> hat, aber Sie können <xref:System.Void> in keinem anderen Kontext verwenden.  
  
 **Fehler\-ID:** BC31422  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn Sie den Laufzeittyp einer Variablen mit <xref:System.Void> vergleichen möchten, verwenden Sie den `GetType`\-Operator.  
  
2.  Sofern es keinen bestimmten Grund gibt, einen Laufzeittyp mit <xref:System.Void> zu vergleichen, sollten Sie den Verweis darauf vollständig entfernen.  
  
## Siehe auch  
 <xref:System.Void>   
 [GetType Operator](/dotnet/visual-basic/language-reference/operators/gettype-operator)