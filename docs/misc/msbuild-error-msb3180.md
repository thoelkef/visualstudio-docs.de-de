---
title: "MSBuild Error MSB3180 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateComDefinition"
helpviewer_keywords: 
  - "MSB3180"
ms.assetid: 98d8cb76-6176-4121-82ee-8a297d9deebc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3180
**MSB3180: Die COM\-Komponente \<Assembly\> ist sowohl in \<Datei\> als auch in \<Datei\>, clsid\/tlbid\="'\<assembly\>'" angegeben.**  
  
 Dieser Fehler wird bei der Erstellung des Anwendungsmanifests generiert, wenn in Dateiverweisen oder abhängigen Manifesten doppelte COM\-Verweise \(auf Klassen oder Typbibliotheken\) gefunden werden.  
  
 Beispielsweise könnte dieser Fehler angezeigt werden, wenn Sie einen Verweis auf ein COM\-Objekt mit einem externen Manifest und einen Verweis auf das gleiche COM\-Objekt mit einem internen Manifest hinzufügen.  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie einen der doppelten COM\-Verweise.  
  
## Siehe auch  
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)