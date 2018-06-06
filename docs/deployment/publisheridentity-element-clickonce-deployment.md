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
ms.openlocfilehash: 92b0082d7a2b062d946d132c5a86fbceb5208802
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815141"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;PublisherIdentity&gt; Element (ClickOnce-Bereitstellung)
Enthält Informationen zum Herausgeber, der dieses Bereitstellungsmanifest signiert hat.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
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