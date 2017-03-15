---
title: "CLS-Kompatibilit&#228;t: Warnung CLS01501 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01501"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01501"
ms.assetid: 74361331-3773-48d5-8508-0113f5464a75
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS01501
**Die varargs\-Einschränkung ist nicht Teil der CLS**  
  
 Die varargs\-Einschränkung ist nicht Teil von CLS \(Common Language Subset\).  Die einzige Aufrufkonvention, die von CLS unterstützt wird, ist die verwaltete Standardaufrufkonvention.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsüberprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Funktionsdeklaration \(unter Verwendung der MSIL\-Assemblysprache\) zeigt, was CLS01501 verursachen könnte:  
  
```  
.method public specialname rtspecialname instance vararg void  .ctor() cil managed  
```  
  
 Sie können CLS01501 auflösen, indem Sie ein Parameterarray verwenden.  Weitere Informationen finden Sie unter [Variable Argument Lists \(...\) \(C\+\+\/CLI\)](/visual-cpp/windows/variable-argument-lists-dot-dot-dot-cpp-cli).