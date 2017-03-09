---
title: "Compilerfehler CS1948 | Microsoft Docs"
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
  - "CS1948"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1948"
ms.assetid: 3dac3abe-0edd-4ee1-8fb1-bc597ea63e1f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1948
Die Bereichsvariable "name" darf nicht denselben Namen wie der Typparameter einer Methode aufweisen  
  
 In einem Deklarationsabschnitt können nicht zwei Deklarationen mit demselben Bezeichner enthalten sein.  
  
### So beheben Sie diesen Fehler  
  
1.  Ändern Sie den Namen der Bereichsvariablen oder des Typparameters.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1948 erzeugt, da der Bezeichner `T` für die Bereichsvariable und für den Typparameter in der Methode `TestMethod` verwendet wird:  
  
```  
// cs1948.cs using System.Linq; class Test { public void TestMethod<T>(T t) { var x = from T in Enumerable.Range(1, 100) // CS1948 select T; } }  
```