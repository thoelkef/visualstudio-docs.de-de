---
title: IDebugProperty::GetExtendedInfo | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc549ecc4cfa3b3cbbb754585c751b16df2fd8a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
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
 [in] Die Anzahl der Objekte der erweiterten Informationen.  
  
 `rgguidExtendedInfo`  
 [in] Ein Array von `GUID`s übergeben wird, sodass mehrere Elemente der erweiterten Informationen zur gleichen Zeit abgerufen werden können.  
  
 `pExtendedInfo`  
 [out] Gibt ein Array von `VARIANT`e, die zum Abrufen von Informationen über die erweiterte Eigenschaft verwendet werden kann.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT`, in der Regel `S_OK`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ruft Informationen für dieses Objekt erweitert. Die API vorhanden ist, nur zum Abrufen von Informationen, die nicht selbst wird durch die Verwendung eines Abrufs geeignet `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)