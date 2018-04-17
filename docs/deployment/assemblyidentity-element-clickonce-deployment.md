---
title: '&lt;AssemblyIdentity&gt; Element (ClickOnce-Bereitstellung) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 79ce08b434e5f26085b4f3f2285f7ae34bfb2d11
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;AssemblyIdentity&gt; Element (ClickOnce-Bereitstellung)
Identifiziert die primäre Assembly von der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  
  
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
|`name`|Erforderlich. Identifiziert den lesbaren Namen der Bereitstellung für Informationszwecke an.<br /><br /> Wenn `name` Sonderzeichen enthält, z. B. einfache oder doppelte Anführungszeichen, die Anwendung möglicherweise nicht aktiviert.|  
|`version`|Erforderlich. Gibt die Versionsnummer der Assembly im folgenden Format an: `major.minor.build.revision`.<br /><br /> Dieser Wert muss in einem aktualisierten Manifest ein Anwendungsupdate auslösen erhöht.|  
|`publicKeyToken`|Erforderlich. Gibt eine hexadezimale Zeichenfolge von 16-Zeichen, die die letzten 8 Bytes des SHA-1-Hash-Wert des öffentlichen Schlüssels darstellt, unter dem das Bereitstellungsmanifest signiert wurde. Die öffentliche Schlüssel, der zum Signieren verwendet wird, muss 2048 Bits betragen.<br /><br /> Obwohl das Signieren einer Assembly wird empfohlen, aber dies ist optional, dieses Attribut ist erforderlich. Wenn eine Assembly nicht signiert ist, sollten Sie Kopieren eines Werts aus einem selbst signierten Assembly oder verwenden Sie den Wert "dummy" Nullen.|  
|`processorArchitecture`|Erforderlich. Gibt den Prozessor. Gültige Werte sind `msil` für alle Prozessoren `x86` für 32-Bit-Windows `IA64` für 64-Bit-Windows und `Itanium` für Intel 64-Bit-Itanium-Prozessoren.|  
|`type`|Erforderlich. Um die Kompatibilität mit Windows-Seite-an-Seite-Installationsverfahrens. Der einzige zulässige Wert ist `win32`.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht eine `assemblyIdentity` Element in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels für die [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md) Thema.  
  
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