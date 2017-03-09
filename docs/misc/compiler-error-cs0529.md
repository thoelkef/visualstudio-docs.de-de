---
title: "Compilerfehler CS0529 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0529"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0529"
ms.assetid: 61de8086-f991-455c-b009-bb8cd05f34bd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0529
Die geerbte Schnittstelle 'Schnittstelle1' verursacht eine Schleife in der Schnittstellenhierarchie von 'Schnittstelle2'.  
  
 Die Vererbungsliste für eine [Schnittstelle](/dotnet/csharp/language-reference/keywords/interface) enthält einen direkten oder indirekten Verweis auf sich selbst. Eine Schnittstelle kann nicht von sich selbst erben.  
  
 Im folgenden Beispiel wird CS0529 generiert:  
  
```  
// CS0529.cs namespace x { public interface a { } public interface b : a, c { } public interface c : b   // CS0529, b inherits from c { } }  
```