---
title: "Compilerfehler CS1663 | Microsoft Docs"
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
  - "CS1663"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1663"
ms.assetid: 013f36ac-8925-4cee-9008-54fa7ad1324b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1663
Puffer fester Größe müssen einen der folgenden Typen aufweisen: "bool", "byte", "short", "int", "long", "char", "sbyte", "ushort", "uint", "ulong", "float" oder "double".  
  
 Ein Puffer fester Größe darf keinen anderen als die hier aufgeführten Typen aufweisen. Um diesen Fehler zu vermeiden, verwenden Sie einen anderen Typ oder kein Array fester Größe.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1663 generiert.  
  
```  
// CS1663.cs // compile with: /unsafe /target:library unsafe struct C { fixed string ab[10];   // CS1663 }  
```