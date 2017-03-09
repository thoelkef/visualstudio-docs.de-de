---
title: "MSBuild Error MSB3149 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoResources"
helpviewer_keywords: 
  - "MSB3149"
ms.assetid: 63857405-d420-457d-9ba7-80e1a2a9dcb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3149
**MSB3149: Es stehen keine Ressourcen zum Erstellen eines Bootstrappers zur Verfügung.**  
  
 Dieser Fehler tritt auf, wenn keine Bootstrapper\-Ressourcendateien \(setup.xml\), die einer Kultur entsprechen, gefunden wurden.  
  
### So beheben Sie diesen Fehler  
  
-   Öffnen Sie die **Systemsteuerung**, wählen Sie **Software** aus, und reparieren Sie Visual Studio SDK, oder kopieren Sie die Dateien in das entsprechende Verzeichnis \(\<SDK\-Installalationspfad\>\\bootstrapper\\engine\\\<Kultur\>\\setup.xml\).  
  
## Siehe auch  
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)