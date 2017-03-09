---
title: "MSBuild Error MSB3184 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidInputManifest"
helpviewer_keywords: 
  - "MSB3184"
ms.assetid: 2be9f8e9-04ee-4299-b79f-965ee57a1a34
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3184
**MSB3184: Das Eingabemanifest ist ungültig.**  
  
 Dieser Fehler wird generiert, wenn der Buildprozess eine Datei lädt, von der er erwartet, dass sie entweder ein Anwendungs\- oder ein Bereitstellungsmanifest enthält, diese Datei jedoch etwas anderes enthält \(z. B. ein anderes Manifest oder beschädigte Daten\).  
  
### So beheben Sie diesen Fehler  
  
-   Vergewissern Sie sich, dass das Projekt die richtigen Manifeste enthält und diese gültig sind.  
  
## Siehe auch  
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)