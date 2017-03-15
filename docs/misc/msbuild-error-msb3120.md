---
title: "MSBuild Error MSB3120 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionTooLong"
helpviewer_keywords: 
  - "MSB3120"
ms.assetid: 20bc64f5-aadc-4eec-9915-a87a3d7f81ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3120
**MSB3120: Dateizuordnungserweiterung '\<Erweiterung \>' überschreitet die maximale zulässige Länge \<maximale Länge\>.**  
  
 Die Anzahl der Zeichen in der Dateizuordnungserweiterung darf die angegebene Zahl nicht überschreiten.  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie das [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md) `extension`\-Attribut auf einen Wert fest, der nicht mehr Zeichen enthält als der zulässige Grenzwert für das Zielbetriebssystem.  
  
## Siehe auch  
 [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)