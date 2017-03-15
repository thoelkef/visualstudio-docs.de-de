---
title: "Compilerfehler CS1537 | Microsoft Docs"
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
  - "CS1537"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1537"
ms.assetid: fdc17f3e-05b3-4d04-8825-4563aec816f5
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1537
Der using\-Alias 'Alias' ist bereits vorher in diesem Namespace aufgetreten.  
  
 Sie haben ein Symbol zweimal als Alias für einen Namespace definiert. Ein Symbol kann nur einmal definiert werden.  
  
 Im folgenden Beispiel wird CS1537 generiert:  
  
```  
// CS1537.cs namespace x { using System; using Object = System.Object; using Object = System.Object;   // CS1537, delete this line to resolve using System = System; }  
```