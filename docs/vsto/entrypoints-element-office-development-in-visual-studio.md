---
title: "&lt;entryPoints&gt;-Element (Office-Entwicklung in Visual Studio) | Microsoft Docs"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <entryPoints>-Element"
ms.assetid: 991d7cbf-85e5-4307-a470-076b2f74d859
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;entryPoints&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `entryPoints`\-Element des `vstav3` \-Namespace enthält alle `entryPoint`\-Elemente, die einer Office\-Projektmappe zugeordnet sind.  
  
## Syntax  
  
```  
<entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
</entryPoints>  
```  
  
## Elemente und Attribute  
 Das `entryPoints`\-Element ist erforderlich und befindet sich im `vstav3` \-Namespace. In einem Anwendungsmanifest ist für jede Office\-Projektmappe ein `entryPoints`\-Element definiert. Wenn Sie z. B. in einer Bereitstellung mit mehreren Projekten drei Office\-Projektmappen bereitstellen, befinden sich im Anwendungsmanifest drei `entryPoints`\-Elemente.  
  
 Das `entryPoints`\-Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|ID|Ist für eine Bereitstellung mit mehreren Projekten erforderlich. Der Name der Office\-Projektmappe. Die ID darf kein Gleichheitszeichen \(\=\) enthalten.|  
  
 `entryPoints` hat die folgenden Elemente:  
  
### entryPoint  
 Erforderlich. Die Rolle des `entryPoint`\-Elements im `vstav3` \-Namespace ist im [&#60;entryPoint&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md) definiert.  
  
## Beispiel für die Anpassung auf Dokumentebene  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `entryPoints`\-Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Projektmappe auf Dokumentebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints>  
```  
  
## Beispiel für ein VSTO\-Add\-In  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `entryPoints`\-Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints>  
```  
  
## Beispiel für eine Bereitstellung mit mehreren Projekten  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `entryPoints`\-Element in einem Anwendungsmanifest für eine Bereitstellung mit mehreren Projekten. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPoints id="ContosoExcel"> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> <vstav3:entryPoints id="ContosoOutlook"> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  