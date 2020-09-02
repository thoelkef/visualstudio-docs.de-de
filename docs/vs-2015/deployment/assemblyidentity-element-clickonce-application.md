---
title: '&lt;AssemblyIdentity- &gt; Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
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
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bde22809af69071f5484e25717a5aea7d78a603
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428533"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;AssemblyIdentity- &gt; Element (ClickOnce-Anwendung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifiziert die in einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung bereitgestellte Anwendung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `assemblyIdentity`-Element ist erforderlich. Sie enthält keine untergeordneten Elemente und weist die folgenden Attribute auf.  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Identifiziert den Namen der Anwendung.<br /><br /> Wenn `Name` Sonderzeichen (z. b. einfache oder doppelte Anführungszeichen) enthält, kann die Anwendung möglicherweise nicht aktiviert werden.|  
|`Version`|Erforderlich. Gibt die Versionsnummer der Anwendung im folgenden Format an: `major.minor.build.revision`|  
|`publicKeyToken`|Optional. Gibt eine hexadezimale Zeichenfolge mit 16 Zeichen an, die die letzten 8 Bytes des `SHA-1` Hashwerts des öffentlichen Schlüssels darstellt, unter dem die Anwendung oder Assembly signiert ist. Der öffentliche Schlüssel, der zum Signieren des Katalogs verwendet wird, muss 2048 Bit oder größer sein.<br /><br /> Das Signieren einer Assembly wird zwar empfohlen, ist aber optional, aber dieses Attribut ist erforderlich. Wenn eine Assembly nicht signiert ist, sollten Sie einen Wert aus einer selbst signierten Assembly kopieren oder einen "Dummy"-Wert aller Nullen verwenden.|  
|`processorArchitecture`|Erforderlich. Gibt den Prozessor an. Gültige Werte sind `msil` für alle Prozessoren, `x86` für 32-Bit-Windows, `IA64` für 64-Bit-Windows und `Itanium` für Intel 64-Bit-Itanium-Prozessoren.|  
|`language`|Erforderlich. Gibt die zwei teiligen Sprachcodes (z. b `en-US` .) der Assembly an. Dieses Element befindet sich im- `asmv2` Namespace. Wenn nicht angegeben, ist der Standardwert `neutral` .|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>BESCHREIBUNG  
 Das folgende Codebeispiel veranschaulicht ein- `assemblyIdentity` Element in einem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungs Manifest. Dieses Codebeispiel ist Teil eines größeren Beispiels, das im [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)bereitgestellt wird.  
  
### <a name="code"></a>Code  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity>-Element](../deployment/assemblyidentity-element-clickonce-deployment.md)
