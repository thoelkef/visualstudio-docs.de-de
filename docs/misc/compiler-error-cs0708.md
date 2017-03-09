---
title: "Compilerfehler CS0708 | Microsoft Docs"
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
  - "CS0708"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0708"
ms.assetid: 19e1907f-b78c-4c8b-b78c-eedfd57115f2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0708
"Feld": Instanzmember können nicht in einer statischen Klasse deklariert werden.  
  
 Dieser Fehler tritt auf, wenn Sie einen nicht statischen Member in einer Klasse deklarieren, die als statisch deklariert ist. Es ist nicht möglich, Instanzen von statischen Klassen zu erstellen, sodass Instanzvariablen nicht sinnvoll wären. Das **static**\-Schlüsselwort muss auf alle Member von statischen Klassen angewendet werden.  
  
 Im folgenden Beispiel wird CS0708 generiert:  
  
```  
// CS0708.cs // compile with: /target:library public static class C { int i;  // CS0708 static int j;  // OK }  
```