---
title: "Problembehandlung bei Ausnahmen: System.Reflection.TargetException | Microsoft Docs"
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
  - "System.Reflection.TargetException-Ausnahme"
  - "TargetException-Ausnahme"
ms.assetid: 88b8e4b4-f1a3-4c4a-b1ef-cac176160803
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Reflection.TargetException
Diese Ausnahme wird ausgelöst, wenn versucht wird, ein ungültiges Ziel aufzurufen.  
  
## Hinweise  
 Eine <xref:System.Reflection.TargetException> wird ausgelöst, wenn versucht wird, eine nicht statische Methode auf einem NULL\-Objekt aufzurufen. Der Grund kann z. B. darin bestehen, dass der Aufrufer keinen Zugriff auf den Member hat oder dass der Member nicht durch das Ziel definiert wird.  
  
## Siehe auch  
 <xref:System.Reflection.TargetException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)