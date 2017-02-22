---
title: "&lt;assemblyIdentity&gt; Element (ClickOnce Application) | Microsoft Docs"
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
  - "<assemblyIdentity> element [ClickOnce application manifest]"
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;assemblyIdentity&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifiziert die mit einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung bereitgestellte Anwendung.  
  
## Syntax  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## Elemente und Attribute  
 Das `assemblyIdentity`\-Element ist erforderlich.  Es enthält keine untergeordneten Elemente und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Name`|Erforderlich.  Identifiziert den Namen der Anwendung.<br /><br /> Wenn `Name` Sonderzeichen, z. B. einzelne oder doppelte Anführungszeichen, enthält, wird die Anwendung möglicherweise nicht aktiviert.|  
|`Version`|Erforderlich.  Gibt die Versionsnummer der Anwendung im folgenden Format an: `major.minor.build.revision`|  
|`publicKeyToken`|Optional.  Gibt eine aus 16 Zeichen bestehende hexadezimale Zeichenfolge an, die die letzten 8 Bytes des `SHA-1`\-Hashwerts des öffentlichen Schlüssels darstellt, der zum Signieren der Anwendung oder der Assembly verwendet wird.  Der öffentliche Schlüssel, der zum Signieren des Katalogs verwendet wird, muss mindestens 2048 Bits groß sein.<br /><br /> Obwohl das Signieren einer Assembly optional empfohlen wird, ist dieses Attribut erforderlich.  Wenn eine Assembly nicht signiert ist, sollten Sie den Wert einer selbst signierten Assembly kopieren oder einen ausschließlich aus 0\-Werten bestehenden "Dummy"\-Wert verwenden.|  
|`processorArchitecture`|Erforderlich.  Gibt den Prozessor an.  Die gültigen Werte sind `msil` für alle Prozessoren, `x86` für 32\-Bit\-Windows, `IA64` für 64\-Bit\-Windows und `Itanium` für Intel 64\-Bit\-Itanium\-Prozessoren.|  
|`language`|Erforderlich.  Identifiziert die zweiteiligen Sprachcodes \(z. B. `en-US`\) der Assembly.  Dieses Element ist im `asmv2`\-Namespace vorhanden.  Falls nicht angegeben, stellt `neutral` den Standard dar.|  
  
## Beispiele  
  
### Beschreibung  
 Im folgenden Codebeispiel wird ein `assemblyIdentity`\-Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsmanifest veranschaulicht.  Dieses Codebeispiel ist Teil eines umfangreichen Beispiels, das im Thema [ClickOnce\-Anwendungsmanifest](../deployment/clickonce-application-manifest.md) bereitgestellt wird.  
  
### Code  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## Siehe auch  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-deployment.md)