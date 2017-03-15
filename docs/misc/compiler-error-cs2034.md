---
title: "Compilerfehler CS2034 | Microsoft Docs"
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
  - "CS2034"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2034"
ms.assetid: 72f2b785-ee23-4a1b-b12d-42d19c324d5e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS2034
Eine \/reference\-Option, die einen externen Alias deklariert, kann nur einen Dateinamen haben. Um mehrere Aliase oder Dateinamen festzulegen, verwenden Sie mehrere \/reference\-Optionen.  
  
 Um zwei Aliase und\/oder Dateinamen anzugeben, verwenden Sie zwei **\/reference**\-Optionen wie folgt:  
  
## Beispiel  
 Im folgenden Code wird Fehler CS2034 generiert.  
  
```  
// CS2034.cs // compile with: /r:A1=cs2034a1.dll;A2=cs2034a2.dll // to fix, compile with: /r:A1=cs2034a1.dll /r:A2=cs2034a2.dll // CS2034 extern alias A1; extern alias A2; using System;  
```