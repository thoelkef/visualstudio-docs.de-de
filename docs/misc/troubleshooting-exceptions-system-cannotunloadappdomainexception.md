---
title: "Problembehandlung bei Ausnahmen: System.CannotUnloadAppDomainException | Microsoft Docs"
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
  - "CannotUnloadAppDomainException-Klasse"
ms.assetid: eeee07c3-fdbc-4c91-859b-a419d23be9ba
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.CannotUnloadAppDomainException
Eine <xref:System.CannotUnloadAppDomainException>\-Ausnahme wird ausgelöst, wenn versucht wird, eine der folgenden Domänen zu entladen:  
  
-   die Standardanwendungsdomäne, die während der gesamten Lebensdauer der Anwendung geladen bleiben muss  
  
-   eine Anwendungsdomäne mit einem laufenden Thread, dessen Ausführung nicht sofort angehalten werden kann  
  
-   eine Anwendungsdomäne, die bereits entladen worden ist  
  
## Tipps  
 **Stellen Sie sicher, dass die Anwendungsdomäne, die Sie entladen möchten, nicht die Standardanwendungsdomäne ist, nicht über einen laufenden Thread verfügt oder nicht schon entladen wurde.**  
 Die Ausnahme wird ausgelöst, sofern eine dieser Bedingungen erfüllt ist. Weitere Informationen finden Sie unter <xref:System.AppDomain.Unload%2A>.  
  
## Siehe auch  
 <xref:System.CannotUnloadAppDomainException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)