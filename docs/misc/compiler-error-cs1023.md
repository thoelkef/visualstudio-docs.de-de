---
title: "Compilerfehler CS1023 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1023"
ms.assetid: 27d70f2c-9ae1-459c-a6be-01ed5a3eea07
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1023
Eine eingebettete Anweisung kann keine Deklaration und keine Anweisung mit Bezeichnung sein.  
  
 Eine eingebettete Anweisung, z. B. die auf eine **if**\-Anweisung folgenden Anweisungen, kann weder Deklarationen noch Anweisungen mit Bezeichnung enthalten.  
  
 Im folgenden Beispiel wird CS1023 generiert:  
  
```  
// CS1023.cs public class a { public static void Main() { if (1) int i;      // CS1023, declaration is not valid here if (1) xx : i++;   // CS1023, labeled statement is not valid here } }  
```