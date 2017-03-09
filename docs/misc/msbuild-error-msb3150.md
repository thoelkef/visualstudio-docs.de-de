---
title: "MSBuild Error MSB3150 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
helpviewer_keywords: 
  - "MSB3150"
ms.assetid: 90d86aef-f4df-4070-8ecc-173eb40668aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3150
**MSB3150: Es stehen keine Zeichenfolgenressourcen zum Erstellen eines Bootstrappers mit der Kultur \<Kultur\> zur Verfügung.**  
  
 Dieser Fehler tritt auf, wenn setup.xml gefunden wurde, jedoch keinen Zeichenfolgenknoten enthielt.  Die XML\-Datei ist vermutlich beschädigt.  
  
### So beheben Sie diesen Fehler  
  
-   Öffnen Sie die **Systemsteuerung**, wählen Sie **Software** aus, und reparieren Sie Visual Studio SDK, oder kopieren Sie die Dateien in das entsprechende Verzeichnis \(\<SDK\-Installalationspfad\>\\bootstrapper\\engine\\\<Kultur\>\\setup.xml\).