---
title: "CLS-Kompatibilit&#228;t: Warnung CLS01506 | Microsoft Docs"
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
  - "CLS01506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01506"
ms.assetid: 030f1b81-1159-4057-9fee-8721a419a5d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS01506
Die varargs\-Einschränkung ist nicht Teil der CLS.  
  
 Die varargs\-Einschränkung ist nicht Teil von CLS \(Common Language Subset\).  Die einzige Aufrufkonvention, die von CLS unterstützt wird, ist die verwaltete Standardaufrufkonvention.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsüberprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Funktionsdeklaration \(die die MSIL\-Assemblysprache verwendet\) zeigt, was CLS01506 verursachen könnte:  
  
```  
.method public instance vararg void  Method1() cil managed  
```  
  
 Sie können diese Warnung beheben, indem Sie das **vararg**\-Schlüsselwort entfernen:  
  
```  
.method public instance void  Method1() cil managed  
```