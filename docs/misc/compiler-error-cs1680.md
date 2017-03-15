---
title: "Compilerfehler CS1680 | Microsoft Docs"
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
  - "CS1680"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1680"
ms.assetid: 973da155-e6fa-4de8-94fd-7838f839a81f
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1680
Ungültige Verweisaliasoption: "Alias" \-\- fehlender Dateiname  
  
 Dieser Fehler tritt auf, wenn Sie das `alias`\-Feature mit der **\/reference**\-Compileroption verwenden, ohne einen gültigen Dateinamen anzugeben.  
  
 Im folgenden Beispiel wird CS1680 generiert.  
  
```  
// CS1680.cs // compile with: /reference:alias= // CS1680 expected // To resolve, specify the name of a file with an assembly manifest class MyClass {}  
  
```