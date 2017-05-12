---
title: "&lt;formRegions&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "formRegions-Element"
  - "<formRegions>-Element"
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <formRegions>-Element"
ms.assetid: 71faa2da-9d38-43e8-9d7d-0bcd944ef9a3
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;formRegions&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `formRegions`\-Element des `vstov4` \-Namespace enthält die Microsoft Office Outlook\-Formularbereiche, die einem VSTO\-Add\-In zugeordnet sind  
  
## Syntax  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## Elemente und Attribute  
 Das `formRegions`\-Element des `vstov4` \-Namespace enthält alle `formRegion`\-Elemente für ein Outlook\-VSTO\-Add\-In. Es ist nur für Outlook\-VSTO\-Add\-Ins erforderlich, die Formularbereiche beinhalten.  
  
 In einem Anwendungsmanifest kann nur ein `formRegions`\-Element definiert sein.  
  
 Das `formRegions`\-Element hat keine Attribute.  
  
 Das `formRegions`\-Element hat das folgende Element.  
  
### formRegion  
 Erforderlich für Outlook\-VSTO\-Add\-Ins, die Formularbereiche beinhalten. Das `formRegion`\-Element ist in [&#60;formRegion&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md) definiert.  
  
## Beispiel für ein VSTO\-Add\-In  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `formRegions`\-Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Office\-Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  