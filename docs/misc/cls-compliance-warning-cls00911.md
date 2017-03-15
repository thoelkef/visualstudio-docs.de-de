---
title: "CLS-Kompatibilit&#228;tswarnung CLS00911 | Microsoft Docs"
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
  - "CLS00911"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00911"
ms.assetid: d1a4721a-a3a6-4de0-bc14-a0b3c5e6dd78
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS00911
Literale statische Felder einer Enumeration müssen den Typ der Enumeration selbst ausweisen.  
  
 Stellen Sie sicher, dass die literalen statischen Felder einer Enumeration dem Typ der Enumeration selbst entsprechen.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Deklaration \(unter Verwendung der MSIL\-Assemblysprache\) zeigt, was CLS00911 verursachen könnte:  
  
```  
.assembly extern legacy library mscorlib {} .assembly legacy library Out {} .namespace Test { .class public auto ansi sealed MyEnum1 extends [mscorlib]System.Enum { .field public specialname rtspecialname int32 value__ .field public static literal uint8 One = uint8(0x1) } // end of class MyEnum1 }  
```  
  
 Sie können diese Warnung beheben, indem Sie das Enumerationsfeld auf den Typ der Enumeration festlegen:  
  
```  
.assembly extern legacy library mscorlib {} .assembly legacy library Out {} .namespace Test { .class public auto ansi sealed MyEnum1 extends [mscorlib]System.Enum { .field public specialname rtspecialname int32 value__ .field public static literal valuetype Test.MyEnum1 One = uint8(0x1) } // end of class MyEnum1 }  
```