---
title: "Compilerfehler CS1024 | Microsoft Docs"
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
  - "CS1024"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1024"
ms.assetid: 41f587cb-1958-4eb6-9f8d-c03500e55e21
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1024
Präprozessordirektive erwartet.  
  
 Eine Zeile beginnt mit dem Nummernzeichen \(\#\), aber die nachfolgende Zeichenfolge war keine gültige [Präprozessordirektive](/dotnet/csharp/language-reference/preprocessor-directives/index).  
  
 Im folgenden Beispiel wird CS1024 generiert:  
  
```  
// CS1024.cs #import System   // CS1024  
```