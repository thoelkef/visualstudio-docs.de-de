---
title: "Compilerfehler CS0685 | Microsoft Docs"
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
  - "CS0685"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0685"
ms.assetid: 20d7c6cf-a388-430f-b22b-232536912491
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0685
Der bedingte Member 'member' kann keinen out\-Parameter enthalten  
  
 Bei der Verwendung des <xref:System.Diagnostics.ConditionalAttribute>\-Attributs für eine Methode darf die betreffende Methode keinen out\-Parameter aufweisen. Das hat den Grund, dass der Wert der für den out\-Parameter verwendeten Variablen nicht definiert wäre, falls der Methodenaufruf zu 'nothing' kompiliert wird. Um diesen Fehler zu vermeiden, entfernen Sie den out\-Parameter aus der Deklaration der bedingten Methode, oder verwenden Sie nicht das Conditional\-Attribut.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0685 generiert:  
  
```  
// CS0685.cs using System.Diagnostics; class C { [Conditional("DEBUG")] void trace(out int i)  // CS0685 { i = 1; } }  
```