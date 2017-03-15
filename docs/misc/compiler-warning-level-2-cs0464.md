---
title: "Compilerwarnung (Stufe 2) CS0464 | Microsoft Docs"
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
  - "CS0464"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0464"
ms.assetid: 3dff97d4-e1f6-4a71-91e2-68cffc38d49a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0464
Beim Vergleich mit NULL vom Typ "type" wird immer "False" zurückgegeben  
  
 Diese Warnung wird erzeugt, wenn Sie einen Vergleich zwischen einer Variablen, die NULL\-Werte zulässt, und Null durchführen, und der Vergleich nicht `==` oder `!=` ist. Um diesen Fehler zu beheben, stellen Sie sicher, dass Sie wirklich einen Wert für `null` überprüfen möchten. Ein Vergleich wie `i == null` kann "true" oder "false" sein. Ein Vergleich wie `i > null` ist immer "false".  
  
## Beispiel  
 Im folgenden Beispiel wird CS0464 generiert.  
  
```  
// CS0464.cs class MyClass { public static void Main() { int? i = 0; if (i < null) ;   // CS0464 i++; } }  
```