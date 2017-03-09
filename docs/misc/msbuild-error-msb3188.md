---
title: "MSBuild Error MSB3188 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PrerequisiteNotSigned"
helpviewer_keywords: 
  - "MSB3188"
ms.assetid: 8520e960-3b31-4e25-9fce-b9092b869bd0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3188
**MSB3188: Die \<Assemblyname\>\-Assembly muss mit einem starken Namen signiert sein, um als erforderliche Komponente markiert zu werden.**  
  
 Dieser Fehler wird generiert, wenn eine erforderliche Assembly nicht mit einem starken Namen signiert ist.  Er bezieht sich nur auf Anwendungsmanifeste.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass sämtliche vom Projekt verwendeten Assemblys mit einem starken Namen signiert sind.