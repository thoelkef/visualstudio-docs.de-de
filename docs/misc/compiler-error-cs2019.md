---
title: "Compilerfehler CS2019 | Microsoft Docs"
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
  - "CS2019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2019"
ms.assetid: eafd2531-8b3a-499c-9e12-a605a011396f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS2019
Ungültiger Zieltyp für \/target: Sie müssen "exe", "winexe", "library", oder "module" angeben.  
  
 Die [\/target](/dotnet/csharp/language-reference/compiler-options/target-compiler-option)\-Compileroption wurde verwendet, aber es wurde ein ungültiger Parameter übergeben. Kompilieren Sie das Programm mithilfe der Form der **\/target**\-Option neu, die für die Ausgabedatei geeignet ist, um diesen Fehler zu beheben.  
  
 Im folgenden Beispiel wird CS2017 generiert:  
  
```  
// CS2019.cs // compile with: /target:libra // CS2019 expected class MyClass { }  
```