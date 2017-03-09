---
title: "Compilerfehler CS0662 | Microsoft Docs"
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
  - "CS0662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0662"
ms.assetid: 836fa15e-3bf3-4af5-8acf-072d7d731dcd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0662
"Methode" kann nicht allein das Out\-Attribut für einen ref\-Parameter angeben. Verwenden Sie "In" zusammen mit "Out" oder keines von beiden.  
  
 Eine Schnittstellenmethode hat einen Parameter, in dem [ref](/dotnet/csharp/language-reference/keywords/ref) nur mit dem [Out](frlrfSystemRuntimeInteropServicesOutAttributeClassTopic)\-Attribut verwendet wird. In einem `ref`\-Parameter, in dem das **Out**\-Attribut verwendet wird, muss auch das [In](frlrfSystemRuntimeInteropServicesInAttributeClassTopic)\-Attribut verwendet werden.  
  
 Im folgenden Beispiel wird CS0662 generiert:  
  
```  
// CS0662.cs using System.Runtime.InteropServices; interface I { void method([Out] ref int i);   // CS0662 // try one of the following lines instead // void method(ref int i); // void method([Out, In]ref int i); } class test { public static void Main() { } }  
```