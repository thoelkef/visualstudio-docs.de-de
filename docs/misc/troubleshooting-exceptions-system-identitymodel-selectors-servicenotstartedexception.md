---
title: "Problembehandlung bei Ausnahmen: System.IdentityModel.Selectors.ServiceNotStartedException | Microsoft Docs"
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
  - "System.IdentityModel.Selectors.ServiceNotStartedException-Ausnahme"
  - "ServiceNotStartedException-Ausnahme"
ms.assetid: 6d34bab2-994a-4b0c-893d-19b5d7acf92d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IdentityModel.Selectors.ServiceNotStartedException
Eine <xref:System.IdentityModel.Selectors.ServiceNotStartedException>\-Ausnahme wird ausgelöst, wenn CardSpace nicht auf dem Computer des Benutzers gestartet wurde. Wurde versucht, CardSpace zu starten, konnte der Start aus irgendeinem Grund jedoch nicht ausgeführt werden, wird diese Ausnahme ausgelöst.  
  
 Überprüfen Sie, dass der CardSpace\-Dienst installiert und auf dem Computer aktiviert ist. Versuchen Sie, den CardSpace\-Dienst manuell mit Microsoft Management Console \(MMC\) zu starten.  
  
 CardSpace Version 1 unterstützt keine FAT\-Dateisysteme. Unter FAT\-Systemen wird CardSpace nicht gestartet, und diese Ausnahme tritt auf.  
  
## Siehe auch  
 <xref:System.IdentityModel.Selectors.ServiceNotStartedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)