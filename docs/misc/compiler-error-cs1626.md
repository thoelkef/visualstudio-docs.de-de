---
title: "Compilerfehler CS1626 | Microsoft Docs"
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
  - "CS1626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1626"
ms.assetid: 3ba03383-eb24-4fd8-bf40-8b0f7d6baf0d
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1626
Mit "yield" kann im Text eines try\-Blocks mit einer catch\-Klausel kein Wert zurückgegeben werden.  
  
 Eine yield\-Anweisung ist in einem try\-Block nicht zulässig, wenn eine dem try\-Block zugeordnete catch\-Klausel vorhanden ist. Verschieben Sie die yield\-Anweisung aus der catch\-Klausel, um diesen Fehler zu vermeiden.  
  
 Im folgenden Beispiel wird CS1626 generiert:  
  
```  
// CS1626.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { try { yield return this;  // CS1626 } catch { } } } public class CMain { public static void Main() { } }  
  
```