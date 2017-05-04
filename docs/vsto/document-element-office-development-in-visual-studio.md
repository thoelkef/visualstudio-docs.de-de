---
title: "&lt;document&gt;-Element (Office-Entwicklung in Visual Studio) | Microsoft Docs"
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
  - "document-Element"
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <document>-Element"
  - "<document>-Element"
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;document&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `document`\-Element des `vstov4` \-Namespace speichert anpassungsspezifische Informationen für Anpassungen auf Dokumentebene.  
  
## Syntax  
  
```  
<document solutionId />  
```  
  
## Elemente und Attribute  
 Nur für Anpassungen auf Dokumentebene erforderlich.  Das `document`\-Element befindet sich im `vstov4` \-Namespace.  Das `document`\-Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`solutionId`|Erforderlich.  Die GUID für die Visual Studio Tools für Office Runtime eine Projektmappe auf Dokumentebene eindeutig identifiziert.  Dieser Wert wird als benutzerdefinierte \_AssemblyLocation\-Dokumenteigenschaft gespeichert.  Weitere Informationen finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](../vsto/custom-document-properties-overview.md).|  
  
 `document` verfügt über keine untergeordneten Elemente.  
  
## Beispiel für die Anpassung auf Dokumentebene  
  
### Beschreibung  
 Im folgenden Codebeispiel wird das `document`\-Element in einer Office\-Projektmappe auf Dokumentebene dargestellt, die mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellt wird.  Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels, das Sie im Thema [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md) finden.  
  
### Code  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  