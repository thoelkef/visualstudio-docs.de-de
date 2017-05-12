---
title: "&lt;friendlyName&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <friendlyName>-Element"
ms.assetid: 80250fbf-fccf-4baa-948e-ace7f4449e9c
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt;friendlyName&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `friendlyName`\-Element des `vstov4` Namespace speichert den angezeigten Namen in der Liste der installierten Programme.  
  
## Syntax  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## Elemente und Attribute  
 Das `friendlyName`\-Element befindet sich im `vstov4` Namespace. Der Wert wird in der Liste der installierten Programme auf dem Computer und im Dialogfeld der COM\-VSTO\-Add\-Ins von Microsoft Office\-Anwendungen angezeigt.  
  
 Das `friendlyName`Element weist keine Attribute oder untergeordnete Elemente auf.  
  
## Beispiel für ein VSTO\-Add\-In  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `friendlyName`\-Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellten Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  