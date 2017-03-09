---
title: "Compilerfehler CS1017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1017"
ms.assetid: e0902e8a-b042-4711-a8a6-83456a3f88cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1017
Catch\-Klauseln können nicht auf die allgemeine catch\-Klausel einer try\-Anweisung folgen.  
  
 Ein `catch`\-Block, der keine Parameter annimmt, muss der letzte in einer Reihe von `catch`\-Blöcken sein. Weitere Informationen zu Ausnahmen finden Sie unter [Ausnahmebehandlungsanweisungen](/dotnet/csharp/language-reference/keywords/exception-handling-statements).  
  
## Beispiel  
 Im folgenden Beispiel wird CS1017 generiert:  
  
```  
// CS1017.cs using System; namespace x { public class b : Exception { } public class a { public static void Main() { try { } catch   // CS1017, must be last catch { } catch(b) { throw; } } } }  
```