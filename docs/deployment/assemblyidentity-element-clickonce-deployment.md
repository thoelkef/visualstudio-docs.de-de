---
title: "&lt;assemblyIdentity&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assemblyIdentity> element [ClickOnce deployment manifest]"
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;assemblyIdentity&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifiziert die primäre Assembly der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung.  
  
## Syntax  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## Elemente und Attribute  
 Das `assemblyIdentity`\-Element ist erforderlich.  Es enthält keine untergeordneten Elemente und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`name`|Erforderlich.  Identifiziert den lesbaren Namen der Bereitstellung für Informationszwecke.<br /><br /> Wenn `name` Sonderzeichen, z. B. einzelne oder doppelte Anführungszeichen, enthält, wird die Anwendung möglicherweise nicht aktiviert.|  
|`version`|Erforderlich.  Gibt die Versionsnummer der Assembly im folgenden Format an: `Hauptversion.Nebenversion.Build.Revision`.<br /><br /> Dieser Wert muss in einem aktualisierten Manifest inkrementiert werden, um ein Anwendungsupdate auszulösen.|  
|`publicKeyToken`|Erforderlich.  Gibt eine aus 16 Zeichen bestehende hexadezimale Zeichenfolge an, die die letzten 8 Bytes des SHA\-1\-Hashwerts des öffentlichen Schlüssels darstellt, der zum Signieren des Bereitstellungsmanifests verwendet wird.  Der öffentliche Schlüssel, der zum Signieren verwendet wird, muss mindestens 2048 Bits groß sein.<br /><br /> Obwohl das Signieren einer Assembly optional empfohlen wird, ist dieses Attribut erforderlich.  Wenn eine Assembly nicht signiert ist, sollten Sie den Wert einer selbst signierten Assembly kopieren oder einen ausschließlich aus 0\-Werten bestehenden "Dummy"\-Wert verwenden.|  
|`processorArchitecture`|Erforderlich.  Gibt den Prozessor an.  Die gültigen Werte sind `msil` für alle Prozessoren, `x86` für 32\-Bit\-Windows, `IA64` für 64\-Bit\-Windows und `Itanium` für Intel 64\-Bit\-Itanium\-Prozessoren.|  
|`type`|Erforderlich.  Für die Kompatibilität mit der Windows\-Technologie für parallele Installationen.  Der einzig zulässige Wert ist `win32`.|  
  
## Hinweise  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein `assemblyIdentity`\-Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsmanifest veranschaulicht.  Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels, das für das Thema [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md) bereitgestellt wird.  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## Siehe auch  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-application.md)