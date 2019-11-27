---
title: 'Ienumdebugextendedpropertyinfo:: Next | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23ebc3e3fd1f7802f4630be42a594d73f8657e43
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574256"
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
Ruft eine angegebene Anzahl von`ExtendedDebugPropertyInfo` Strukturen in einer Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 in Die Anzahl der `ExtendedDebugPropertyInfo`Strukturen, die abgerufen werden sollen.  
  
 `rgelt`  
 vorgenommen Ein Array von `ExtendedDebugPropertyInfo`-Strukturen, die abgerufen wurden.  
  
 `pceltFetched`  
 vorgenommen Die Anzahl der tatsächlich abgerufenen `ExtendedDebugPropertyInfo` Strukturen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT`zurück, die in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [Ienumdebugextendedpropertyinfo-Schnittstelle](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)