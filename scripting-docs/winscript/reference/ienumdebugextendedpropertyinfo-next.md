---
title: IEnumDebugExtendedPropertyInfo::Next | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 343620e4539e9d095f2708ab46077ee0dafd1932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
Ruft eine angegebene Anzahl von`ExtendedDebugPropertyInfo` Strukturen in eine Enumerationsfolge.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der `ExtendedDebugPropertyInfo`Strukturen abgerufen werden sollen.  
  
 `rgelt`  
 [out] Ein Array von `ExtendedDebugPropertyInfo` Strukturen abgerufen.  
  
 `pceltFetched`  
 [out] Die Anzahl der `ExtendedDebugPropertyInfo` Strukturen tatsächlich abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugExtendedPropertyInfo-Schnittstelle](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)