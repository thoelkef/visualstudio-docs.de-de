---
title: "MSBuild Error MSB3486 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertificateError"
helpviewer_keywords: 
  - "MSB3486"
ms.assetid: 75d03d8e-3a28-4010-b602-61fe037dec74
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3486
**MSB3486: Zertifikat kann nicht aus Speicher \<Zertifikatspeicher\> abgerufen werden.**  
  
 Dieser Fehler wird von der `ResolveKeySource`\-Aufgabe von MSBuild generiert, wenn das Zertifikat, das dem Daumenabdruck der PFX\-Datei des Projekts entspricht, nicht in Ihrem persönlichen Zertifikatspeicher gefunden wurde.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass der Daumenabdruck der PFX\-Datei des Projekts dem Daumenabdruck des Zertifikats in Ihrem persönlichen Zertifikatspeicher entspricht.  
  
## Siehe auch  
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)