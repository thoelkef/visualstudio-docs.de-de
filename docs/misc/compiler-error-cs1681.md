---
title: "Compilerfehler CS1681 | Microsoft Docs"
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
  - "CS1681"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1681"
ms.assetid: 99934e15-1db8-4b71-9da8-a681a1d47407
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1681
Sie können den globalen externen Alias nicht neu definieren.  
  
 Der globale Alias ist bereits für die Aufnahme aller Verweise ohne Alias definiert und kann folglich nicht neu definiert werden.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1681 generiert.  
  
```  
// CS1681.cs // compile with: /reference:global=System.dll // CS1681 expected // try this instead: /reference:System.dll class A { static void Main() {} }  
```