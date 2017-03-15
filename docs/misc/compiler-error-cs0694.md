---
title: "Compilerfehler CS0694 | Microsoft Docs"
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
  - "CS0694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0694"
ms.assetid: 048615e4-4599-4726-b5db-55322ccc936f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0694
Der Bezeichner\-Typparameter hat den gleichen Namen wie der enthaltende Typ bzw. die enthaltende Methode.  
  
 Sie müssen einen anderen Namen für den Typparameter verwenden, da der Name des Typparameters nicht mit dem Namen des Typs oder der Methode identisch sein kann, der bzw. die den Typparameter enthält.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0694 generiert.  
  
```  
// CS0694.cs // compile with: /target:library class C<C> {}   // CS0694  
```  
  
## Beispiel  
 Neben der oben beschriebenen Situation mit einer generischen Klasse kann dieser Fehler auch bei einer Methode auftreten:  
  
```  
// CS0694_2.cs // compile with: /target:library class A { public void F<F>(F arg);   // CS0694 }  
```