---
title: "MSBuild Error MSB3143 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyPackageError"
helpviewer_keywords: 
  - "MSB3143"
ms.assetid: b4278c8c-31df-4b4f-9ef9-7b9327e8ee77
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3143
**MSB3143: Fehler beim Kopieren von \<Datei\> für das \<Paket\>\-Element: \<Fehler\>**  
  
 Dieser Fehler wird ausgegeben, wenn Bootstrapperpakete in das Buildausgabeverzeichnis kopiert werden.  Dieser Fehler kann folgende Ursachen haben:  
  
-   Sie verfügen nicht über die Berechtigung zum Kopieren in das Buildausgabeverzeichnis.  
  
-   Der Datenträger ist voll.  
  
 Aus den gleichen Gründe kann auch file.copy oder directory.createdirectory scheitern.  
  
## Siehe auch  
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)