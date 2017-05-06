---
title: "&lt;postActionData&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "<postActionData>-Element"
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <postActionData>-Element"
  - "postActionData-Element"
ms.assetid: e36cbd64-fd27-4413-b293-cf5546fbdfaf
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;postActionData&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `postActionData`\-Element des `vstav3` \-Namespace gibt die Daten an, die jeder Aktion nach der Bereitstellung zugeordnet sind, die nach der Installation von Office\-Projektmappen ausgeführt wird.  
  
## Syntax  
  
```  
<postActionData>  
</postActionData>  
```  
  
## Elemente und Attribute  
 Das `postActionData`\-Element ist optional und befindet sich im `vstav3` \-Namespace. In einem Anwendungsmanifest ist für jede Aktion nach der Bereitstellung ein `postActionData`\-Element definiert.  
  
 Das `postActions`\-Element weist keine Attribute auf.  
  
 `postActions` hat keine untergeordneten Elemente.  
  
## Beispiel für eine Aktion nach der Bereitstellung  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `postAction`\-Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellte Office\-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:postActionData> data in any format </vstav3:postActionData>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  