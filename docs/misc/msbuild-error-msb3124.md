---
title: "MSBuild Error MSB3124 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsDuplicateExtensions"
helpviewer_keywords: 
  - "MSB3124"
ms.assetid: d8365103-aa9d-400e-9c24-0a43e2bfbd14
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3124
**MSB3124: Für die Erweiterung '\<Erweiterungsname\>' wurde bereits eine Dateizuordnung erstellt.'**  
  
 Dieser Fehler tritt auf, wenn eine doppelte Dateizuordnungserweiterung gefunden wird.  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)`extension`\-Attribute, die nicht eindeutig sind.  Die Erweiterungsattribute jedes aufgelisteten \<fileAssociation\>\-Elements müssen eindeutig sein.  
  
## Siehe auch  
 [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)