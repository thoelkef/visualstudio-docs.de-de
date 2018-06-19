---
title: '&lt;CompatibleFrameworks&gt; Element (ClickOnce-Bereitstellung) | Microsoft Docs'
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
ms.openlocfilehash: d406ecf058bf1c570b57ed8f50815cc3d9378cbe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31560777"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;CompatibleFrameworks&gt; Element (ClickOnce-Bereitstellung)
Identifiziert die Versionen von .NET Framework, mit denen diese Anwendung installiert und ausgeführt werden kann.  
  
> [!NOTE]
>  [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) unterstützt nicht die `compatibleFrameworks` -Element, wenn ein Anwendungsmanifest speichern, die bereits mit einem Zertifikat signiert wurde [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Stattdessen müssen Sie [Mage.exe](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) verwenden.  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `compatibleFrameworks` Element ist erforderlich, für die Bereitstellungsmanifeste der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Runtime gebotenen [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] oder höher. Die `compatibleFrameworks` Element enthält eine oder mehrere `framework` Elemente, die .NET Framework-Versionen angeben, auf denen diese Anwendung ausgeführt werden kann. Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Runtime wird die Anwendung auszuführen, auf dem ersten verfügbaren `framework` in dieser Liste.  
  
 In der folgenden Tabelle werden die Attribute aufgeführt, die die `compatibleFrameworks` Element unterstützt.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`S` `upportUrl`|Dies ist optional. Gibt eine URL, in dem die bevorzugte kompatible .NET Framework-Version heruntergeladen werden kann.|  
  
## <a name="framework"></a>Framework  
 Erforderlich. In der folgenden Tabelle werden die Attribute aufgelistet, die die `framework` Element unterstützt.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`targetVersion`|Erforderlich. Gibt die Versionsnummer von .NET Framework-Zielversion.|  
|`profile`|Erforderlich. Gibt das Profil des .NET Framework-Zielversion.|  
|`supportedRuntime`|Erforderlich. Gibt die Versionsnummer der Common Language Runtime das Ziel-.NET Framework zugeordnet.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt eine `compatibleFrameworks` Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest. Diese Bereitstellung ausgeführt werden kann, auf die [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Es kann auch ausgeführt, auf die [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] ist eine Obermenge von der [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)