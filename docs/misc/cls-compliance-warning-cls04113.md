---
title: "CLS-Kompatibilit&#228;tswarnung CLS04113 | Microsoft Docs"
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
  - "CLS04113"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04113"
ms.assetid: 628f56bf-5f2f-4245-b4fd-02d4605a901c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS04113
**Attribute müssen vom Typ 'System::Attribute' sein oder von diesem erben.**  
  
 Um CLS\-Kompatibilität zu gewährleisten, muss ein benutzerdefiniertes Attribut von 'System:: Attribute' erben.  
  
 Weitere Informationen zur Überprüfung der CLS\-Kompatibilität \(Common Language Subset\) finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Deklaration \(unter Verwendung von MSIL\-Assemblysprache\) zeigt, was CLS04100 verursachen könnte:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 Indem Sie das Attribut von „System::Attribute“ ableiten, wird die Warnung aufgelöst:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```