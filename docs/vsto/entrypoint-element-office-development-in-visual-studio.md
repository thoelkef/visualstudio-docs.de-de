---
title: "&lt;entryPoint&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <entryPoint>-Element"
  - "<entryPoint>-Element"
  - "entryPoint-Element"
ms.assetid: 0c9d22d0-0852-4260-89c6-b83f24e48793
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;entryPoint&gt;-Element (Office-Entwicklung in Visual Studio)
  Durch jedes `entryPoint`\-Element im `vstav3` \-Namespace wird eine Anpassungsassembly gekennzeichnet, die bei Installation dieser [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Anwendung ausgeführt werden sollte.  
  
## Syntax  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## Elemente und Attribute  
 Das `entryPoint`\-Element ist erforderlich und befindet sich im `vstav3` \-Namespace.  
  
 Jedes `entryPoint`\-Element kann nur eine Anpassungsassembly enthalten. In einem Anwendungsmanifest können mehrere `entryPoint`\-Elemente definiert werden.  
  
 Das `entryPoint`\-Element weist folgende Attribute auf:  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`class`|Erforderlich. Kennzeichnet eine auszuführende Anpassungsassembly. Die Syntax für dieses Attribut ist *NamespaceName.ClassName*.|  
  
 `entryPoint` weist das folgende Element auf:  
  
### assemblyIdentity  
 Erforderlich. Das `assemblyIdentity`\-Element im `vstav3` \-Namespace verweist auf ein vorhandenes `assemblyIdentity`\-Element im [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Anwendungsmanifest.  
  
 Die Rolle von `assemblyIdentity` und seiner Attribute ist in [&#60;assemblyIdentity&#62; Element &#40;ClickOnce Application&#41;](~/deployment/assemblyidentity-element-clickonce-application.md) definiert.  
  
## Beispiel für die Anpassung auf Dokumentebene  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht `entryPoint`\-Elemente in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Office\-Projektmappe auf Dokumentebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## Beispiel für ein VSTO\-Add\-In  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `entryPoint`\-Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Office\-Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  