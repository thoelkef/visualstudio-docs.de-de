---
title: '&lt;CompatibleFrameworks&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44329fc4c2ec5e9f2f8352d69ea487f23cbe3c5a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077684"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;CompatibleFrameworks&gt; -Element (ClickOnce-Bereitstellung)
Identifiziert die Versionen von .NET Framework, mit denen diese Anwendung installiert und ausgeführt werden kann.  
  
> [!NOTE]
>  [*MageUI.exe* ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) unterstützt nicht die `compatibleFrameworks` -Element, wenn ein Anwendungsmanifest, das Speichern von wurde bereits mit einem Zertifikat signiert [ *MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Sie müssen stattdessen [ *Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `compatibleFrameworks` Element ist erforderlich, für die Bereitstellungsmanifeste der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Runtime gebotenen [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] oder höher. Die `compatibleFrameworks` Element enthält ein oder mehrere `framework` Elemente, die .NET Framework-Versionen angeben, auf denen diese Anwendung ausgeführt werden kann. Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Runtime wird die Anwendung ausgeführt, auf dem ersten verfügbaren `framework` in dieser Liste.  
  
 In der folgende Tabelle werden die Attribute aufgeführt, die die `compatibleFrameworks` Element unterstützt.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`S` `upportUrl`|Dies ist optional. Gibt eine URL, in denen die bevorzugte kompatible .NET Framework-Version heruntergeladen werden kann.|  
  
## <a name="framework"></a>Framework  
 Erforderlich. Die folgende Tabelle enthält die Attribute, die die `framework` Element unterstützt.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`targetVersion`|Erforderlich. Gibt die Versionsnummer des .NET Framework-Ziel an.|  
|`profile`|Erforderlich. Gibt das Profil von .NET Framework-Ziel.|  
|`supportedRuntime`|Erforderlich. Gibt die Versionsnummer der Laufzeit mit dem Ziel .NET Framework verknüpft ist.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt eine `compatibleFrameworks` Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest. Diese Bereitstellung ausgeführt werden kann, auf die [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Es kann auch ausgeführt, auf die [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , da es sich um eine Obermenge ist die [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
```xml  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)