---
title: "Unterschiede zwischen Sandkasten- und Farml&#246;sungen | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Farmlösungen [SharePoint-Entwicklung in Visual Studio]"
  - "Sandkastenlösungen [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Farmlösungen"
  - "SharePoint-Entwicklung in Visual Studio, Sandkastenlösungen"
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Unterschiede zwischen Sandkasten- und Farml&#246;sungen
  Bei der Kompilierung einer SharePoint\-Lösung wird sie auf dem SharePoint\-Server bereitgestellt, und ein Debugger zum Debuggen der Lösung wird angefügt.  Der Prozess, der zum Debuggen der Lösung verwendet wird, hängt von der Einstellung der Eigenschaft "Sandkastenlösung" \("Sandkastenlösung" oder "Farmlösung"\) ab.  
  
 Weitere Informationen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
## Farmlösungen  
 Farmlösungen, die im IIS\-Arbeitsprozess \(W3WP.exe\) gehostet werden, führen Code aus, der sich auf die ganze Farm auswirken kann.  Beim Debuggen eines SharePoint\-Projekts, dessen Eigenschaft "Sandkastenlösung" auf "Farmlösung" festgelegt ist, wird der IIS\-Anwendungspool des Systems wiederverwendet, bevor SharePoint die Funktion zurückzieht oder bereitstellt, um so vom IIS\-Arbeitsprozess gesperrte Dateien freizugeben.  Nur der IIS\-Anwendungspool für die Website\-URL des SharePoint\-Projekts wird wiederverwendet.  
  
## Sandkastenlösungen  
 Sandkastenlösungen, die im SharePoint\-Anwendercodelösungs\-Arbeitsprozess \(SPUCWorkerProcess.exe\) gehostet werden, führen Code aus, der sich auf nur die Websiteauflistung der Lösung auswirken kann.  Da Sandkastenlösungen nicht im IIS\-Arbeitsprozess ausgeführt werden, muss weder der IIS\-Anwendungspool noch der IIS\-Server neu gestartet werden.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt den Debugger an den SPUCWorkerProcess\-Prozess an, der vom SPUserCodeV4\-Dienst in SharePoint automatisch ausgelöst und gesteuert wird.  Der SPUCWorkerProcess\-Prozess muss nicht wiederverwendet werden, um die neueste Version der Lösung zu laden.  
  
## Beide Lösungstypen  
 Mit beiden Lösungstypen wird der Debugger von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] an den Browser angefügt, um clientseitiges Skriptdebugging zu aktivieren.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwendet zu diesem Zweck das Skriptdebugmodul.  Um Skriptdebugging zu aktivieren, müssen bei Aufforderung die Standardbrowsereinstellungen geändert werden.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt den Debugger nur an die W3WP\- oder SPUCWorkerProcess\-Prozesse an, von denen die aktuelle Website ausgeführt wird.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt zudem das verwaltete COM\-Plus\-Modul und das Workflowdebugmodul an.  
  
## Siehe auch  
 [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md)   
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md)  
  
  