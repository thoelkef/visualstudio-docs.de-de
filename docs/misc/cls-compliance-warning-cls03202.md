---
title: "CLS-Kompatibilit&#228;t: Warnung CLS03202 | Microsoft Docs"
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
  - "CLS03202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03202"
ms.assetid: 2219c86c-9276-4244-a2ff-bce578c4d65f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS03202
Die add\- und remove\-Methoden eines Ereignisses müssen jeweils einen Parameter erhalten, dessen Typ den Ereignistyp definiert. Dieser Typ muss von System.Delegate abgeleitet sein.  
  
 Die add\- und remove\-Methoden eines Ereignisses müssen jeweils einen Parameter erhalten, dessen Typ den Ereignistyp definiert. Dieser Typ muss von System.Delegate abgeleitet sein.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Funktionsdeklaration \(unter Verwendung der MSIL\-Assemblysprache\) zeigt, was CLS03202 verursachen könnte:  
  
```  
// bad .method public specialname instance void add_MyEvent(class MyDelegate __unnamed000, int32 __extra) cil managed {}  
```  
  
 Sie können diese Warnung beheben, wenn der Ereignisaccessor nur einen Parameter übernimmt:  
  
```  
.method public specialname instance void add_MyEvent(class MyDelegate __unnamed000) cil managed {}  
```