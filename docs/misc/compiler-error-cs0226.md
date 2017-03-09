---
title: "Compilerfehler CS0226 | Microsoft Docs"
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
  - "CS0226"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0226"
ms.assetid: 9f8c74c4-de21-41fb-84e1-ef32a4b23ced
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0226
Ein \_\_arglist\-Ausdruck darf nur in einem call\- oder new\-Ausdruck enthalten sein.  
  
 Das nicht unterstützte `__arglist`\-Schlüsselwort darf nur in einem Methodenaufruf oder einem new\-Ausdruck enthalten sein.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS0226 ausgelöst:  
  
```  
// cs0226.cs using System; public class C { public static int Main () { __arglist(1,"This is a string"); // CS0226 return 0; } }  
```