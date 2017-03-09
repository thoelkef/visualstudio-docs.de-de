---
title: "Compilerfehler CS1524 | Microsoft Docs"
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
  - "CS1524"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1524"
ms.assetid: a7b80bbc-a2de-4718-b0f0-4c9526726525
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1524
"catch" oder "finally" erwartet.  
  
 Ein `try`\-Block muss von einem `catch`\- oder `finally`\-Block gefolgt werden.  
  
 Weitere Informationen zu Ausnahmen finden Sie unter [Ausnahmebehandlungsanweisungen](/dotnet/csharp/language-reference/keywords/exception-handling-statements).  
  
## Beispiel  
 Im folgenden Beispiel wird CS1524 generiert:  
  
```  
// CS1524.cs class x { public static void Main() { try { // Code here } catch { } try { // Code here } finally { } try { // Code here } }     // CS1524, missing catch or finally }  
```