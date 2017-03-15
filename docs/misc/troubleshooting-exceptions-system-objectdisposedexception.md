---
title: "Problembehandlung bei Ausnahmen: System.ObjectDisposedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ObjectDisposedException-Klasse, Problembehandlung"
ms.assetid: 702912b6-e927-4f8e-8b7c-2e1880312b0e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.ObjectDisposedException
Eine <xref:System.ObjectDisposedException>\-Ausnahme wird ausgelöst, wenn versucht wird, eine Operation an einem verworfenen Objekt auszuführen, z. B. ein geschlossener Stream oder ein geschlossener Registrierungsschlüssel.  
  
## Tipps  
 **Stellen Sie sicher, dass keine Ressource vor ihrer Verwendung freigegeben wurde.**  
 Wenn Sie beispielsweise einen Stream bearbeiten möchten, stellen Sie sicher, dass er vorher nicht geschlossen worden ist.  
  
## Siehe auch  
 <xref:System.ObjectDisposedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)