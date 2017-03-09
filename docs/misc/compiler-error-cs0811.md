---
title: "Compilerfehler CS0811 | Microsoft Docs"
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
  - "CS0811"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0811"
ms.assetid: 99f81ad3-684f-47aa-adb8-360e24901454
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0811
Der vollqualifizierte Name für "name" ist zu lang für Debuginformationen. Führen Sie die Kompilierung ohne die \/debug\-Option durch.  
  
 Variablen\- und Typnamen in den Debuginformationen unterliegen Größenbeschränkungen.  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn eine Namensänderung nicht möglich ist, besteht die einzige Alternative in der Kompilierung ohne die [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)\-Option.  
  
## Beispiel  
 Der folgende Code generiert CS0811:  
  
```  
// cs0811.cs //Compile with: /debug using System; using System.Collections.Generic; namespace TestNamespace { using Long = List<List<List<List<List<List<List<List<List<List<List<List<List <List<List<List<List<List<List<List<List<List<List<List<List<List<List<List<int>>>>>>>>>>>>>>>>>>>>>>>>>>>>; // CS0811 class Test { static int Main() { return 1; } } }  
```