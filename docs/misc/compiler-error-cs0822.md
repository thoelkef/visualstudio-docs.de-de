---
title: "Compilerfehler CS0822 | Microsoft Docs"
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
  - "CS0822"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0822"
ms.assetid: 519091be-2332-4df4-acd9-e3b633966b3d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0822
Implizit typisierte lokale Variablen dürfen nicht konstant sein  
  
 Implizit typisierte lokale Variablen sind nur notwendig, um anonyme Typen zu speichern. In allen anderen Fällen sind sie nur ein bequemes Mittel. Wenn sich der Wert der Variablen niemals ändert, sollten Sie ihr einen expliziten Typ zuweisen. Bei dem Versuch, den `readonly`\-Modifizierer mit einer implizit typisierten lokalen Variablen zu verwenden, wird CS0106 generiert.  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn Sie die Variable so benötigen, dass sie konstant oder `readonly` ist, weisen Sie ihr einen expliziten Typ zu.  
  
## Beispiel  
 Mit dem folgenden Code wird der Fehler CS0822 generiert:  
  
```  
// cs0822.cs class A { public static int Main() { const var x = 0; // CS0822.cs return -1; } }  
```  
  
## Siehe auch  
 [Implizit typisierte lokale Variablen](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)