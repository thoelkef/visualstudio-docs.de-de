---
title: "Invalid assembly strong name or name not specified | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.invalid_strong_name"
ms.assetid: cb02b69d-09a9-478f-914c-fbdc420e973d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Invalid assembly strong name or name not specified
Die **Project**\-Eigenschaft im Objektmodell des Projektsystems war leer. Mit dieser Eigenschaft können Sie einen Schlüsselnamen oder Schlüsselcontainer für die Projekte angeben, die in Assemblys mit starkem Namen \(signierte Assemblys\) integriert werden.  Wenn diese Fehlermeldung angezeigt wird, schlägt das Build fehl.  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass im Code entweder ein Schlüsselcontainername oder eine Schlüsseldatei angegeben ist.  
  
## Siehe auch  
 [Erstellen und Verwenden von Assemblys mit starkem Namen](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)