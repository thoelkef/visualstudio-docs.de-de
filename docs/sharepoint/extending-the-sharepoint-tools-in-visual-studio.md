---
title: "Extending the SharePoint Tools in Visual Studio | Microsoft Docs"
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
helpviewer_keywords: 
  - "Visual Studio, extending tools"
  - "extensibility [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Tools in Visual Studio
  Die SharePoint\-Tools in Visual Studio erfüllen die Anforderungen vieler Anwendungsentwicklung Szenarios.  Es kann jedoch auch Fälle geben, in denen eine bestimmte Funktionalität, die Sie oder andere Entwickler benötigen, nicht zur Verfügung steht.  In so einem Fall können Sie die SharePoint\-Tools erweitern, um die benötigte Funktionalität zu erstellen.  
  
## So erweitern Sie die SharePoint\-Tools  
 Sie können das SharePoint\-Projektsystem und den Knoten **SharePoint\-Verbindungen** im Fenster **Server\-Explorer** erweitern.  
  
### Erweitern des SharePoint\-Projektsystems  
 Visual Studio umfasst eine Reihe von Projektvorlagen und Elementvorlagen, die Sie verwenden können, um SharePoint\-Lösungen zu erstellen.  Es gibt z. B. Vorlagen für Ereignisempfänger, Listendefinitionen, Workflows oder Webparts.  Sie können jedoch auch eigene Typen von SharePoint\-Projektelementen definieren, um SharePoint\-Komponenten \(z. B. Felder oder benutzerdefinierte Aktionen\) zu erstellen.  Darüber hinaus können Sie Erweiterungen für SharePoint\-Projektelementtypen erstellen, die bereits in Visual Studio installiert sind, und Sie können Erweiterungen für SharePoint\-Projekte erstellen.  
  
 Weitere Informationen finden Sie unter [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### Erweitern des SharePoint\-Verbindungsknotens im Server\-Explorer  
 In Visual Studio können Sie den **SharePoint\-Verbindungen** Knoten im **Server\-Explorer** Fenster verwenden, um viele der Komponenten einer oder mehreren lokalen SharePoint\-Websites in einer hierarchischen Strukturansicht anzuzeigen. Sie können den **SharePoint\-Verbindungen** Knoten auch auf die folgende Weise erweitern:  
  
-   Durch das Hinzufügen eigener Knoten.  Dies ist hilfreich, wenn Sie Komponenten von SharePoint\-Websites anzeigen möchten, die standardmäßig nicht angezeigt werden.  
  
-   Durch das Erweitern vorhandener Knoten.  Sie können z. B. einem vorhandenen Knoten einen neuen untergeordneten Knoten hinzufügen oder einem Knoten ein Kontextmenüelement hinzufügen und Aufgaben ausführen, wenn ein Entwickler auf das Menüelement klickt.  
  
 Weitere Informationen finden Sie unter [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## Anforderungen an den Entwicklungscomputer  
 Um Erweiterungen für die SharePoint\-Tools zu erstellen, muss der Entwicklungscomputer über die gleichen Voraussetzungen zum Erstellen von SharePoint\-Lösungen in Visual Studio erfüllen.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 Zudem wird die Installation von [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] empfohlen.  Das SDK enthält Projektvorlagen und Tools, mit denen Sie Visual Studio erweitern können.  Vor allem enthält das SDK eine Projektvorlage, mit der Sie leicht Visual Studio\-Erweiterungspakete \(VSIX\) erstellen können.  VSIX\-Pakete sind die bevorzugte Methode für Visual Studio\-Erweiterungen in Visual Studio bereitzustellen.  Alle Erweiterungen der SharePoint\-Tools müssen mit VSIX\-Paketen bereitgestellt werden.  In allen exemplarischen Vorgehensweisen in dieser Dokumentation wird davon ausgegangen, dass [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installiert wurde.  
  
 Das SDK kann unter [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164562](http://go.microsoft.com/fwlink/?LinkId=164562) heruntergeladen werden.  Weitere Informationen zu Visual Studio\-Erweiterungen finden Sie unter [Entwickeln von Visual Studio-Erweiterungen](http://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).  
  
## Siehe auch  
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Reference &#40;SharePoint Tools Extensibility&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  