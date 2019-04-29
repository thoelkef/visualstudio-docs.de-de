---
title: IDebugProperty::GetExtendedInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 707474f786a8f88c0e08d887f2c2b09c8aaedc8e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979122"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Ruft Informationen für die Eigenschaft erweitert werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cInfos`  
 [in] Die Anzahl von Objekten mit erweiterten Informationen.  
  
 `rgguidExtendedInfo`  
 [in] Ein Array von `GUID`s wird übergeben, sodass mehrere Elemente von erweiterten Informationen zur gleichen Zeit abgerufen werden können.  
  
 `pExtendedInfo`  
 [out] Gibt ein Array von `VARIANT`s, die zum Abrufen der Informationen der erweiterten Eigenschaft verwendet werden kann.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ruft Informationen für dieses Objekt erweitert werden. Die API vorhanden ist, nur für das Abrufen von Informationen, die nicht alleine als komponententestbar ist an abgerufen wird, durch die Verwendung von `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)