---
title: "MSBuild Error MSB3174 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidValue"
helpviewer_keywords: 
  - "MSB3174"
ms.assetid: 6f9a040c-7f21-40fd-bf74-03f99f265e79
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3174
**MSB3174: Ungültiger Wert für \<Datei\>.**  
  
 Dieser Fehler wird generiert, wenn im Buildprozess beim Überprüfen des Manifestdateiformats ein unspezifisches Problem auftritt.  Die Fehlermeldung bezieht sich auf den Namen der Manifestdatei.  
  
 Diese Fehlermeldung wird generiert, wenn einer der folgenden Parameter falsch festgelegt ist.  Jeder aufgeführte Parameter ist eine <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>\-Eigenschaft oder eine <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>\-Eigenschaft, wie zum Beispiel <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> oder <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.MinimumRequiredVersion%2A>.  
  
 Wenn die Aufgabe <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> lautet, gelten die folgenden Voraussetzungen:  
  
|Parameter|Anforderungen|  
|---------------|-------------------|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyName%2A>|Muss ein gültiger Dateiname sein.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyVersion%2A>|Verfügt über die gleichen Voraussetzungen wie <xref:System.Version.%23ctor%2A>.  Alle Oktette müssen größer als 0 \(null\) sein.  Es müssen alle vier Oktette angegeben werden.  Eine leere Zeichenfolge ist zulässig.|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.ClrVersion%2A>|Verfügt über die gleichen Voraussetzungen wie <xref:System.Version.%23ctor%2A>.  Alle Oktette müssen größer als 0 \(null\) sein.  Es müssen alle vier Oktette angegeben werden.  Eine leere Zeichenfolge ist zulässig.|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.OSVersion%2A>|Verfügt über die gleichen Voraussetzungen wie <xref:System.Version.%23ctor%2A>.  Alle Oktette müssen größer als 0 \(null\) sein.  Es müssen alle vier Oktette angegeben werden.  Eine leere Zeichenfolge ist zulässig.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.Platform%2A>|Muss **AnyCPU**, **x86**, **x64** oder **Itanium** lauten.  Eine leere Zeichenfolge ist zulässig.|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.ManifestType%2A>|Muss **Systemeigen** oder **ClickOnce** sein.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.TargetCulture%2A>|Eine leere Zeichenfolge ist zulässig.  Kann auch eine neutrale Kultur sein \(wird nur durch den aus zwei Kleinbuchstaben bestehenden Sprachcode angegeben, z. B. "jp" für Japanisch\).  Andernfalls weist dieser Wert über die gleichen Voraussetzungen wie <xref:System.Globalization.CultureInfo.%23ctor%2A> auf.|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>|Muss das Format v*\#**\#* aufweisen.  Muss höher als v2.0 sein.  Eine leere Zeichenfolge ist zulässig.|  
  
 Wenn die Aufgabe <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest> lautet, gelten die folgenden Voraussetzungen:  
  
|Parameter|Anforderungen|  
|---------------|-------------------|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyName%2A>|Muss ein gültiger Dateiname sein.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyVersion%2A>|Verfügt über die gleichen Voraussetzungen wie <xref:System.Version.%23ctor%2A>.  Alle Oktette müssen größer als 0 \(null\) sein.  Es müssen alle vier Oktette angegeben werden.  Eine leere Zeichenfolge ist zulässig.|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.MinimumRequiredVersion%2A>|Verfügt über die gleichen Voraussetzungen wie <xref:System.Version.%23ctor%2A>.  Alle Oktette müssen größer als 0 \(null\) sein.  Eine leere Zeichenfolge ist zulässig.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.Platform%2A>|Muss **AnyCPU**, **x86**, **x64** oder **Itanium** lauten.  Eine leere Zeichenfolge ist zulässig.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.TargetCulture%2A>|Eine leere Zeichenfolge ist zulässig.  Kann auch eine neutrale Kultur sein \(wird nur durch den aus zwei Kleinbuchstaben bestehenden Sprachcode angegeben, z. B. "jp" für Japanisch\).  Andernfalls weist dieser Wert über die gleichen Voraussetzungen wie <xref:System.Globalization.CultureInfo.%23ctor%2A> auf.|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.UpdateMode%2A>|Muss **Vordergrund** oder **Hintergrund** lauten.  Eine leere Zeichenfolge ist zulässig.|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.UpdateUnit%2A>|Muss **Stunden**, **Tage** oder **Wochen** lauten.  Eine leere Zeichenfolge ist zulässig.|  
  
## Siehe auch  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)   
 [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)   
 [MSBuild Error MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild Error MSB3117](../misc/msbuild-error-msb3117.md)   
 [MSBuild Error MSB3118](../misc/msbuild-error-msb3118.md)   
 [MSBuild Error MSB3185](../misc/msbuild-error-msb3185.md)