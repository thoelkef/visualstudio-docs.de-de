---
title: "Compilerfehler CS0669 | Microsoft Docs"
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
  - "CS0669"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0669"
ms.assetid: c7f81869-79d7-481f-a026-2cef0e87df4c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0669
Eine Klasse mit dem ComImport\-Attribut kann keinen benutzerdefinierten Konstruktor haben.  
  
 Die COM\-Interop\-Ebene in der Common Language Runtime gibt den Konstruktor für [ComImport](frlrfSystemRuntimeInteropServicesComImportAttributeClassTopic)\-Klassen an. Folglich kann ein COM\-Objekt als ein verwaltetes Objekt in der Laufzeit verwendet werden.  
  
 Im folgenden Beispiel wird CS0669 generiert:  
  
```  
// CS0669.cs using System.Runtime.InteropServices; [ComImport, Guid("00000000-0000-0000-0000-000000000001")] class TestClass { TestClass()   // CS0669, delete constructor to resolve { } public static void Main() { } }  
```