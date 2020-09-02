---
title: '&lt;compatibleframe- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675416"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleframe- &gt; Element (ClickOnce-Bereitstellung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifiziert die Versionen von .NET Framework, mit denen diese Anwendung installiert und ausgeführt werden kann.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) unterstützt das- `compatibleFrameworks` Element nicht, wenn ein Anwendungs Manifest gespeichert wird, das bereits mit einem Zertifikat signiert wurde, das [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)verwendet. Stattdessen müssen Sie [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) verwenden.  
  
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
 Das- `compatibleFrameworks` Element ist für Bereitstellungs Manifeste erforderlich, die auf die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] von oder höher bereitgestellte Runtime abzielen [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] . Das- `compatibleFrameworks` Element enthält ein oder mehrere- `framework` Elemente, die die .NET Framework Versionen angeben, auf denen diese Anwendung ausgeführt werden kann. Die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Laufzeit führt die Anwendung auf dem ersten aus, der `framework` in dieser Liste verfügbar ist.  
  
 In der folgenden Tabelle werden die Attribute aufgelistet, die das- `compatibleFrameworks` Element unterstützt.  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|`S` `upportUrl`|Optional. Gibt eine URL an, unter der die bevorzugte kompatible .NET Framework Version heruntergeladen werden kann.|  
  
## <a name="framework"></a>Framework  
 Erforderlich. In der folgenden Tabelle werden die Attribute aufgelistet, die das- `framework` Element unterstützt.  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|`targetVersion`|Erforderlich. Gibt die Versionsnummer des Ziel .NET Framework an.|  
|`profile`|Erforderlich. Gibt das Profil des Ziel .NET Framework an.|  
|`supportedRuntime`|Erforderlich. Gibt die Versionsnummer der Laufzeit an, die der Ziel .NET Framework zugeordnet ist.|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt ein- `compatibleFrameworks` Element in einem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungs Manifest. Diese Bereitstellung kann auf dem ausgeführt werden [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] . Sie kann auch auf dem ausgeführt werden, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] da es sich um eine übergeordnete Gruppe von handelt [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)
