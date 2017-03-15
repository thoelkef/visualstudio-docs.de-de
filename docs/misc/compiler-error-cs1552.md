---
title: "Compilerfehler CS1552 | Microsoft Docs"
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
  - "CS1552"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1552"
ms.assetid: 647af14d-249e-4f69-80a8-2c0d77fbb244
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1552
Der Arraytypspezifizierer \[\] muss vor dem Parameternamen stehen.  
  
 Der Arraytypspezifizierer befindet sich in der Arraydeklaration hinter dem Variablennamen.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1552 generiert:  
  
```  
// CS1552.cs public class C { public static void Main(string args[])   // CS1552 // try the following line instead // public static void Main(string [] args) { } }  
```