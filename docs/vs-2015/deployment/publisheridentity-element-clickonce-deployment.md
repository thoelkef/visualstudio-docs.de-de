---
title: '&lt;PublisherIdentity&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4c11e8ed9a3e0b4341708fc849462fbc476dc395
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515823"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;PublisherIdentity&gt; -Element (ClickOnce-Bereitstellung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [ &lt;PublisherIdentity&gt; -Element (ClickOnce-Bereitstellung)](https://docs.microsoft.com/visualstudio/deployment/publisheridentity-element-clickonce-deployment).  
  
Enthält Informationen zum Herausgeber, der dieses Bereitstellungsmanifest signiert hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `publisherIdentity` Element für signierte Manifeste erforderlich ist. Die folgende Tabelle zeigt die Attribute an, dass die `publisherIdentity` Element unterstützt.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`name`|Erforderlich. Beschreibt die Identität der Partei, die diese Anwendung veröffentlicht.|  
|`issuerKeyHash`|Erforderlich. Enthält den SHA-1-Hash des öffentlichen Schlüssels des Zertifikatausstellers.|  
  
#### <a name="parameters"></a>Parameter  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
  
## <a name="exceptions"></a>Ausnahmen  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="subhead"></a>Untertitel



