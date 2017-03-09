---
title: "Compilerwarnung (Stufe 3) CS0693 | Microsoft Docs"
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
  - "CS0693"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0693"
ms.assetid: a3902336-49db-4808-b41f-8f0936bff53a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 3) CS0693
Der Typparameter "Typparameter" hat denselben Namen wie der Typparameter des äußeren Typs "Typ".  
  
 Dieser Fehler tritt bei einem generischen Member, z. B. einer Methode in einer generischen Klasse, auf. Da der Typparameter der Methode nicht notwendigerweise mit dem Typparameter der Klasse übereinstimmt, können Sie ihm nicht den gleichen Namen geben. Weitere Informationen finden Sie unter [Generische Methoden](/dotnet/csharp/programming-guide/generics/generic-methods).  
  
 Um diese Situation zu vermeiden, verwenden Sie für einen der Typparameter einen anderen Namen.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0693 generiert.  
  
```  
// CS0693.cs // compile with: /W:3 /target:library class Outer<T> { class Inner<T> {}   // CS0693 // try the following line instead // class Inner<U> {} }  
```