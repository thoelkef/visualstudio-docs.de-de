---
title: "&lt;vstoRuntime&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <vstoRuntime>-Element"
  - "<vstoRuntime>-Element"
  - "vstoRuntime-Element"
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# &lt;vstoRuntime&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `vstoRuntime`\-Element des `vstav3` \-Namespace enthält eine unterstützte Version der Visual Studio Tools for Office\-Laufzeit für eine bestimmte Office\-Projektmappe.  
  
## Syntax  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## Elemente und Attribute  
 Das `vstoRuntime`\-Element ist erforderlich und befindet sich im `vstav3` \-Namespace. Wenn eine Office\-Projektmappe zwei Versionen der Visual Studio\-Tools für Office\-Laufzeit unterstützt, gibt es zwei `vstoRuntime`\-Elemente im Anwendungsmanifest.  
  
 Das `vstoRuntime`\-Element weist folgende Attribute auf.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`release`|Erforderlich. Die Releaseversion der Visual Studio Tools for Office\-Laufzeit.|  
|`version`|Erforderlich. Versionsnummer der Visual Studio Tools for Office\-Laufzeit.|  
|`supportUrl`|Optional. Link zum Installationspfad der Visual Studio Tools for Office\-Laufzeit.|  
  
 `vstoRuntime` enthält keine Elemente.  
  
## Beispiel  
 Das folgende Codebeispiel veranschaulicht das `vstoRuntime`\-Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Office\-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstav3:vstoRuntime release="VSTOR40Beta1" version="10.0.20303" supportUrl="http://www.microsoft.com" />  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  