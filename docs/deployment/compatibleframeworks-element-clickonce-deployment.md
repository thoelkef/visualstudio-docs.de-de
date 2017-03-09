---
title: "&lt;compatibleFrameworks&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<compatibleFrameworks> element [ClickOnce deployment manifest]"
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;compatibleFrameworks&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifiziert die Versionen von .NET Framework, in denen die Anwendung installiert und ausgeführt werden kann.  
  
> [!NOTE]
>  [MageUI.exe](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md) unterstützt nicht das `compatibleFrameworks`\-Element, sofern es ein Anwendungsmanifest speichert, das bereits mit einem Zertifikat mit [MageUI.exe](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)signiert wurde.  Stattdessen müssen Sie [Mage.exe](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)verwenden.  
  
## Syntax  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## Elemente und Attribute  
 Das `compatibleFrameworks`\-Element ist für Bereitstellungsmanifeste erforderlich, die für die von [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] oder höher bereitgestellte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Laufzeit vorgesehen sind.  Das `compatibleFrameworks`\-Element enthält ein oder mehrere `framework`\-Elemente, die die .NET Framework\-Versionen angeben, in denen die Anwendung ausgeführt werden kann.  Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Laufzeit führt die Anwendung im ersten verfügbaren `framework` in dieser Liste aus.  
  
 In der folgenden Tabelle werden die Attribute aufgeführt, die vom `compatibleFrameworks`\-Element unterstützt werden.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`S` `upportUrl`|Optional.  Gibt eine URL an, von der die bevorzugte kompatible .NET Framework\-Version heruntergeladen werden kann.|  
  
## framework  
 Erforderlich.  In der folgenden Tabelle werden die Attribute aufgeführt, die vom `framework`\-Element unterstützt werden.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`targetVersion`|Erforderlich.  Gibt die Versionsnummer des .NET Framework\-Ziels an.|  
|`profile`|Erforderlich.  Gibt das Profil des .NET Framework\-Ziels an.|  
|`supportedRuntime`|Erforderlich.  Gibt die Versionsnummer der Laufzeit an, die dem .NET Framework\-Ziel zugeordnet ist.|  
  
## Hinweise  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein `compatibleFrameworks`\-Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsmanifest veranschaulicht.  Diese Bereitstellung kann in [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] ausgeführt werden.  Sie kann auch in [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] ausgeführt werden, da es sich um eine Obermenge von [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] handelt.  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## Siehe auch  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)