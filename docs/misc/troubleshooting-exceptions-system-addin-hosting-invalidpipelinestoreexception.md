---
title: "Problembehandlung bei Ausnahmen: System.AddIn.Hosting.InvalidPipelineStoreException | Microsoft Docs"
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
  - "InvalidPipelineStoreException-Ausnahme"
  - "System.AddIn.Hosting.InvalidPipelineStoreException-Ausnahme"
ms.assetid: d12556bc-5cfd-481c-a27b-46ee2571e646
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.AddIn.Hosting.InvalidPipelineStoreException
Die <xref:System.AddIn.Hosting.InvalidPipelineStoreException>\-Ausnahme, die ausgelöst wird, wenn ein Verzeichnis nicht gefunden wird und der Benutzer nicht über die Berechtigung zum Zugriff auf den Stammpfad der Pipeline oder einen Add\-In\-Pfad verfügt.  
  
## Hinweise  
 Im Gegensatz zur <xref:System.IO.DirectoryNotFoundException> stellt diese Ausnahme keine Pfadinformationen bereit. Hierdurch wird verhindert, dass ein böswilliger Benutzer absichtlich falsche Pfade angibt und die von der Ausnahme zurückgegebenen Informationen zur Ermittlung der tatsächlichen Pfade verwendet.  
  
 Diese Ausnahme wird von den folgenden Ermittlungsmethoden ausgelöst, die den Speicher mit Add\-In\- und Pipelineinformationen erstellen und aktualisieren: <xref:System.AddIn.Hosting.AddInStore.FindAddIns%2A>, <xref:System.AddIn.Hosting.AddInStore.Rebuild%2A>, <xref:System.AddIn.Hosting.AddInStore.RebuildAddIns%2A>, <xref:System.AddIn.Hosting.AddInStore.Update%2A> und <xref:System.AddIn.Hosting.AddInStore.UpdateAddIns%2A>.  
  
## Siehe auch  
 <xref:System.AddIn.Hosting.InvalidPipelineStoreException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)