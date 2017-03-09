---
title: "CLS-Kompatibilit&#228;tswarnung CLS01512 | Microsoft Docs"
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
  - "CLS01512"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01512"
ms.assetid: 15822eb3-43b1-4d58-a22d-9532e5820008
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS01512
Die varargs\-Einschränkung ist nicht Teil der CLS  
  
 Die varargs\-Einschränkung ist nicht Teil von CLS \(Common Language Subset\).  Die einzige Aufrufkonvention, die von CLS unterstützt wird, ist die verwaltete Standardaufrufkonvention.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Funktionsdeklaration \(unter Verwendung der MSIL\-Assemblysprache\) zeigt, was CLS01512 verursachen könnte:  
  
```  
.method public specialname rtspecialname static vararg void  .cctor() cil managed  
```  
  
 Sie können diese Warnung beheben, indem Sie das **vararg**\-Schlüsselwort entfernen:  
  
```  
.method public specialname rtspecialname static void  .cctor() cil managed  
```