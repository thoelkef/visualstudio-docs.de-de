---
title: "MSBuild Error MSB3182 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.TargetPathTooLong"
helpviewer_keywords: 
  - "MSB3182"
ms.assetid: b257a206-b12b-453b-97d8-2cb9a0d3dcc9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3182
**MSB3182: Der Dateiname \<Dateiname\> ist länger als \<Zeichenanzahl\> Zeichen.**  
  
 Diese Warnung wird generiert, wenn der Wert der `TargetPath`\-Eigenschaft zu lang ist.  Er kann sich sowohl auf das Anwendungs\- als auch auf das Bereitstellungsmanifest beziehen.  
  
### So beheben Sie diesen Fehler  
  
-   Kürzen Sie den Wert der `TargetPath`\-Eigenschaft.  
  
## Siehe auch  
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)