---
title: "MSBuild Error MSB3153 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageValidation"
helpviewer_keywords: 
  - "MSB3153"
ms.assetid: 937bb1ff-79f7-45a5-a085-525f4b48ea4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3153
**MSB3156: Die XML\-Validierung konnte für das Element \<Paket\> in \<Ordner\> nicht erfolgreich durchgeführt werden.**  
  
 Diese Warnung wird generiert, wenn das Manifest \(namentlich package.xml\) die XML\-Validierung nicht besteht.  Die spezifischen Probleme werden in einer nachfolgenden Fehlermeldung aufgeführt \([MSBuild Error MSB3159](../misc/msbuild-error-msb3159.md) oder [MSBuild Error MSB3160](../misc/msbuild-error-msb3160.md)\).  
  
### So beheben Sie diesen Fehler  
  
-   Beheben Sie die in den nachfolgenden Fehlermeldungen aufgelisteten Validierungsprobleme des Manifests.  
  
## Siehe auch  
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)