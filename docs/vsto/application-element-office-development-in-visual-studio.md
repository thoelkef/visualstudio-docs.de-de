---
title: "&lt;application&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <application>-Element"
ms.assetid: b8d3db7c-9127-4812-b18f-bb17e1f8788f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# &lt;application&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `application`\-Element des `vstav3`\-Namespace umschließt die Beschreibung von Office\-Projektmappen Die untergeordneten Elemente sind für Anpassungen auf Dokumentebene und für VSTO\-Add\-Ins unterschiedlich.  
  
## Syntax für Anpassungen auf Dokumentebene  
  
```  
<application> <customization id <document solutionId /> </customization> </application>  
```  
  
## Syntax für Add\-Ins auf Anwendungsebene  
  
```  
<application> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </application>  
```  
  
## Elemente und Attribute  
 Das `application`\-Element des `vstav3`\-Namespace ist der Knoten, der alle anpassungsspezifischen Informationen umschließt, die im `vstov4`\-Namespace enthalten sind.  
  
 Das `application`\-Element weist keine Attribute auf.  
  
 Das `application`\-Element hat das folgende Element.  
  
### Anpassung  
 Die Rolle des `customization`\-Elements im `vstov3`\-Namespace ist im [&#60;customization&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md) definiert.  
  
## Beispiel für die Anpassung auf Dokumentebene  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `application`\-Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellten Office\-Projektmappe auf Dokumentebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## Beispiel für ein VSTO\-Add\-In  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `application`\-Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellten Office\-Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  