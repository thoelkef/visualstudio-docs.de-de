---
title: "&lt;assembly&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assembly> element [ClickOnce deployment manifest]"
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;assembly&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Element der obersten Ebene für das Bereitstellungsmanifest.  
  
## Syntax  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## Elemente und Attribute  
 Das `assembly`\-Element stellt das Stammelement dar und ist erforderlich.  Das erste darin enthaltene Element muss ein `assemblyIdentity`\-Element sein.  Die Manifestelemente müssen in den folgenden Namespaces vorhanden sein: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2` und `http://www.w3.org/2000/09/xmldsig#`.  Untergeordnete Elemente der Assembly müssen ebenfalls in diesen Namespaces vorhanden sein, entweder durch Vererbung oder durch Tagging.  
  
 Das `assembly`\-Element verfügt über das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`manifestVersion`|Erforderlich.  Das Attribut muss auf `1.0` festgelegt werden.|  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein `assembly`\-Element in einem Bereitstellungsmanifest für eine mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitgestellte Anwendung veranschaulicht.  Dieses Codebeispiel ist Teil eines umfangreichen Beispiels, das für das Thema [ClickOnce\-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md) bereitgestellt wird.  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## Siehe auch  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly\> Element](../deployment/assembly-element-clickonce-application.md)