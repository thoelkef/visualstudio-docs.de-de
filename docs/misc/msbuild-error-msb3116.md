---
title: "MSBuild Error MSB3116 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.HostInBrowserNotOnlineOnly"
helpviewer_keywords: 
  - "MSB3116"
ms.assetid: bf04c587-d0e2-4d68-bbff-da9a985ea70e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3116
**MSB3116: Die Anwendung ist für das Hosten im Browser gekennzeichnet, ist aber ebenfalls für die Online\- und Offlineverwendung markiert.  Ändern Sie die Anwendung auf reine Onlineverwendung.**  
  
 Wenn Sie eine WPF\-Webbrowseranwendung bereitstellen, müssen Sie für die <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>\-Eigenschaft `True` festlegen.  Wenn für <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> `True` festgelegt ist, müssen Sie für die <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A>\-Eigenschaft `False` festlegen \(um die Installation nur online verfügbar zu machen\).  Wenn letztere Bedingung nicht erfüllt wird, erhalten Sie diese Fehlermeldung.  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie für die <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A>\-Eigenschaft `False` fest.  
  
## Siehe auch  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A>   
 [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)