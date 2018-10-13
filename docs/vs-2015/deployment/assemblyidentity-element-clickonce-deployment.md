---
title: '&lt;AssemblyIdentity&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 157ad7bb43ae7eb164d7c58edb79f51df3da5dcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195105"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;AssemblyIdentity&gt; -Element (ClickOnce-Bereitstellung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifiziert die primäre Assembly von der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung.  
  
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
 Die `assemblyIdentity` Element ist erforderlich. Es enthält keine untergeordneten Elemente und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`name`|Erforderlich. Gibt den lesbaren Namen der Bereitstellung um zu Informationszwecken.<br /><br /> Wenn `name` Sonderzeichen enthält, z. B. einfache oder doppelte Anführungszeichen, die Anwendung möglicherweise nicht aktiviert.|  
|`version`|Erforderlich. Gibt die Versionsnummer der Assembly im folgenden Format an: `major.minor.build.revision`.<br /><br /> Dieser Wert muss in einem aktualisierten Manifest zum Auslösen eines Anwendungsupdates erhöht werden.|  
|`publicKeyToken`|Erforderlich. Gibt eine hexadezimale Zeichenfolge von 16 Zeichen, die die letzten 8 Bytes des SHA-1-Hash-Wert des öffentlichen Schlüssels darstellt, unter dem das Bereitstellungsmanifest signiert wurde. Der öffentliche Schlüssel, der zum Signieren verwendet wird, muss 2048 Bits betragen.<br /><br /> Obwohl das Signieren einer Assembly empfohlen aber optional ist, ist dieses Attribut erforderlich. Wenn eine Assembly nicht signiert ist, sollten Sie Kopieren eines Werts aus einem selbst signierten Assembly oder verwenden Sie den Wert "dummy" nur Nullen.|  
|`processorArchitecture`|Erforderlich. Gibt den Prozessor. Gültige Werte sind `msil` für alle Prozessoren `x86` für 32-Bit-Windows `IA64` für 64-Bit-Windows und `Itanium` für Intel 64-Bit-Itaniumprozessoren gegeben.|  
|`type`|Erforderlich. Für die Kompatibilität mit Windows-Seite-an-Seite-installationstechnologie. Der einzige zulässige Wert ist `win32`.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht ein `assemblyIdentity` Element in einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungsmanifest. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels für die [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md) Thema.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)   
 [\<AssemblyIdentity >-Element](../deployment/assemblyidentity-element-clickonce-application.md)



