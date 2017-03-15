---
title: "Compilerwarnung (Stufe 1) CS0824 | Microsoft Docs"
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
  - "CS0824"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0824"
ms.assetid: ad643bb7-51b2-455b-a9f3-2bd4588d2c5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS0824
Der Konstruktor 'name' ist als extern markiert  
  
 Ein Konstruktor kann als extern gekennzeichnet werden. Der Compiler kann dann jedoch nicht überprüfen, ob der Konstruktor tatsächlich vorhanden ist. Daher wird eine Warnung generiert.  
  
### So entfernen Sie die Warnung  
  
1.  Verwenden Sie eine Pragma\-Warnungsdirektive, um sie zu ignorieren.  
  
2.  Verlagern Sie den Konstruktor in den Typ.  
  
## Beispiel  
 Mit dem folgenden Code wird CS0824 generiert:  
  
```  
// cs0824.cs public class C { extern C(); // CS0824 public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [extern](/dotnet/csharp/language-reference/keywords/extern)   
 [\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)