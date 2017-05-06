---
title: "&lt;description&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "description-Element"
  - "<description>-Element"
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <description>-Element"
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;description&gt;-Element (Office-Entwicklung in Visual Studio)
  Im `description`\-Element des `vstov4` \-Namespace wird die Beschreibung für die Office\-Projektmappe gespeichert, die im Dialogfeld für COM\-Add\-Ins von Microsoft Office\-Anwendungen angezeigt werden.  
  
## Syntax  
  
```  
<description>  
</description>  
```  
  
## Elemente und Attribute  
 Optional. Das `description`\-Element befindet sich im `vstov4` \-Namespace. Es enthält die Beschreibung des Add\-Ins, das im Dialogfeld für COM\-Add\-Ins von Microsoft Office\-Anwendungen angezeigt wird.  
  
 Das `description`Element weist keine Attribute oder Elemente auf.  
  
## Beispiel für ein VSTO\-Add\-In  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `description`\-Element für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:description> ContosoOutlookAddIn - Outlook add-in created with Visual Studio Tools for Office </vstov4:description>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  