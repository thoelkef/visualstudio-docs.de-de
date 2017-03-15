---
title: "Compilerfehler CS1939 | Microsoft Docs"
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
  - "CS1939"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1939"
ms.assetid: 9a7cdd48-3d45-473a-a799-c7771ef8158d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1939
Die Bereichsvariable "name" kann nicht als out\-Parameter oder ref\-Parameter übergeben werden.  
  
 Eine Bereichsvariable ist eine schreibgeschützte Variable, die in einem Abfrageausdruck eingeführt wird und als Bezeichner für jedes darauffolgende Element in einer Quellsequenz dient. Da die Variable in keiner Weise geändert werden kann, ist es nicht sinnvoll, sie durch `ref` oder `out` zu übergeben. Daher ist keiner der beiden Vorgänge gültig.  
  
### So beheben Sie diesen Fehler  
  
1.  Übergeben Sie die Bereichsvariable nach Wert.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1939 generiert:  
  
```  
// cs1939.cs using System.Linq; class Test { public static void F(ref int i) { } public static void Main() { var list = new int[] { 0, 1, 2, 3, 4, 5 }; var q = from x in list let k = x select Test.F(ref x); // CS1939 } }  
```