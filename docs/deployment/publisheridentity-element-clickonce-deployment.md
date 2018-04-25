---
title: '&lt;PublisherIdentity&gt; Element (ClickOnce-Bereitstellung) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ad10cae4ebd3aee6b65ad408ea3a3df3f82fd02
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;PublisherIdentity&gt; Element (ClickOnce-Bereitstellung)
Enthält Informationen zum Herausgeber, der dieses Bereitstellungsmanifest signiert hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `publisherIdentity` Element für signierte Manifeste erforderlich ist. Die folgende Tabelle zeigt die Attribute, die die `publisherIdentity` Element unterstützt.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`name`|Erforderlich. Beschreibt die Identität der Person, die diese Anwendung veröffentlicht.|  
|`issuerKeyHash`|Erforderlich. Enthält den SHA-1-Hash des öffentlichen Schlüssels des Zertifikatausstellers.|  
  
#### <a name="parameters"></a>Parameter  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
  
## <a name="exceptions"></a>Ausnahmen  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="subhead"></a>Untertitel