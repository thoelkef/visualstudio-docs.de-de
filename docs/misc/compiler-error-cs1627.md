---
title: "Compilerfehler CS1627 | Microsoft Docs"
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
  - "CS1627"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1627"
ms.assetid: 58dd6e22-e9ed-4e5c-ae04-ce255f07064e
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1627
Ausdruck nach "yield return" erwartet.  
  
 Dieser Fehler tritt auf, wenn `yield` ohne einen Ausdruck verwendet wird. Um diesen Fehler zu vermeiden, fügen Sie den entsprechenden Ausdruck in die Anweisung ein.  
  
 Im folgenden Beispiel wird CS1627 generiert:  
  
```  
// CS1627.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { yield return;   // CS1627 // To resolve, add the following line: // yield return 0; } } public class CMain { public static void Main() { } }  
```