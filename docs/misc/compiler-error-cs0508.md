---
title: "Compilerfehler CS0508 | Microsoft Docs"
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
  - "CS0508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0508"
ms.assetid: 28403573-6e64-4496-918d-fb50c8851e51
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0508
'Typ 1': Der Typ muss 'Typ 2' sein, um mit dem überschriebenen Member 'MemberName' übereinzustimmen.  
  
 Es wurde versucht, den Rückgabetyp in einer Methodenüberschreibung zu ändern. Um diesen Fehler zu beheben, stellen Sie sicher, dass beide Methoden denselben Rückgabetyp deklarieren.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0508 generiert:  
  
```  
// CS0508.cs // compile with: /target:library abstract public class Clx { public int i = 0; // Return type is int. abstract public int F(); } public class Cly : Clx { public override double F() { return 0.0;   // CS0508 } }  
```