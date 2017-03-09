---
title: "MSBuild Error MSB3117 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.HostInBrowserInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3117"
ms.assetid: 18aec642-6000-4626-bf75-f3547769c780
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3117
**MSB3117: Die Anwendung ist auf das Hosten im Browser festgelegt, für die TargetFrameworkVersion wurde jedoch v2.0 angegeben.**  
  
 Eine WPF\-Webbrowseranwendung wurde bereitgestellt, wobei für die <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>\-Eigenschaft `True` festgelegt ist, TargetFrameworkVersion jedoch auf `v2.0` oder `v3.0` eingestellt wurde.  Wenn Sie diese Einstellung verwenden, müssen Sie für die <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>\-Eigenschaft außerdem mindestens den Wert `v3.5` festlegen.  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie den Wert der <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>\-Eigenschaft auf mindestens `v3.5` fest.  
  
## Siehe auch  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)   
 [MSBuild Error MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild Error MSB3118](../misc/msbuild-error-msb3118.md)   
 [MSBuild Error MSB3174](../misc/msbuild-error-msb3174.md)   
 [MSBuild Error MSB3185](../misc/msbuild-error-msb3185.md)