---
title: '&lt;Beschreibung&gt; Element (ClickOnce-Bereitstellung) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: f5045f9203d5413efdd6d192d2667e94d0119220
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Beschreibung&gt; Element (ClickOnce-Bereitstellung)
Identifiziert Anwendungsinformationen, die zum Erstellen eines Shell-Eintrags verwendet und ein **Software** Element in der Systemsteuerung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `description`-Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v1`-Namespace. Es enthält keine untergeordneten Elemente und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`publisher`|Erforderlich. Identifiziert den Firmennamen, die für die Platzierung von Symbol in Windows verwendet **starten** Menü und die **Software** Systemsteuerungselement, wenn die Bereitstellung für die Installation konfiguriert wird.|  
|`product`|Erforderlich. Den vollständige Produktname wird identifiziert. Als Titel für das Symbol, das in Windows verwendeten **starten** Menü.|  
|`suiteName`|Dies ist optional. Identifiziert einen Unterordner innerhalb der `publisher` Ordner in Windows **starten** Menü.|  
|`supportUrl`|Dies ist optional. Gibt eine Support-URL, die in angezeigt wird der **Software** Element in der Systemsteuerung. Eine Verknüpfung zu dieser URL ist auch für die anwendungsunterstützung in Windows erstellt **starten** Menü, wenn die Bereitstellung für die Installation konfiguriert wird.|  
  
## <a name="remarks"></a>Hinweise  
 Das Description-Element ist in allen Bereitstellungskonfigurationen erforderlich.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht eine `description` Element in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels für die [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md) Thema.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)