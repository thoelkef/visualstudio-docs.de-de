---
title: "MSBuild Error MSB3146 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.MissingDependency"
helpviewer_keywords: 
  - "MSB3146"
ms.assetid: 717fd649-3024-427d-a068-cff8034ffc0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3146
**MSB3146: Das \<Paket\>\-Element ist für \<Paket\> erforderlich, war jedoch nicht enthalten.**  
  
 Dieser Fehler tritt auf, wenn ein Bootstrapperpaket von einem anderen abhängt, jedoch nur das abhängige Paket installiert wurde.  Dies wäre z. B. der Fall, wenn Paket B von Paket A abhängt, jedoch nur Paket B installiert ist.  
  
### So beheben Sie diesen Fehler  
  
-   Installieren Sie das erforderliche Paket.