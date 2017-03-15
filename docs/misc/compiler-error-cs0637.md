---
title: "Compilerfehler CS0637 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0637"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0637"
ms.assetid: 02f6964c-0fcc-4f81-8ebb-0330aecdde19
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0637
Das FieldOffset\-Attribut ist für statische oder konstante Felder nicht zulässig.  
  
 Das [FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic)\-Attribut darf nicht für Felder verwendet werden, die mit [static](/dotnet/csharp/language-reference/keywords/static) oder [const](/dotnet/csharp/language-reference/keywords/const) gekennzeichnet sind.  
  
 Im folgenden Beispiel wird CS0637 generiert:  
  
```  
// CS0637.cs using System; using System.Runtime.InteropServices; [StructLayout(LayoutKind.Explicit)] public class MainClass { [FieldOffset(3)]   // CS0637 public static int i; public static void Main () { } }  
```