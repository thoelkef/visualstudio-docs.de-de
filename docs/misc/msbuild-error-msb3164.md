---
title: "MSBuild Error MSB3164 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageHomeSiteMissing"
helpviewer_keywords: 
  - "MSB3164"
ms.assetid: 5a1e31fc-0322-4d4e-8c26-013b1efb82c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3164
**MSB3164: Für \<Paket\> wurde kein HomeSite\-Attribut angegeben. Aus diesem Grund wird das Paket im gleichen Pfad wie der Bootstrapper veröffentlicht.**  
  
 Diese Warnung wird generiert, wenn der Benutzer HomeSite verwenden möchte, die entsprechenden HomeSite\-Informationen für das angegebene Paket jedoch nicht verfügbar sind.  
  
### So beheben Sie diesen Fehler  
  
-   Aktualisieren Sie das Manifest, sodass die HomeSite\-Informationen eingeschlossen werden.  
  
-   Verzichten Sie andernfalls auf die Verwendung von HomeSite.  
  
## Siehe auch  
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)