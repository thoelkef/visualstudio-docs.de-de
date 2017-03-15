---
title: "Compilerfehler CS1662 | Microsoft Docs"
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
  - "CS1662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1662"
ms.assetid: e61a4fc8-0ef1-4a4a-a27b-3a015c3ba38a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1662
Der anonyme Methodenblock kann nicht in den gewünschten Delegattyp 'Delegattyp' konvertiert werden, da einige der Rückgabetypen im Block nicht implizit in den Delegatrückgabetyp konvertiert werden können.  
  
 Dieser Fehler tritt auf, wenn die return\-Anweisung des anonymen Methodenblocks einen Typ enthielt, der nicht implizit in den Rückgabetyp des Delegaten konvertiert werden konnte.  
  
 Im folgenden Beispiel wird CS1662 generiert:  
  
```  
// CS1662.cs delegate int MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(int i) { return 1.0; };  // CS1662 // Try this instead: // MyDelegate d = dekegate(int i) { return (int)1.0; }; } }  
```