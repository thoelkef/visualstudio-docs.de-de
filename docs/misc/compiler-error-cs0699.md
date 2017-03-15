---
title: "Compilerfehler CS0699 | Microsoft Docs"
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
  - "CS0699"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0699"
ms.assetid: 1dff310b-6b8d-46b4-a649-bbf23282ff1f
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0699
Für 'generisch' ist der Typparameter 'bezeichner' nicht definiert  
  
 Ein Typparameter wurde in einer generischen Definition verwendet, der nicht in der Deklarationsliste der Typparameter für dieses Generikum gefunden wurde. Dazu kann es kommen, wenn der für den Typparameter verwendete Name inkonsistent ist.  
  
 Im folgenden Beispiel wird CS0699 generiert:  
  
```  
// CS0699.cs class C<T> where U : I   // CS0699 – U is not a valid type parameter { }  
```