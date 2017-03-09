---
title: "Compilerfehler CS0574 | Microsoft Docs"
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
  - "CS0574"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0574"
ms.assetid: 43684abe-982c-45ae-9d0b-4fe031671fc8
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0574
Der Name des Destruktors muss mit dem Namen der Klasse übereinstimmen.  
  
 Der Name eines Destruktors muss der Klassenname mit einer vorangestelltenTilde \(~\) sein.  
  
 Im folgenden Beispiel wird CS0574 generiert:  
  
```  
// CS0574.cs namespace x { public class iii { ~iiii()   // CS0574 { } public static void Main() { } } }  
```