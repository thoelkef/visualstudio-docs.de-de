---
title: "Compilerfehler CS1100 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1100"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1100"
ms.assetid: ea233371-36b6-49ae-a98c-a00ee3b79e53
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1100
Die Methode 'Name' weist den this\-Parametermodifizierer auf, der nicht für den ersten Parameter angegeben ist.  
  
 Der `this`\-Modifizierer ist nur für den ersten Parameter einer Methode zulässig, wodurch dem Compiler angezeigt wird, dass es sich bei der Methode um eine Erweiterungsmethode handelt.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie den `this`\-Modifizierer überall, außer für den ersten Parameter der Methode.  
  
## Beispiel  
 Der folgende Code führt zu Fehler CS1100, da ein `this` \-Parameter den zweiten Parameter ändert:  
  
```  
// cs1100.cs static class Test { static void ExtMethod(int i, this Test c) // CS1100 { } }  
```  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)