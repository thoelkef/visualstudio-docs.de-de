---
title: "Compilerfehler CS0636 | Microsoft Docs"
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
  - "CS0636"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0636"
ms.assetid: 47597f89-fbe6-4708-9493-3c86c6f0ce56
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0636
Das FieldOffset\-Attribut kann nur für Member des mit "StructLayout\(LayoutKind.Explicit\)" markierten Typs festgelegt werden.  
  
 Sie müssen das **StructLayout\(LayoutKind.Explicit\)** \-Attribut für die Strukturdeklaration verwenden, wenn sie mit dem **FieldOffset**\-Attribut markierte  Member enthält. Weitere Informationen finden Sie unter [FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic).  
  
 Im folgenden Beispiel wird CS0636 generiert:  
  
```  
// CS0636.cs using System; using System.Runtime.InteropServices; // To resolve the error, uncomment the following line: // [StructLayout(LayoutKind.Explicit)] struct Worksheet { [FieldOffset(4)]public int i;   // CS0636 } public class MainClass { public static void Main () { } }  
```