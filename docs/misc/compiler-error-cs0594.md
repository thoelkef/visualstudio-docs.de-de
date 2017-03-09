---
title: "Compilerfehler CS0594 | Microsoft Docs"
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
  - "CS0594"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0594"
ms.assetid: a3d6bde1-db63-4c5c-a425-8c6a39e00999
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0594
Die Gleitkommakonstante liegt außerhalb des Bereichs von Typ "Typ".  
  
 Einer Gleitkommavariablen wurde ein Wert zugewiesen, der für die Variablen dieses Datentyps zu groß ist. Informationen zu dem für Datentypen zulässigen Wertebereich finden Sie in der [Tabelle ganzzahliger Typen](/dotnet/csharp/language-reference/keywords/integral-types-table).  
  
 Im folgenden Beispiel wird CS0594 generiert:  
  
```  
// CS0594.cs namespace MyNamespace { public class MyClass { public static void Main() { float f = 6.77777777777E400;   // CS0594, value too large } } }  
```