---
title: "Compilerfehler CS0734 | Microsoft Docs"
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
  - "CS0734"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0734"
ms.assetid: 9e1b0e49-bfc3-400c-9fd1-37e3c827e656
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0734
Die Option \/moduleassemblyname kann nur beim Erstellen des Zieltyps "module" angegeben werden.  
  
 Die Compileroption **\/moduleassemblyname** sollte nur beim Erstellen eines .netmodule verwendet werden. Weitere Informationen finden Sie unter [\/moduleassemblyname \(Specify Friend Assembly for Module\)](/dotnet/csharp/language-reference/compiler-options/moduleassemblyname-compiler-option).  
  
 Weitere Informationen zum Erstellen eines .netmodule finden Sie unter [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0734 generiert. Fügen Sie der Kompilierung **\/target:module** hinzu, um den Fehler zu beheben.  
  
```  
// CS0734.cs // compile with: /moduleassemblyname:A // CS0734 expected public class Test {}  
```