---
title: '&lt;Assembly&gt; Element (ClickOnce-Anwendung) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: c94d70f2be28a6a420d683335c99ee0466a52114
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;Assembly&gt; Element (ClickOnce-Anwendung)
Das Element der obersten Ebene für das Anwendungsmanifest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `assembly` Element ist das Stammelement und ist erforderlich. Das erste darin enthaltene Element muss ein `assemblyIdentity` Element. Die Elemente von Manifesten muss sich in einem der folgenden Namespaces:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Untergeordnete Elemente der Assembly muss auch in diesen Namespaces, durch Vererbung oder durch tagging.  
  
 Die `assembly` Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`manifestVersion`|Erforderlich. Die `manifestVersion` Attribut muss festgelegt werden, um `1.0`.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht eine `assembly` Element in einem Anwendungsmanifest für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)   
 [\<Assembly >-Element](../deployment/assembly-element-clickonce-deployment.md)