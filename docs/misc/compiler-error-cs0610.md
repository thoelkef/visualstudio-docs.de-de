---
title: "Compilerfehler CS0610 | Microsoft Docs"
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
  - "CS0610"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0610"
ms.assetid: 6cdce74c-5c00-4539-9df1-32be70e9912d
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0610
Das Feld oder die Eigenschaft kann nicht vom Typ "Typ" sein  
  
 Es gibt einige Typen, die nicht als Felder oder Eigenschaften verwendet werden können. Zu diesen Typen gehören **System.ArgIterator** und **System.TypedReference**.  
  
 Im folgenden Beispiel wird CS0610 generiert, weil **System.TypedReference** als Feld verwendet wurde:  
  
```  
// CS0610.cs public class MainClass { System.TypedReference i;   // CS0610 public static void Main () { } public static void Test(System.TypedReference i)   // OK { } }  
```