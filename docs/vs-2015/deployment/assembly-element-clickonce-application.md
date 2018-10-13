---
title: '&lt;Assembly&gt; -Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
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
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 44437c0ff78c5f957a0d774530e8911513ba0fd6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191775"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;Assembly&gt; -Element (ClickOnce-Anwendung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Element der obersten Ebene für das Anwendungsmanifest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `assembly` -Element ist das Stammelement und ist erforderlich. Das erste darin enthaltene Element muss ein `assemblyIdentity` Element. Die Elemente von Manifesten muss sich in einem der folgenden Namespaces:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Untergeordnete Elemente der Assembly muss auch in diesen Namespaces, die durch Vererbung oder durch markieren.  
  
 Das `assembly` -Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`manifestVersion`|Erforderlich. Die `manifestVersion` Attribut muss festgelegt werden, um `1.0`.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht eine `assembly` Element in einem Anwendungsmanifest für eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md).  
  
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
 [ClickOnce Application Manifest (ClickOnce-Anwendungsmanifest)](../deployment/clickonce-application-manifest.md)   
 [\<Assembly >-Element](../deployment/assembly-element-clickonce-deployment.md)



