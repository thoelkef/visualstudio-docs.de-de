---
title: "MSBuild Error MSB3144 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidInput"
helpviewer_keywords: 
  - "MSB3144"
ms.assetid: 955e0db3-afe2-4c03-8e95-3419878374df
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3144
**MSB3144: Es wurden nicht genügend Daten zur Verfügung gestellt, um einen Bootstrapper zu generieren.  Geben Sie einen Wert für mindestens einen der Parameter ApplicationFile oder BootstrapperItems an.**  
  
 Dieser Fehler tritt auf, wenn nicht genügend Daten zum Generieren eines Bootstrappers angegeben wurden.  Der Buildprozess erstellt dann einen leeren Bootstrapper ohne Anwendungsinstallationsprogramm und ohne Pakete.  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie mindestens für einen der Parameter `ApplicationFile` oder `BootstrapperItems` einen Wert an.  
  
## Siehe auch  
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)