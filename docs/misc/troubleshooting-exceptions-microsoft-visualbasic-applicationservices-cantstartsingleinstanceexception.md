---
title: "Problembehandlung bei Ausnahmen: Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CantStartSingleInstanceException-Ausnahme"
  - "Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException-Ausnahme"
ms.assetid: 3639f15d-9547-43da-8145-60da34782991
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException
Diese Ausnahme wird ausgelöst, wenn die zweite Instanz einer Einzelinstanzanwendung keine Verbindung mit der ursprünglichen Instanz herstellen konnte.  
  
## Hinweise  
 Dieses Problem kann folgende Ursachen haben:  
  
-   Die ursprüngliche Instanz reagiert nicht mehr.  
  
-   Die Anwendung verfügt nicht über die Berechtigungen, Kernelobjekte zu erstellen.  
  
     Der Basisname des Kernelobjekts wird gebildet, indem GUID, Hauptversionsnummer und Nebenversionsnummer der Assembly aneinander gehängt werden. Ein Beispiel für einen Basisnamen ist 3639f15d\-9547\-43da\-8145\-60da347829915.1.  
  
## Siehe auch  
 <xref:Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)