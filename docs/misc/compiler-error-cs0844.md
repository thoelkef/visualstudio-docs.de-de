---
title: "Compilerfehler CS0844 | Microsoft Docs"
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
  - "CS0844"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0844"
ms.assetid: ccf74e01-292a-42d0-897c-8add7aee2118
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0844
Die lokale Variable "Name" kann erst verwendet werden, nachdem sie deklariert wurde. In der Deklaration der lokalen Variablen ist das Feld "Name" verborgen.  
  
 Ein Bezeichner kann in einem bestimmten Block nur eine Bedeutung haben. Lokale Variablen, die den gleichen Namen wie Klassenfelder haben, können das Feld verbergen, indem sie eine zweite Bedeutung für den Bezeichner einführen. Aus diesem Grund generiert der Compiler beim Verweisen auf ein Klassenfeld in einer Methode einen Fehler und deklariert dann eine lokale Variable mit demselben Namen.  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie `this.num`, um auf das Klassenfeld zu verweisen.  
  
-   Geben Sie der lokalen Variable einen anderen Namen als dem Klassenfeld.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS0844 ausgelöst:  
  
```  
class Test { int num; public void TestMethod() { num = 5; // CS0844 int num = 6;        } public static int Main() { return 1; } }  
```