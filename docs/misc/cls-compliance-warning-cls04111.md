---
title: "CLS-Kompatibilit&#228;tswarnung CLS04111 | Microsoft Docs"
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
  - "CLS04111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04111"
ms.assetid: 4b445ce7-d823-4cf3-b971-1c181be5fa41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS04111
Attribute sollten vom Typ „System::Attribute“ sein von von diesem erben.  
  
 Um CLS\-Kompatibilität zu gewährleisten, muss ein benutzerdefiniertes Attribut von „System:: Attribute“ erben.  Ein Attribut, das nicht von „System::Attribute“ geerbt hat, wurde auf einen Typ angewendet.  
  
 Die folgende Deklaration \(unter Verwendung von MSIL\-Assemblysprache\) zeigt, was CLS04111 verursachen könnte:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 Indem Sie das Attribut von „System::Attribute“ ableiten, wird die Warnung aufgelöst:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```