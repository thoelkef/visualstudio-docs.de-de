---
title: "Compilerwarnung (Stufe 2) CS1711 | Microsoft Docs"
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
  - "CS1711"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1711"
ms.assetid: 0021275a-43eb-4295-929e-bb3283577a11
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS1711
Der XML\-Kommentar für "Typ" enthält ein typeparam\-Tag für "Parameter", es gibt aber keinen Typparameter mit diesem Namen.  
  
 Die Dokumentation eines generischen Typs enthält ein Tag für den Typparameter, der den falschen Namen aufweist.  
  
## Beispiel  
 Der folgende Code generiert die Warnung CS1711.  
  
```  
// cs1711.cs // compile with: /doc:cs1711.xml // CS1711 expected using System; ///<typeparam name="WrongName">can be an int</typeparam> class CMain { public static void Main() { } }  
```