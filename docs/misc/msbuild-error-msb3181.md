---
title: "MSBuild Error MSB3181 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.DuplicateTargetPath"
helpviewer_keywords: 
  - "MSB3181"
ms.assetid: 49349fc2-3fa1-470d-a5cb-6ad72b93f408
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3181
**MSB3181: Zwei oder mehr Dateien haben den gleichen Zielpfad \<Pfad\>.**  
  
 Diese Warnung wird bei der Anwendungsmanifesterstellung generiert, wenn mindestens zwei Assemblys oder Dateien, auf die verwiesen wird, den gleichen Zielpfad aufweisen.  Der Pfad enthält auch den Dateinamen, und diese Assemblys würden einander zur Bereitstellungszeit überschreiben.  
  
## Siehe auch  
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)