---
title: "Compilerfehler CS0441 | Microsoft Docs"
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
  - "CS0441"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0441"
ms.assetid: 3f07500a-d479-424c-a0f4-c219be1b5a45
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0441
"class": Eine Klasse kann nicht gleichzeitig statisch und versiegelt sein  
  
 Dieser Fehler tritt auf, wenn Sie eine Klasse deklarieren, die gleichzeitig statisch und versiegelt ist. Statische Klassen sind grundsätzlich versiegelt, d. h., der versiegelte Modifizierer ist nicht erforderlich. Verwenden Sie nur einen Modifizierer, um den Fehler zu beheben.  
  
 Im folgenden Beispiel wird der Fehler CS0441 generiert:  
  
```  
// CS0441.cs sealed static class MyClass { }   // CS0441  
```