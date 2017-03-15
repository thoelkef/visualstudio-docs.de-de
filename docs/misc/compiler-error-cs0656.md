---
title: "Compilerfehler CS0656 | Microsoft Docs"
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
  - "CS0656"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0656"
ms.assetid: e695280a-e75d-4e8c-aec2-1f3fb455544a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0656
Der vom Compiler angeforderte Member 'Objekt.Member' fehlt.  
  
 Eines der folgenden Probleme ist aufgetreten:  
  
-   Die Installation der Common Language Runtime ist beschädigt.  
  
-   Sie verfügen über einen Verweis auf eine Assembly, die einen Typ definiert, der sich auch in der Common Language Runtime befindet. Der Typ der Assembly ist jedoch nicht so definiert, wie es vom C\#\-Compiler erwartet wird.  
  
 Überprüfen Sie die Verweise, um sicherzustellen, dass Sie die richtige Version der Common Language Runtime verwenden.