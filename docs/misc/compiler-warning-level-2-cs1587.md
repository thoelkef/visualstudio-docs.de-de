---
title: "Compilerwarnung (Stufe 2) CS1587 | Microsoft Docs"
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
  - "CS1587"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1587"
ms.assetid: b27c2009-d485-43fd-a649-fbc15570d256
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS1587
Der XML\-Kommentar ist auf keinem gültigen Sprachelement abgelegt.  
  
 Empfohlene Tags für Dokumentationskommentare sind nicht für alle Sprachelemente zulässig. Tags sind z. B. für Namespaces nicht zulässig. Weitere Informationen zu XML\-Kommentaren finden Sie unter [Empfohlene Tags für Dokumentationskommentare](/dotnet/csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments).  
  
## Beispiel  
 Im folgenden Beispiel wird CS1587 generiert:  
  
```  
// CS1587.cs // compile with: /W:2 /doc:x.xml /// <summary>test</summary>   // CS1587, tag not allowed on namespace namespace MySpace { class MyClass { public static void Main() { } } }  
```