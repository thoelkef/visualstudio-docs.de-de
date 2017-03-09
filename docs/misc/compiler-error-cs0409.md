---
title: "Compilerfehler CS0409 | Microsoft Docs"
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
  - "CS0409"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0409"
ms.assetid: 23d86c13-7978-41b7-a087-ffcea52476fa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0409
Für den Typparameter 'Typparameter' wurde bereits eine Einschränkungsklausel angegeben. Alle Einschränkungen für einen Typparameter müssen in einer einzelnen Where\-Klausel angegeben werden.  
  
 Mehrere Einschränkungsklauseln \(Where\-Klauseln\) wurden für einen einzelnen Typparameter gefunden. Entfernen Sie die überflüssige Where\-Klausel, oder korrigieren Sie die Where\-Klauseln, damit sich in jeder Klausel ein eindeutiger Typparameter befindet.  
  
```  
// CS0409.cs interface I { } class C<T1, T2> where T1 : I where T1 : I  // CS0409 – T1 used twice { }  
```