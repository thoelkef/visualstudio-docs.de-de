---
title: "Compilerwarnung (Stufe 1) CS1635 | Microsoft Docs"
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
  - "CS1635"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1635"
ms.assetid: e1795880-f7ea-4dca-b15b-4ba549d7ed78
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1635
Die Warnung 'warnungscode' kann nicht wiederhergestellt werden, da sie global deaktiviert wurde.  
  
 Diese Warnung tritt auf, wenn Sie die Befehlszeilenoption oder Projekteinstellung **\/nowarn** verwenden, um eine Warnung für die gesamte Kompilationseinheit zu deaktivieren, aber mithilfe von `#pragma warning restore` versuchen, die betreffende Warnung wiederherzustellen. Entfernen Sie zum Beheben dieses Fehlers entweder die Befehlszeilenoption oder Projekteinstellung „\/nowarn“, oder entfernen Sie das `#pragma warning restore` für alle Warnungen, die Sie mithilfe der Befehlszeile oder der Projekteinstellungen deaktivieren. Weitere Informationen finden Sie unter der [\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning).  
  
 Im folgenden Beispiel wird CS1635 generiert:  
  
```  
// CS1635.cs // compile with: /w:1 /nowarn:162 enum MyEnum {one=1,two=2,three=3}; class MyClass { public static void Main() { #pragma warning disable 162 if (MyEnum.three == MyEnum.two) System.Console.WriteLine("Duplicate"); #pragma warning restore 162 } }  
```