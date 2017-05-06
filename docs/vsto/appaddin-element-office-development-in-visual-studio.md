---
title: "&lt;appAddin&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <appAddin>-Element"
ms.assetid: 6152fe5b-6af1-465d-aee7-19e4fd4d04c1
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# &lt;appAddin&gt;-Element (Office-Entwicklung in Visual Studio)
  Im `appAddin`\-Element des `vstov4` \-Namespace werden anpassungsspezifische Informationen für VSTO\-Add\-Ins gespeichert.  
  
## Syntax  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## Elemente und Attribute  
 Das `appAddin`\-Element ist erforderlich und befindet sich im `vstov4` \-Namespace. In einem Anwendungsmanifest ist nur ein `appAddin`\-Element definiert.  
  
 Das `appAddin`\-Element weist folgende Attribute auf:  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`application`|Erforderlich. Identifiziert die Microsoft Office\-Anwendung. Einer der folgenden Werte ist möglich: Excel, InfoPath, Outlook, PowerPoint, Project, Visio oder Word.|  
|`loadBehavior`|Optional.`loadBehavior` wird standardmäßig aktiviert, indem dieser Wert entsprechend festgelegt wird. Zum Debuggen kann das VSTO\-Add\-In deaktiviert werden, indem der Wert auf 2 festgelegt wird. Weitere Informationen finden Sie in der Tabelle mit dem Namen "LoadBehavior\-Werte" in [Registrierungseinträge für VSTO-Add-Ins](../vsto/registry-entries-for-vsto-add-ins.md).|  
|`keyName`|Erforderlich. Dieser Wert ist der Name des Registrierungsschlüssels, der von der Anwendung zum Laden des VSTO\-Add\-Ins verwendet wird. Weitere Informationen finden Sie unter [Registrierungseinträge für VSTO-Add-Ins](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 Das `appAddin`\-Element weist die folgenden untergeordneten Elemente auf:  
  
### friendlyName  
 Optional. Das `friendlyName`\-Element wird in [&#60;friendlyName&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md) erläutert.  
  
### Beschreibung  
 Optional. Das `description`\-Element wird in [&#60;description&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md) erläutert.  
  
### formRegions  
 Nur für Outlook VSTO\-Add\-Ins erforderlich, die Formularbereiche enthalten. Das `formRegions`\-Element wird in [&#60;formRegions&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md) erläutert.  
  
## Beispiel für ein VSTO\-Add\-In  
  
### Beschreibung  
 Im folgenden Codebeispiel werden `appAddin`\-Elemente in einer Outlook\-Projektmappe veranschaulicht, die mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellt wurde. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  