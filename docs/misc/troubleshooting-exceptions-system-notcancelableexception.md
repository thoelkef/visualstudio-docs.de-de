---
title: "Problembehandlung bei Ausnahmen: System.NotCancelableException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NotCancelableException-Klasse"
ms.assetid: 36b82d4b-f075-4af5-993a-3e763a7e254a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.NotCancelableException
`NotCancelableException` wird bei dem Versuch ausgelöst, eine Operation abzubrechen, die nicht abgebrochen werden kann.  
  
## Tipps  
 Versuchen Sie nicht, die Operation abzubrechen.  
 Einige Operationen können nicht abgebrochen werden und lösen bei einem derartigen Versuch diese Ausnahme aus. Geben Sie in solchen Fällen dem Benutzer nicht die Möglichkeit, die Operation abzubrechen.  
  
## Siehe auch  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)