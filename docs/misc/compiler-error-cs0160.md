---
title: "Compilerfehler CS0160 | Microsoft Docs"
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
  - "CS0160"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0160"
ms.assetid: 4ef07061-8ef5-42d9-b043-3f81307d569f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0160
Eine vorherige Catch\-Klausel hat bereits alle Ausnahmen dieses oder eines übergeordneten Typs abgefangen \(„type“\).  
  
 Eine Reihe von **catch**\-Anweisungen muss in absteigender Reihenfolge der Ableitung angegeben sein. Die meisten abgeleiteten Objekte müssen beispielsweise zuerst angezeigt werden.  
  
 Weitere Informationen finden Sie unter [Ausnahmebehandlungsanweisungen](/dotnet/csharp/language-reference/keywords/exception-handling-statements) und [Ausnahmen und Ausnahmebehandlung](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 Im folgenden Beispiel wird CS0160 generiert:  
  
```  
// CS0160.cs public class MyClass2 : System.Exception {} public class MyClass { public static void Main() { try {} catch(System.Exception) {}   // Second-most derived; should be second catch catch(MyClass2) {}   // CS0160  Most derived; should be first catch } }  
```