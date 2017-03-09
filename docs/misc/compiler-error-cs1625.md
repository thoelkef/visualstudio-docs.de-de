---
title: "Compilerfehler CS1625 | Microsoft Docs"
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
  - "CS1625"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1625"
ms.assetid: 0b25b7f9-a585-49b0-9ee6-4384e87fcea6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1625
"yield" kann nicht im Text einer finally\-Klausel verwendet werden.  
  
 Eine yield\-Anweisung ist im Text einer finally\-Klausel nicht zulässig. Verschieben Sie die yield\-Anweisung aus der finally\-Klausel, um diesen Fehler zu vermeiden.  
  
 Im folgenden Beispiel wird CS1625 generiert:  
  
```  
// CS1625.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { try { } finally { yield return this;  // CS1625 } } } public class CMain { public static void Main() { } }  
  
```