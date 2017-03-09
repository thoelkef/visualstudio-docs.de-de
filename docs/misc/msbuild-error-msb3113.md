---
title: "MSBuild Error MSB3113 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ResolveFailedInReadWriteMode"
helpviewer_keywords: 
  - "MSB3113"
ms.assetid: 81e73738-e6ee-4651-9f48-acb1feef3ff5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3113
**MSB3113: Die Datei \<Datei\> konnte nicht gefunden werden.**  
  
 Dieser Fehler wird generiert, wenn beim Erstellen eines neuen Manifests ein Verweis vorgefunden wird, der nicht aufgelöst werden kann.  Dieser kann aus der Projektdatei stammen oder ein Aufgabenparameter sein.  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie die Projektdatei \(und bei einer benutzerdefinierten Erstellung auch die Buildparameter\) auf Dateiverweiskonflikte.  
  
## Siehe auch  
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)