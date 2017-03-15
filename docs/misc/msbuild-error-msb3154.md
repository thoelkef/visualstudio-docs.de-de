---
title: "MSBuild Error MSB3154 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductCultureNotFound"
helpviewer_keywords: 
  - "MSB3154"
ms.assetid: 513b70fa-15f5-4137-bdbc-5974607fb75a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3154
**MSB3154: Keine Zeichenfolgenressourcen für \<Paket\>\-Element gefunden.**  
  
 Dieser Fehler wird generiert, wenn das angegebene Paket keine kulturspezifischen Informationen enthält.  Die Datei package.xml ist entweder nicht vorhanden oder enthält kein `Culture`\-Attribut.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie eine gültige Datei package.xml mit einem korrekten `Culture`\-Tag bereit.