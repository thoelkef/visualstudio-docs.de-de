---
title: "Compilerfehler CS1022 | Microsoft Docs"
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
  - "CS1022"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1022"
ms.assetid: 76b9f32b-2ebf-471d-a635-852daf8877d7
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1022
Typ\- oder Namespacedefinition oder Dateiende erwartet.  
  
 Eine Quellcodedatei weist kein übereinstimmendes Paar geschweifter Klammern auf.  
  
 Im folgenden Beispiel wird CS1022 generiert:  
  
```  
// CS1022.cs namespace x { } }   // CS1022  
```