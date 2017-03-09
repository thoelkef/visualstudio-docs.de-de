---
title: "Compilerfehler CS1730 | Microsoft Docs"
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
  - "CS1730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1730"
ms.assetid: 20900ca0-702f-4f35-9a60-2dee9cb11902
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1730
Assembly\- und Modulattribute müssen vor allen anderen in einer Datei definierten Elementen mit Ausnahme von using\-Klauseln und externen Aliasdeklarationen angegeben werden.  
  
 Ein Attribut, das auf Assemblyebene angewendet wird, kann nicht nach den Typdefinitionen stehen.  
  
### So beheben Sie diesen Fehler  
  
1.  Verschieben Sie das Attribut an den Anfang der Datei, aber unter die `using`\-Direktiven und die `extern`\-Aliasdeklarationen.  
  
## Beispiel  
 Der folgende Code generiert CS1730:  
  
```  
// cs1730.cs class Test { } [assembly: System.Attribute] // CS1730  
```  
  
## Siehe auch  
 [Attribute](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)