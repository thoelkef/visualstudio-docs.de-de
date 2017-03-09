---
title: "MSBuild Error MSB3119 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionMissingLeadDot"
helpviewer_keywords: 
  - "MSB3119"
ms.assetid: 52d68b0e-01d4-436f-a96c-733fd20a8c04
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3119
**MSB3119: Dateizuordnungserweiterungen müssen mit einem Punktzeichen \(.\) beginnen.**  
  
 Dieser Fehler tritt auf, wenn Sie eine Dateizuordnung konfigurieren und die Erweiterung nicht mit einem Punktzeichen \(.\) beginnt.  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie das [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md) `extension`\-Attribut auf einen Wert fest, der mit einem Punktzeichen \(.\) beginnt, z. B. ".doc".  
  
## Siehe auch  
 [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)