---
title: "&lt;assembly&gt; Element (ClickOnce Application) | Microsoft Docs"
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
  - "<assembly> element [ClickOnce application manifest]"
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# &lt;assembly&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Element der obersten Ebene für das Anwendungsmanifest.  
  
## Syntax  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## Elemente und Attribute  
 Das `assembly`\-Element stellt das Stammelement dar und ist erforderlich.  Das erste darin enthaltene Element muss ein `assemblyIdentity`\-Element sein.  Die Manifestelemente müssen in einem der folgenden Namespaces vorhanden sein:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Untergeordnete Elemente der Assembly müssen ebenfalls in diesen Namespaces vorhanden sein, entweder durch Vererbung oder durch Tagging.  
  
 Das `assembly`\-Element verfügt über das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`manifestVersion`|Erforderlich.  Das `manifestVersion`\-Attribut muss auf `1.0` festgelegt werden.|  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein `assembly`\-Element in einem Anwendungsmanifest für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung veranschaulicht.  Dieses Codebeispiel ist Teil eines umfangreichen Beispiels, das im Thema [ClickOnce\-Anwendungsmanifest](../deployment/clickonce-application-manifest.md) bereitgestellt wird.  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## Siehe auch  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<assembly\> Element](../deployment/assembly-element-clickonce-deployment.md)