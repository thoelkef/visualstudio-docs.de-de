---
title: "Compilerfehler CS1104 | Microsoft Docs"
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
  - "CS1104"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1104"
ms.assetid: 65bfe85f-8dd1-4aed-bcd1-1f7e0635868c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1104
Ein Parameterarray kann für eine Erweiterungsmethode nicht mit dem this\-Modifizierer verwendet werden.  
  
 Der erste Parameter einer Erweiterungsmethode darf kein Parameterarray sein.  
  
### So beheben Sie diesen Fehler  
  
1.  Beachten Sie, dass der erste Parameter in der Definition einer Erweiterungsmethode den Typ angibt, der von der Methode erweitert wird. Es ist kein Eingabeparameter. Daher ergibt es keinen Sinn, an dieser Stelle ein Parameterarray zu verwenden. Wenn Sie ein Parameterarray übergeben müssen, verwenden Sie es als zweiten Parameter.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1104 generiert:  
  
```  
// cs1104.cs // Compile with: /target:library public static class Extensions { public static void Test<T>(this params T[] tArr) {} // CS1104 }   
```  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)