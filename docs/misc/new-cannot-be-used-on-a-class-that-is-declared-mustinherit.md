---
title: "&#39;New&#39; darf nicht f&#252;r eine Klasse verwendet werden, die als &#39;MustInherit&#39; deklariert ist. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30569"
  - "bc30569"
helpviewer_keywords: 
  - "BC30569"
ms.assetid: 94c9e6a3-6489-4d58-b7e5-7b4203677e3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; darf nicht f&#252;r eine Klasse verwendet werden, die als &#39;MustInherit&#39; deklariert ist.
Eine `MustInherit`\-Klasse kann nicht direkt instanziiert werden, und daher kann der Operator `New` nicht für eine `MustInherit`\-Klasse verwendet werden. Es ist zwar möglich, Variablen und Werte zu verwenden, deren Typen zur Kompilierungszeit `MustInherit` sind, doch handelt es sich bei diesen Variablen und Werten entweder um Nullwerte oder um Verweise auf Instanzen von regulären Klassen, die aus den `MustInherit`\-Typen abgeleitet sind.  
  
 **Fehler\-ID:** BC30569  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den `New`\-Operator.  
  
## Siehe auch  
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)