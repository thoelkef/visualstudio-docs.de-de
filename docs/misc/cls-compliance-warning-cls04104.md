---
title: "CLS-Kompatibilit&#228;t: Warnung CLS04104 | Microsoft Docs"
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
  - "CLS04104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04104"
ms.assetid: 89a5c080-c7f3-48b5-b2ff-90aa2236c90e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS04104
Attribute müssen vom Typ "System::Attribute" sein oder von diesem erben.  
  
 Um CLS\-Kompatibilität zu gewährleisten, muss ein benutzerdefiniertes Attribut von "System:: Attribute" erben.  Ein Attribut, das nicht von "System::Attribute" geerbt hat, wurde auf eine Memberfunktion angewendet.  
  
 Die folgende Deklaration \(unter Verwendung von MSIL\-Assemblysprache\) zeigt, was CLS04111 verursachen könnte:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 und dann eine Memberfunktion, die das Attribut verwendet:  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 00 00 00 00 00 00 )  
```  
  
 Sie beheben den Fehler, indem Sie das Attribut von "System::Attribute" ableiten:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```