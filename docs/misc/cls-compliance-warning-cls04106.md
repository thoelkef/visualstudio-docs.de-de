---
title: "CLS-Kompatibilit&#228;tswarnung CLS04106 | Microsoft Docs"
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
  - "CLS04106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04106"
ms.assetid: a74e4cb7-c96a-4673-bf11-c2ff3c4b02f1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS04106
Attribute sollten vom Typ „System::Attribute“ sein von von diesem erben.  
  
 Um CLS\-Kompatibilität zu gewährleisten, muss ein benutzerdefiniertes Attribut von „System:: Attribute“ erben.  Ein Attribut, das nicht von „System::Attribute“ geerbt hat, wurde auf eine Funktion angewendet.  
  
 Die folgende Deklaration \(unter Verwendung von MSIL\-Assemblysprache\) zeigt, was CLS04106 verursachen könnte:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 und dann eine Funktion, die das Attribut verwendet:  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 01 00 00 00 00 00 )  
```  
  
 Indem Sie das Attribut von „System::Attribute“ ableiten, wird die Warnung aufgelöst:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```