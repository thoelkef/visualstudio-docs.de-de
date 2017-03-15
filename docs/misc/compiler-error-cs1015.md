---
title: "Compilerfehler CS1015 | Microsoft Docs"
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
  - "CS1015"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1015"
ms.assetid: 53179feb-e8be-41e0-bb0b-f7879e9fa613
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1015
Objekt, Zeichenfolge oder Klassentyp erwartet.  
  
 Es wurde versucht, einen vordefinierten Datentyp in einen [catch](/dotnet/csharp/language-reference/keywords/try-catch)\-Block zu übergeben. An einen <xref:System.Exception?displayProperty=fullName>\-Block können nur Datentypen übergeben werden, die von `catch` abgeleitet wurden. Weitere Informationen zu Ausnahmen finden Sie unter [Ausnahmebehandlungsanweisungen](/dotnet/csharp/language-reference/keywords/exception-handling-statements).  
  
## Beispiel  
 Im folgenden Beispiel wird CS1015 generiert:  
  
```  
// CS1015.cs class Sample { static void Main() { try { } catch(int)   // CS1015, int is not derived from System.Exception { } } }  
```