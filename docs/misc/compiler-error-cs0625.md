---
title: "Compilerfehler CS0625 | Microsoft Docs"
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
  - "CS0625"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0625"
ms.assetid: 44091813-9988-436c-b35e-e24094793782
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0625
"field": Instanzenfeldtypen, die mit StructLayout\(LayoutKind.Explicit\) markiert sind, müssen ein FieldOffset\-Attribut aufweisen.  
  
 Wenn eine Struktur mit einem expliziten **StructLayout**\-Attribut markiert ist, müssen alle Felder in der Struktur das [FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic)\-Attribut enthalten. Weitere Informationen finden Sie unter [StructLayoutAttribute\-Klasse](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic).  
  
 Im folgenden Beispiel wird CS0625 generiert:  
  
```  
// CS0625.cs // compile with: /target:library using System; using System.Runtime.InteropServices; [StructLayout(LayoutKind.Explicit)] struct A { public int i;   // CS0625 not static; an instance field } // OK [StructLayout(LayoutKind.Explicit)] struct B { [FieldOffset(5)] public int i; }  
```