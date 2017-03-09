---
title: "CLS-Kompatibilit&#228;tswarnung CLS04114 | Microsoft Docs"
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
  - "CLS04114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04114"
ms.assetid: 84285fbb-ecd1-46e6-9bdb-dc44db40dcc0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS04114
Attribute sollten vom Typ „System::Attribute“ sein und von diesem erben.  
  
 Um CLS\-Kompatibilität zu gewährleisten, muss ein benutzerdefiniertes Attribut von „System:: Attribute“ erben.  Ein Attribut, das nicht von „System::Attribute“ geerbt hat, wurde auf einen Delegat angewendet.  
  
 Weitere Informationen zur Überprüfung der CLS\-Kompatibilität \(Common Language Subset\) finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Deklaration \(unter Verwendung von MSIL\-Assemblysprache\) zeigt, was CLS04100 verursachen könnte:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 und dann ein Delegat, der das Attribut verwendet:  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 01 00 00 00 00 00 )  
```  
  
 Indem Sie das Attribut von „System::Attribute“ ableiten, wird die Warnung aufgelöst:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```