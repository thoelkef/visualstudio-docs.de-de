---
title: '&lt;Assembly&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9d72eafb03f22a01d22894bb887085648c324e3
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080632"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;Assembly&gt; -Element (ClickOnce-Bereitstellung)
Das Element der obersten Ebene für das Bereitstellungsmanifest.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `assembly` -Element ist das Stammelement und ist erforderlich. Das erste darin enthaltene Element muss ein `assemblyIdentity` Element. Manifestelemente muss in den folgenden Namespaces: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2`, und `http://www.w3.org/2000/09/xmldsig#`. Untergeordnete Elemente der Assembly muss auch in diesen Namespaces, die durch Vererbung oder durch markieren.  
  
 Die `assembly` Element weist das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`manifestVersion`|Erforderlich. Dieses Attribut muss festgelegt werden, um `1.0`.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht eine `assembly` Element in einem-Bereitstellungsmanifest für eine Anwendung mithilfe von bereitgestellt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels für die [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md) Thema.  
  
```xml  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)   
 [\<Assembly >-Element](../deployment/assembly-element-clickonce-application.md)