---
title: "Compilerwarnung (Stufe 1) CS1645 | Microsoft Docs"
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
  - "CS1645"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1645"
ms.assetid: ea45fb20-b696-4d4e-b893-edde9d96bd3a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1645
Feature 'Feature' ist nicht Teil der standardisierten ISO C\#\-Sprachspezifikation, und wird möglicherweise von anderen Compilern nicht unterstützt.  
  
 Das von Ihnen verwendete Feature ist nicht Teil des ISO\-Standards. Code, der dieses Feature verwendet, kann von anderen Compilern möglicherweise nicht kompiliert werden.  
  
```  
// CS1645.cs // compile with: /W:1 /t:module /langversion:ISO-1 [assembly:System.CLSCompliant(false)] // To supress the warning use the switch: /nowarn:1645 [module:System.CLSCompliant(false)]   // CS1645 class Test { }  
```