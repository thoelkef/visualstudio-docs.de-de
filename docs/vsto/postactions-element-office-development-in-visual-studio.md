---
title: "&lt;postActions&gt;-Element (Office-Entwicklung in Visual Studio) | Microsoft Docs"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <postActions>-Element"
  - "postActions-Element"
  - "<postActions>-Element"
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;postActions&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `postActions`\-Element des `vstav3` \-Namespace enthält alle `postAction`\-Elemente, die Aktionen nach der Bereitstellung beschreiben, die ausgeführt werden, nachdem Office\-Projektmappen installiert sind.  
  
## Syntax  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## Elemente und Attribute  
 Das `postActions`\-Element ist optional und befindet sich im `vstav3` \-Namespace. In einem Anwendungsmanifest ist nur ein `postActions`\-Element definiert.  
  
 Das `postActions`\-Element hat keine Attribute.  
  
 `postActions` weist das folgende Element auf:  
  
### postAction  
 Optional. Die Rolle des `postAction`\-Elements im `vstav3` \-Namespace ist im [&#60;postAction&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md) definiert.  
  
## Beispiel für eine Aktion nach der Bereitstellung  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `postActions`\-Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Office\-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:postActions> <vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction> </vstav3:postActions>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  