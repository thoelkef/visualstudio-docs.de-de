---
title: "&lt;entryPointsCollection&gt;-Element (Office-Entwicklung in Visual Studio) | Microsoft Docs"
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
  - "<entryPointsCollection>-Element"
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <entryPointsCollection>-Element"
  - "entryPointsCollection-Element"
ms.assetid: da386d67-e45f-467c-a9ba-9b8451b520eb
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# &lt;entryPointsCollection&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `entryPointsCollection`\-Element des `vstav3` \-Namespace enthält alle `entryPoints`\-Elemente, die Office\-Projektmappen zugeordnet sind.  
  
## Syntax  
  
```  
<entryPointsCollection>  
  <entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
  </entryPoints>  
</entryPointsCollection>  
```  
  
## Elemente und Attribute  
 Das `entryPointsCollection`\-Element ist erforderlich und befindet sich im `vstav3`\-Namespace. Untergeordnete Elemente müssen sich ebenfalls in diesem Namespace befinden. In einem Anwendungsmanifest ist nur ein `entryPointsCollection`\-Element definiert.  
  
 Das `entryPointsCollection`\-Element weist keine Attribute auf.  
  
 `entryPointsCollection` hat die folgenden Elemente:  
  
### entryPoints  
 Erforderlich. Die Rolle des `entryPoints`\-Elements im `vstav3` \-Namespace ist im [&#60;entryPoints&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md) definiert.  
  
## Beispiel für die Anpassung auf Dokumentebene  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `entryPointsCollection`\-Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Projektmappe auf Dokumentebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection>  
```  
  
## Beispiel für ein VSTO\-Add\-In  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `entryPointsCollection`\-Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection>  
```  
  
## Beispiel für eine Bereitstellung mit mehreren Projekten  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `entryPointsCollection`\-Element in einem Anwendungsmanifest für eine Bereitstellung mit mehreren Projekten mit zwei Office\-Projektmappen. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPointsCollection> <vstav3:entryPoints id="ContosoExcel"> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> <vstav3:entryPoints id="ContosoOutlook"> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  