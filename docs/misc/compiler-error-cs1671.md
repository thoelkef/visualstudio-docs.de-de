---
title: "Compilerfehler CS1671 | Microsoft Docs"
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
  - "CS1671"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1671"
ms.assetid: 34255d2b-6ff6-4ac1-b617-3199e16726cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1671
Eine Namespacedeklaration darf keine Modifizierer oder Attribute aufweisen.  
  
 Modifizierer haben bei Anwendung auf einen Namespace keine Aussagekraft, daher sind sie unzulässig.  
  
 Im folgenden Beispiel wird CS1671 generiert:  
  
```  
// CS1671.cs public namespace NS // CS1671 { }  
```