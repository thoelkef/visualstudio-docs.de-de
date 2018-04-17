---
title: '&lt;AssemblyIdentity&gt; Element (ClickOnce-Anwendung) | Microsoft Docs'
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
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 86a9aedcd3f21d4dbc1cc4f09106421542b188f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;AssemblyIdentity&gt; Element (ClickOnce-Anwendung)
Identifiziert die bereitgestellte Anwendung eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung.  
  
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
 Die `assemblyIdentity` Element ist erforderlich. Es enthält keine untergeordneten Elemente und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Identifiziert den Namen der Anwendung.<br /><br /> Wenn `Name` Sonderzeichen enthält, z. B. einfache oder doppelte Anführungszeichen, die Anwendung möglicherweise nicht aktiviert.|  
|`Version`|Erforderlich. Gibt die Versionsnummer der Anwendung im folgenden Format an: `major.minor.build.revision`|  
|`publicKeyToken`|Dies ist optional. Gibt eine hexadezimale Zeichenfolge von 16-Zeichen, die die letzten 8 Bytes des darstellt der `SHA-1` der Hashwert des öffentlichen Schlüssels unter dem die Anwendung oder Assembly signiert ist. Die öffentliche Schlüssel, der zum Signieren des Katalogs verwendet wird, muss 2048 Bits betragen.<br /><br /> Obwohl das Signieren einer Assembly wird empfohlen, aber dies ist optional, dieses Attribut ist erforderlich. Wenn eine Assembly nicht signiert ist, sollten Sie Kopieren eines Werts aus einem selbst signierten Assembly oder verwenden Sie den Wert "dummy" Nullen.|  
|`processorArchitecture`|Erforderlich. Gibt den Prozessor. Gültige Werte sind `msil` für alle Prozessoren `x86` für 32-Bit-Windows `IA64` für 64-Bit-Windows und `Itanium` für Intel 64-Bit-Itanium-Prozessoren.|  
|`language`|Erforderlich. Identifiziert die zweiteiligen Sprachcodes (z. B. `en-US`) der Assembly. Dieses Element ist der `asmv2` Namespace. Wenn nicht angegeben, wird standardmäßig `neutral`.|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht eine `assemblyIdentity` Element in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifest. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md).  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)   
 [\<AssemblyIdentity >-Element](../deployment/assemblyidentity-element-clickonce-deployment.md)