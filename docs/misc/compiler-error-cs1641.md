---
title: "Compilerfehler CS1641 | Microsoft Docs"
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
  - "CS1641"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1641"
ms.assetid: ba6eab47-c28b-4531-b6a0-6d538b236d19
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1641
Bei einem Pufferfeld fester Größe muss sich der Arraygrößenspezifizierer hinter dem Feldnamen befinden.  
  
 Im Gegensatz zu regulären Arrays benötigen Puffer mit fester Größe eine konstante Größe, die am Deklarationspunkt angegeben werden muss. Fügen Sie ein positives Integer\-Literal oder eine konstante positive Ganzzahl hinzu, und fügen Sie die rechteckigen Klammern hinter dem Bezeichner ein, um diesen Fehler zu beheben.  
  
 Im folgenden Beispiel wird CS1641 generiert:  
  
```  
// CS1641.cs // compile with: /unsafe /target:library unsafe struct S { fixed int [] a;  // CS1641 // OK fixed int b [10]; const int c = 10; fixed int d [c]; }  
```