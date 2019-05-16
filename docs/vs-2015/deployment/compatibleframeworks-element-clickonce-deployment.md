---
title: '&lt;CompatibleFrameworks&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef54062bd74c9395e187503dd12db1c0cd70d822
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675416"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;CompatibleFrameworks&gt; -Element (ClickOnce-Bereitstellung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifiziert die Versionen von .NET Framework, mit denen diese Anwendung installiert und ausgeführt werden kann.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) unterstützt nicht die `compatibleFrameworks` -Element, wenn ein Anwendungsmanifest, das Speichern von wurde bereits mit einem Zertifikat signiert [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Stattdessen müssen Sie [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) verwenden.  
  
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
 Die `compatibleFrameworks` Element ist erforderlich, für die Bereitstellungsmanifeste der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Runtime gebotenen [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] oder höher. Die `compatibleFrameworks` Element enthält ein oder mehrere `framework` Elemente, die .NET Framework-Versionen angeben, auf denen diese Anwendung ausgeführt werden kann. Die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Runtime wird die Anwendung ausgeführt, auf dem ersten verfügbaren `framework` in dieser Liste.  
  
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
 Das folgende Codebeispiel zeigt eine `compatibleFrameworks` Element in einem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungsmanifest. Diese Bereitstellung ausgeführt werden kann, auf die [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)]. Es kann auch ausgeführt, auf die [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , da es sich um eine Obermenge ist die [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)].  
  
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
