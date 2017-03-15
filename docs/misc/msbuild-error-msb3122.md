---
title: "MSBuild Error MSB3122 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsApplicationNotFullTrust"
helpviewer_keywords: 
  - "MSB3122"
ms.assetid: 523e4160-f165-437a-9f19-fb2ec77d46f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3122
**MSB3122: Verwendung von Dateizuordnungen erfordert volle Vertrauenswürdigkeit.**  
  
 Für die Veröffentlichung einer Anwendung, die Dateizuordnungen konfiguriert, ist es erforderlich, dass die Anwendung eine voll vertrauenswürdige Anwendung ist.  
  
### So beheben Sie diesen Fehler  
  
-   Aktivieren Sie ClickOnce\-Sicherheitseinstellungen, und legen Sie die Anwendung als voll vertrauenswürdige Anwendung fest.  Weitere Informationen finden Sie unter [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md).  
  
## Siehe auch  
 [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [Codezugriffssicherheit für ClickOnce\-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)