---
title: "MSBuild Error MSB3186 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoIdentity"
helpviewer_keywords: 
  - "MSB3186"
ms.assetid: 1219fef4-9114-401c-875b-1dc69697fd9f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3186
**MSB3186: Die Assemblyidentität für das generierte Manifest kann nicht aus Eingabeparametern für Aufgaben abgeleitet werden.**  
  
 Dieser Fehler wird generiert, wenn beim Buildprozess kein Assemblyname für das Anwendungs\- oder Bereitstellungsmanifest abgeleitet werden kann.  Der Assemblyname wird nicht explizit vergeben. Im Basismanifest ist keine Identität vorhanden, und es ist kein Einstiegspunktbezeichner angegeben.  
  
## Siehe auch  
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)