---
title: "Problembehandlung bei Ausnahmen: System.IdentityModel.Selectors.PolicyValidationException | Microsoft Docs"
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
  - "PolicyValidationException-Ausnahme"
  - "System.IdentityModel.Selectors.PolicyValidationException-Ausnahme"
ms.assetid: 510c7698-a12b-4bcb-a9d8-87c704b62ffa
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IdentityModel.Selectors.PolicyValidationException
Eine <xref:System.IdentityModel.Selectors.PolicyValidationException>\-Ausnahme wird ausgelöst, wenn die vom Empfänger angegebene Richtlinie nicht überprüft werden kann. Weitere Informationen zu Richtlinienanforderungen finden Sie unter [Technische Referenz für das Informationskarten\-Profil V1.0](http://go.microsoft.com/fwlink/?LinkID=102401).  
  
 Jeder ungültiger Richtlinieninhalt kann diesen Fehler verursachen. Häufige Probleme mit Richtlinieninhalten sind unter anderem:  
  
-   Ungültiger Schlüsseltyp  
  
-   Ungültige Schlüsselgröße  
  
-   Ungültiges XML\-Format.  
  
-   Richtlinie enthält keine Ansprüche \(wenigstens ein nicht optionaler Anspruch muss angegeben werden\)  
  
## Siehe auch  
 <xref:System.IdentityModel.Selectors.PolicyValidationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)