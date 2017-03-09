---
title: "MSBuild Error MSB3481 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertNotInStore"
helpviewer_keywords: 
  - "MSB3481"
ms.assetid: 55f99775-3bd5-4e1b-b184-c6405d75e8ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3481
**MSB3481: Das Signaturzertifikat konnte nicht gefunden werden.  Vergewissern Sie sich, dass es sich im privaten Speicher des derzeitigen Benutzers befindet.**  
  
 Dieser Fehler wird generiert, wenn das Signaturzertifikat nicht im persönlichen Zertifikatspeicher gefunden wurde.  Dieser Fehler ähnelt [MSBuild Error MSB3486](../misc/msbuild-error-msb3486.md), d. h., dass das Zertifikat gefunden wurde, jedoch nicht übereinstimmt.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass sich in Ihrem persönlichen Zertifikatspeicher ein gültiges Zertifikat befindet, das der PFX\-Datei des Projekts entspricht.  
  
## Siehe auch  
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)