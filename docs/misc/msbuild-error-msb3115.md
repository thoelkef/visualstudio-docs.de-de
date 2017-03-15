---
title: "MSBuild Error MSB3115 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidEntryPoint"
helpviewer_keywords: 
  - "MSB3115"
ms.assetid: 7d9d4156-fd6a-455a-8a3d-b191485f1294
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3115
**MSB3115: Die Datei "\<Datei\>" ist kein gültiger Einstiegspunkt.**  
  
 Dieser Fehler wird generiert, wenn ein Manifest einen ungültigen Einstiegspunkt angibt.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass in den Manifesten gültige Einstiegspunkte angegeben sind.  Für ein Anwendungsmanifest ist eine EXE\-Datei ein gültiger Einstiegspunkt.  Für ein Bereitstellungsmanifest ist ein Anwendungsmanifest ein gültiger Einstiegspunkt.