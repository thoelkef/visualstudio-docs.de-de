---
title: "Compilerfehler CS1732 | Microsoft Docs"
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
  - "CS1732"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1732"
ms.assetid: 72c7f7fc-d5f2-4538-9b02-50dda54d3b1e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1732
Parameter erwartet.  
  
 Dieser Fehler wird ausgelöst, wenn ein Lambdaausdruck ein Komma nach einem Eingabeparameter enthält, jedoch nicht der folgende Parameter angegeben wird.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie das Komma, oder fügen Sie den Eingabeparameter hinzu, den der Compiler nach dem Komma erwartet.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1732 generiert:  
  
```  
// cs1732.cs // compile with: /target:library class Test { delegate void D(int x, int y); static void Main() { D d = (x,) => { }; // CS1732 } }  
```