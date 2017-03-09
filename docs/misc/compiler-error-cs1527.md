---
title: "Compilerfehler CS1527 | Microsoft Docs"
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
  - "CS1527"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1527"
ms.assetid: a0d52130-d6da-41bb-b153-8e96cbb7e316
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1527
Die in einem Namespace definierten Elemente dürfen nicht explizit als "private", "protected" oder "protected internal" deklariert werden.  
  
 Typdeklarationen in einem Namespace können [öffentlichen](/dotnet/csharp/language-reference/keywords/public) oder [internen](/dotnet/csharp/language-reference/keywords/internal) Zugriff haben. Wenn keine Zugriffsart angegeben ist, wird standardmäßig der **interne** Zugriff verwendet.  
  
 Im folgenden Beispiel wird CS1527 generiert:  
  
```  
// CS1527.cs namespace Sample { private class C1 {};             // CS1527 protected class C2 {};           // CS1527 protected internal class C3 {};  // CS1527 }  
```  
  
 Im folgenden Beispiel wird CS1527 generiert, da sich alle Typdeklarationen implizit im globalen Namespace befinden, wenn kein Namespace explizit im Programmcode deklariert wird.  
  
```  
//cs1527_2.cs using System; protected class C4{} private struct S1{}  
```  
  
## Siehe auch  
 [Namespaces](/dotnet/csharp/programming-guide/namespaces/index)   
 [Global](/dotnet/csharp/language-reference/keywords/global)   
 [Operator ::](../Topic/::%20Operator%20\(C%23%20Reference\).md)   
 [Zugriffsdomäne](/dotnet/csharp/language-reference/keywords/accessibility-domain)   
 [Zugriffsmodifizierer](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)