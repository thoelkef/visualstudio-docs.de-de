---
title: "&lt;postAction&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <postAction>-Element"
  - "<postAction>-Element"
  - "postAction-Element"
ms.assetid: a047e2e2-9732-4140-b8bd-bc5bd1b84291
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# &lt;postAction&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `postAction`\-Element des `vstav3` \-Namespace enthält alle `entrypoint`\-Elemente und alle `postActionData`\-Elemente, die Aktionen nach der Bereitstellung zugeordnet sind, die ausgeführt werden, sobald Office\-Projektmappen installiert sind.  
  
## Syntax  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## Elemente und Attribute  
 Das `postAction`\-Element ist optional und befindet sich im `vstav3` \-Namespace. In einem Anwendungsmanifest ist für jede Aktion nach der Bereitstellung ein `postAction`\-Element definiert.  
  
 Das `postAction`\-Element hat keine Attribute.  
  
 `postAction` hat die folgenden Elemente:  
  
### entryPoint  
 Optional. Die Rolle des `entryPoint`\-Elements im `vstav3` \-Namespace ist im [&#60;entryPoints&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md) definiert.  
  
### postActionData  
 Optional. Die Rolle des `postActionData`\-Elements im `vstav3` \-Namespace ist im [&#60;postActionData&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md) definiert.  
  
## Beispiel für eine Aktion nach der Bereitstellung  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `postAction`\-Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Office\-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  