---
title: "&lt;customHostSpecified&gt;-Element (Office-Entwicklung in Visual Studio) | Microsoft Docs"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <customHostSpecified>-Element"
  - "<customHostSpecified>-Element"
  - "customHostSpecified-Element"
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;customHostSpecified&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `customHostSpecified`\-Element gibt an, dass es sich bei dieser Projektmappe nicht um eine eigenständige Anwendung handelt.  Office\-Projektmappen enthalten Komponenten, die in Microsoft\-Anwendungen gehostet werden.  
  
## Syntax  
  
```  
<customHostSpecified />  
```  
  
## Elemente und Attribute  
 Das `customHostSpecified`\-Element ist für Office\-Projektmappen erforderlich.  Dieses Element befindet sich im `co.v1`\-Namespace und gibt an, dass diese Bereitstellung eine Komponente enthält, die innerhalb eines benutzerdefinierten Hosts bereitgestellt wird und dass es sich nicht um eine eigenständige Anwendung handelt.  
  
 Dieses Element ist ein untergeordnetes Element des ersten `<entrypoint>`\-Elements im Anwendungsmanifest.  In diesem `<entrypoint>`\-Element dürfen keine anderen untergeordneten Elemente enthalten sein, da von [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] andernfalls während der Installation ein Validierungsfehler ausgegeben wird.  
  
 Dieses Element verfügt über keine Attribute und keine untergeordneten Elemente.  
  
## Beispiel  
 Im Folgenden Codebeispiel wird das `customHostSpecified` Element in einem Anwendungsmanifest für eine Office\-Projektmappe.  Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels, das Sie im Thema [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md) finden.  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  