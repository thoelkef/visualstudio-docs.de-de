---
title: "Calling into the SharePoint Object Models | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint development in Visual Studio, server object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Calling into the SharePoint Object Models
  Wenn Sie Erweiterungen für die SharePoint\-Tools in Visual Studio erstellen, müssen Sie ggf. SharePoint\-APIs aufrufen, um bestimmte Aufgaben auszuführen.  Wenn Sie z. B. einen benutzerdefinierten Bereitstellungsschritt für SharePoint\-Projekte erstellen, müssen Sie eventuell SharePoint\-APIs aufrufen, um einige der Aufgaben für das Bereitstellen von Projektmappen auszuführen.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] stellen zwei verschiedene Objektmodelle bereit, die Sie in Erweiterungen für SharePoint\-Tools verwenden können: ein Serverobjektmodell und ein Clientobjektmodell.  Jedes Objektmodell hat Vor\- und Nachteile im Kontext von SharePoint\-Tools\-Erweiterungen.  
  
 Eine Übersicht über die SharePoint\-Objektmodelle finden Sie unter [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Verwenden des Clientobjektmodells in Erweiterungsprojekten  
 Wenn Sie eine Erweiterung für die SharePoint\-Tools entwickeln, können Sie das Clientobjektmodell im Projekt wie jeden anderen Satz verwalteter APIs verwenden.  Sie können dem Projekt Verweise auf Assemblys im Clientobjektmodell hinzufügen, und Sie können APIs im Clientobjektmodell direkt vom Code aufrufen.  
  
 Das Clientobjektmodell weist jedoch zwei Nachteile bezüglich SharePoint\-Toolerweiterungen auf:  
  
-   Das Clientobjektmodell stellt nur eine Teilmenge des Serverobjektmodells bereit.  Wenn Sie SharePoint\-Funktionalitäten verwenden müssen, die im Clientobjektmodell nicht verfügbar sind, müssen Sie das Serverobjektmodell verwenden.  
  
-   Außerdem kann das Clientobjektmodell zwar in vielen Fällen für SharePoint\-Toolerweiterungen verwendet werden, es gibt aber auch Szenarios, in denen Aufrufe des Clientobjektmodells nicht in der erwarteten Weise funktionieren.  Das Clientobjektmodell wurde für Aufrufe in SharePoint\-Websites auf einem Remoteserver oder in einer Remotefarm in Clientanwendungen entwickelt.  Die SharePoint\-Tools in Visual Studio funktionieren nur mit einer lokalen SharePoint\-Installation auf dem Entwicklungscomputer.  Wenn Sie das Clientobjektmodell in einer SharePoint\-Toolerweiterung verwenden, rufen Sie daher eine SharePoint\-Website auf dem lokalen Computer auf. Dies entspricht nicht der vorgesehenen Verwendung des Clientobjektmodells.  
  
 Eine exemplarische Vorgehensweise, die zeigt, wie das Clientobjektmodell in einer Erweiterung der SharePoint\-Tools in Visual Studio finden. [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## Verwenden des Serverobjektmodells in Erweiterungsprojekten  
 Das Serverobjektmodell ist eine Obermenge des Clientobjektmodells.  Wenn Sie das Serverobjektmodell verwenden, können Sie alle Funktionen verwenden, die [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] programmgesteuert verfügbar machen.  
  
 SharePoint\-Tools\-Erweiterungen können APIs im Serverobjektmodell verwenden, aber sie können die APIs nicht direkt aufrufen.  Das Serverobjektmodell kann nur von einem 64\-Bit\-Prozess aufgerufen werden, der auf .NET Framework 3.5 abzielt.  SharePoint\-Tools\-Erweiterungen erfordern jedoch [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und werden im 32\-Bit\-Prozess von Visual Studio ausgeführt.  Dies verhindert, dass SharePoint\-Tools\-Erweiterungen direkt auf die Assemblys im SharePoint\-Serverobjektmodell verweisen.  
  
 Wenn Sie das Serverobjektmodell in einer SharePoint\-Tools\-Erweiterung verwenden möchten, müssen Sie einen benutzerdefinierten *SharePoint\-Befehl* erstellen, um die API aufzurufen.  Sie definieren den SharePoint\-Befehl in einer sekundären Assembly, die direkte Aufrufe des Serverobjektmodells ausführen kann.  Im Erweiterungsprojekt rufen Sie den SharePoint\-Befehl indirekt mit der ExecuteCommand\-Methode eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>\-Objekts auf.  
  
 Weitere Informationen zum Erstellen und Verwenden von SharePoint\-Befehlen finden Sie unter [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md) und [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).  Informationen zum Bereitstellen von SharePoint\-Befehlen finden Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Exemplarische Vorgehensweisen, in denen das Erstellen und Verwenden von SharePoint\-Befehlen veranschaulicht wird, finden Sie unter [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) und [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### Grundlegendes zur Ausführung von SharePoint\-Befehlen  
 Assemblys, die SharePoint\-Befehle definieren, werden in einen 64\-Bit\-Hostprozess mit dem Namen "vssphost4.exe" geladen.  Nachdem Sie einen SharePoint\-Befehl in einer SharePoint\-Tools\-Erweiterung aufgerufen haben, wird der Befehl von "vssphost4.exe" ausgeführt, und nicht vom 32\-Bit\-Prozess von Visual Studio \(devenv.exe\).  Einige Aspekte der Ausführung von SharePoint\-Befehlen können mit Werten in der Registrierung gesteuert werden.  Weitere Informationen finden Sie unter [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  