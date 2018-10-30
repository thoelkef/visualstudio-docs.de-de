---
title: IDebugProperty::GetExtendedInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c66ea53bde17f2936567cd93ae0be166f35382ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925539"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Ruft Informationen für die Eigenschaft erweitert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
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