---
title: '&lt;publisherIdentity- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 995b002784c1e76ceed36e51edb1ae893448f448
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62927538"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity- &gt; Element (ClickOnce-Bereitstellung)
Enthält Informationen zum Herausgeber, der dieses Bereitstellungsmanifest signiert hat.

## <a name="syntax"></a>Syntax

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das- `publisherIdentity` Element ist für signierte Manifeste erforderlich. In der folgenden Tabelle sind die Attribute aufgeführt, die das- `publisherIdentity` Element unterstützt.

|attribute|Beschreibung|
|---------------|-----------------|
|`name`|Erforderlich. Beschreibt die Identität der Partei, die diese Anwendung veröffentlicht hat.|
|`issuerKeyHash`|Erforderlich. Enthält den SHA-1-Hash des öffentlichen Schlüssels des Zertifikat Ausstellers.|

#### <a name="parameters"></a>Parameter

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

## <a name="exceptions"></a>Ausnahmen

## <a name="remarks"></a>Bemerkungen

## <a name="requirements"></a>Requirements (Anforderungen)

## <a name="subhead"></a>Untertitel