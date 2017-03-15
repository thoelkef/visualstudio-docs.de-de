---
title: "MSBuild Error MSB3125 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsNoEntryPoint"
helpviewer_keywords: 
  - "MSB3125"
ms.assetid: f8a08b05-1946-4788-8577-ceefde785e95
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3125
**MSB3125: Die Anwendung verwendet Dateizuordnungen, verfügt aber nicht über einen EntryPoint\-Buildparameter.**  
  
 Dieser Fehler tritt auf, wenn kein entryPoint\-Buildparameter vorhanden ist.  Wenn Sie eine Anwendung für die Verwendung von Dateizuordnungen konfigurieren, muss ein entryPoint\-Buildparameter im Anwendungsmanifest enthalten sein.  Das \<entryPoint\>\-Element identifiziert die Assembly, die ausgeführt werden sollte, wenn die Anwendung ausgeführt wird.  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie das [\<entryPoint\> Element](../deployment/entrypoint-element-clickonce-application.md) auf einen gültigen Wert fest.  Weitere Informationen hierzu finden Sie unter [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
## Siehe auch  
 [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)