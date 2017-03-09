---
title: "Compilerfehler CS1935 | Microsoft Docs"
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
  - "CS1935"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1935"
ms.assetid: d5dda801-fbf3-4340-bfe1-f9409f2d344d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1935
Es konnte keine Implementierung des Abfragemusters für den Quelltyp „type“ gefunden werden. „method“ wurde nicht gefunden. Möglicherweise fehlt einen Verweis auf „System.Core.dll“ oder eine using\-Direktive für „System.Linq“?  
  
 Der Quelltyp in einer Abfrage muss `IEnumerable`, `IEnumerable<T>` oder ein abgeleiteter Typ bzw. ein Typ sein, für den die standardmäßigen Abfrageoperatoren implementiert wurden. Wenn der Quelltyp ein `IEnumerable` oder `IEnumerable<T>`ist, müssen Sie einen Verweis auf „system.core.dll“ und eine `using`\-Direktive für den „System.Linq“\-Namespace hinzufügen, um die Standardabfrageoperator\-Erweiterungsmethoden in den Gültigkeitsbereich einzubinden. Benutzerdefinierte Implementierungen der Standardabfrageoperatoren müssen auf die gleiche Weise mit einer `using`\-Direktive und, falls erforderlich, einem Verweis auf die Assembly in den Gültigkeitsbereich eingebunden werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie die erforderlichen using\-Direktiven und Verweise auf das Projekt hinzu.  
  
## Beispiel  
 Der folgende Code generiert den Fehler CS1935, da die `using`\-Direktive für „System.Linq“ auskommentiert ist:  
  
```  
// cs1935.cs // CS1935 using System; using System.Collections.Generic; // using System.Linq; class Test { static int Main() { int[] nums = {0,1,2,3,4,5}; IEnumerable<int> e = from n in nums where n > 3 select n; return 0; } }  
```  
  
## Siehe auch  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)