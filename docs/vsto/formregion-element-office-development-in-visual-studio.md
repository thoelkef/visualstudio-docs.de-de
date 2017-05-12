---
title: "&lt;formRegion&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <formRegion>-Element"
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt;formRegion&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `formRegion`\-Element des `vstov4` \-Namespace identifiziert einen Microsoft Office Outlook\-Formularbereich, der einem VSTO\-Add\-In zugeordnet ist.  
  
## Syntax  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## Elemente und Attribute  
 Das `formRegion`\-Element des `vstov4` \-Namespace identifiziert einen Formularbereich, der einem VSTO\-Add\-In für Outlook zugeordnet ist. Es ist nur für Outlook\-VSTO\-Add\-Ins erforderlich, die Formularbereiche einbeziehen.  
  
 Es können mehrere `formRegion`\-Elemente in einem `formRegions`\-Element für ein einzelnes VSTO\-Add\-In definiert sein.  
  
 Das `formRegion`\-Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`name`|Erforderlich. Gibt den Namen des Formularbereichs an.|  
  
 Das `formRegion`\-Element weist die folgenden untergeordneten Elemente auf.  
  
### messageClass  
 Das `messageClass` \-Element identifiziert das Outlook\-Formular, das dem Formularbereich zugeordnet ist.  
  
 Das `messageClass`\-Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`name`|Erforderlich. Identifiziert das Formular, das dem Formularbereich zugeordnet ist.|  
  
## Beispiel  
 Das folgende Codebeispiel veranschaulicht ein `formRegion`\-Element in einem Anwendungsmanifest für ein mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestelltes Outlook\-VSTO\-Add\-In. Es gibt drei Nachrichtenklassen, die diesem einen Formularbereich zugeordnet sind. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion>  
```  
  
## Siehe auch  
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  