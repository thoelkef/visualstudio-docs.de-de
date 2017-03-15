---
title: "Compilerwarnung (Stufe 2) CS1927 | Microsoft Docs"
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
  - "CS1927"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1927"
ms.assetid: 32b4e58f-668c-4596-9529-7f3a293ff4ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS1927
"\/win32manifest" gilt nur für Assemblys und wird für das Modul ignoriert.  
  
 Ein win32\-Manifest wird nur auf Assemblyebene angewendet. Das Modul wird kompiliert, verfügt jedoch über kein Manifest.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die **\/win32manifest option**.  
  
2.  Kompilieren Sie den Code als Assembly.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1927 generiert. Dies gilt sowohl für die Compileroption **\/target:module** als auch für die Compileroption **\/win32manifest**.  
  
```  
// cs1927.cs // Compile with: /target:module /win32manifest using System; class ManifestWithModule { static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [\/win32manifest \(Import a Custom Win32 Manifest File\)](/dotnet/csharp/language-reference/compiler-options/win32manifest-compiler-option)   
 [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)