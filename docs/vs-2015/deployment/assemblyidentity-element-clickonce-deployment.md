---
title: '&lt;AssemblyIdentity- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfc2ff97a2eb465fe7306ebe368a20e2a7fd8638
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155729"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;AssemblyIdentity- &gt; Element (ClickOnce-Bereitstellung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifiziert die primäre Assembly der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `assemblyIdentity`-Element ist erforderlich. Sie enthält keine untergeordneten Elemente und weist die folgenden Attribute auf.  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`name`|Erforderlich. Identifiziert den lesbaren Namen der Bereitstellung zu Informationszwecken.<br /><br /> Wenn `name` Sonderzeichen (z. b. einfache oder doppelte Anführungszeichen) enthält, kann die Anwendung möglicherweise nicht aktiviert werden.|  
|`version`|Erforderlich. Gibt die Versionsnummer der Assembly im folgenden Format an: `major.minor.build.revision` .<br /><br /> Dieser Wert muss in einem aktualisierten Manifest inkrementiert werden, um ein Anwendungs Update zu initiieren.|  
|`publicKeyToken`|Erforderlich. Gibt eine hexadezimale Zeichenfolge mit 16 Zeichen an, die die letzten 8 Bytes des SHA-1-Hashwerts des öffentlichen Schlüssels darstellt, unter dem das Bereitstellungs Manifest signiert ist. Der öffentliche Schlüssel, der zum Signieren verwendet wird, muss 2048 Bit oder größer sein.<br /><br /> Das Signieren einer Assembly wird zwar empfohlen, ist aber optional, aber dieses Attribut ist erforderlich. Wenn eine Assembly nicht signiert ist, sollten Sie einen Wert aus einer selbst signierten Assembly kopieren oder einen "Dummy"-Wert aller Nullen verwenden.|  
|`processorArchitecture`|Erforderlich. Gibt den Prozessor an. Gültige Werte sind `msil` für alle Prozessoren, `x86` für 32-Bit-Windows, `IA64` für 64-Bit-Windows und `Itanium` für Intel 64-Bit-Itanium-Prozessoren.|  
|`type`|Erforderlich. Aus Gründen der Kompatibilität mit der parallelen Installation von Windows. Der einzige zulässige Wert ist `win32` .|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht ein- `assemblyIdentity` Element in einem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungs Manifest. Dieses Codebeispiel ist Teil eines größeren Beispiels, das für das [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md) -Thema bereitgestellt wird.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity>-Element](../deployment/assemblyidentity-element-clickonce-application.md)
