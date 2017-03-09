---
title: "Problembehandlung bei Ausnahmen: System.IO.InternalBufferOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InternalBufferOverflowException-Klasse"
ms.assetid: 1f58ca15-c4e4-4af9-9a3d-42d2cf919cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IO.InternalBufferOverflowException
Eine <xref:System.IO.InternalBufferOverflowException>\-Ausnahme wird ausgelöst, wenn der interne Puffer überläuft.  
  
## Tipps  
 **Filtern Sie bei Verwendung von FileSystemWatcher unerwünschte Änderungsbenachrichtigungen.**  
 Dateiänderungen werden bei Benachrichtigung durch den FileSystemWatcher vom System in einem Puffer gespeichert. Dieser wird von der Komponente erstellt und an die Anwendungsprogrammierschnittstellen \(APIs\) übergeben. Bei vielen Änderungen innerhalb von kurzer Zeit kann der Puffer überlaufen. Dies hat eine <xref:System.IO.InternalBufferOverflowException>\-Ausnahme zur Folge, bei der alle Änderungen verloren gehen. Damit der Puffer nicht überläuft, verwenden Sie die <xref:System.IO.FileSystemWatcher.NotifyFilter%2A>\-Eigenschaft und die <xref:System.IO.FileSystemWatcher.IncludeSubdirectories%2A>\-Eigenschaft, um unerwünschte Änderungsbenachrichtigungen herauszufiltern. Weitere Informationen finden Sie unter <xref:System.IO.FileSystemWatcher>.  
  
## Hinweise  
 Sie können Größe des internen Puffers auch mit der <xref:System.IO.FileSystemWatcher.InternalBufferSize%2A>\-Eigenschaft vergrößern. Eine größerer Puffer hat jedoch Auswirkungen auf die Leistung. Sie sollten deshalb den Puffer so klein wie möglich halten.  
  
## Siehe auch  
 <xref:System.IO.InternalBufferOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)