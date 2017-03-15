---
title: "Compilerfehler CS1689 | Microsoft Docs"
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
  - "CS1689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1689"
ms.assetid: 5fa6e845-40ef-4451-81ee-acbe2665527a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1689
Das 'Attributname'\-Attribut ist nur für Methoden oder Attributklassen gültig.  
  
 Dieser Fehler tritt nur beim **ConditionalAttribute**\-Attribut auf. Wie die Meldung besagt, kann dieses Attribut nur für Methoden oder Attributklassen verwendet werden. Wenn Sie z. B. versuchen, dieses Attribut auf eine Klasse anzuwenden, wird dieser Fehler wird generiert.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1689 generiert:  
  
```  
// CS1689.cs // compile with: /target:library [System.Diagnostics.Conditional("A")]   // CS1689 class MyClass {}  
```