---
title: "Compilerfehler CS1934 | Microsoft Docs"
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
  - "CS1934"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1934"
ms.assetid: 18624be3-d534-4695-bafd-cc664fcde15e
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1934
Es konnte keine Implementierung des Abfragemusters für den Quelltyp "Typ" gefunden werden. "Methode" wurde nicht gefunden. Geben Sie den Typ der Bereichsvariablen "Name" explizit an.  
  
 Dieser Fehler wird ausgelöst, wenn ein Abfrageausdruck eine Datenquelle angibt, für die keine Standardabfrageoperatoren implementiert sind. Eine Möglichkeit, diesen Fehler auszulösen, besteht darin, ein `ArrayList`\-Objekt ohne einen expliziten Typ für die Bereichsvariable anzugeben.  
  
### So beheben Sie diesen Fehler  
  
1.  Im folgenden Beispiel besteht die Lösung einfach darin, dass der Typ der Bereichsvariablen angegeben wird.  
  
    ```  
    var q = from int x in list  
    ```  
  
## Beispiel  
 Im folgenden Beispiel wird eine Möglichkeit zum Auslösen von CS1934 dargestellt:  
  
```  
// cs1934.cs using System.Linq; using System.Collections; static class Test { public static void Main() { var list = new ArrayList { 0, 1, 2, 3, 4, 5 }; var q = from x in list // CS1934 select x + 1; } }  
```  
  
## Siehe auch  
 [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)