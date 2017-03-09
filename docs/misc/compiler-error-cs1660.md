---
title: "Compilerfehler CS1660 | Microsoft Docs"
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
  - "CS1660"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1660"
ms.assetid: ae7fede3-471b-4e20-97a7-b80fdc2bb080
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1660
Ein anonymer Methodenblock kann nicht in den Typ 'typ' konvertiert werden, da es sich nicht um einen Delegattyp handelt  
  
 Dieser Fehler tritt auf, wenn Sie versuchen, einen Methodenblock einem Typ zuzuweisen, der kein Delegattyp ist, oder ihn in anderer Weise zu konvertieren versuchen.  
  
 Im folgenden Beispiel wird CS1660 generiert:  
  
```  
// CS1660.cs delegate int MyDelegate(); class C { static void Main() { int i = delegate { return 1; };  // CS1660 // Try this instead: // MyDelegate myDelegate = delegate { return 1; }; // int i = myDelegate(); } }  
```