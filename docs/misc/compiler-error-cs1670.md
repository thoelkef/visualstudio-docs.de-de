---
title: "Compilerfehler CS1670 | Microsoft Docs"
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
  - "CS1670"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1670"
ms.assetid: ee2507e5-b509-4af3-a15e-2c1f2da7159c
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1670
"params" ist in diesem Kontext nicht gültig.  
  
 Eine Reihe von C\#\-Features sind inkompatibel mit variablen Argumentlisten und erlauben das `params```\-Schlüsselwort nicht, einschließlich der Folgenden:  
  
-   Parameterlisten mit anonymen Methoden  
  
-   Überladene Operatoren  
  
## Beispiel  
 Im folgenden Beispiel wird CS1670 generiert:  
  
```  
// CS1670.cs public class C { public bool operator +(params int[] paramsList)  // CS1670 { return false; } static void Main() { } }  
```