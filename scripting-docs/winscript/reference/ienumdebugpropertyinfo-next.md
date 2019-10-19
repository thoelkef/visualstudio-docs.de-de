---
title: 'Ienumdebugpropertyinfo:: Next | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b99631c217ca56dce91512403dfb6623cd1e7641
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574197"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Ruft eine angegebene Anzahl von `DebugPropertyInfo` Strukturen in einer Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 in Die Anzahl der abzurufenden `DebugPropertyInfo`structures.  
  
 `rgelt`  
 vorgenommen Ein Array von `DebugPropertyInfo`-Strukturen, die abgerufen wurden.  
  
 `pceltFetched`  
 vorgenommen Gibt die Anzahl der tatsächlich abgerufenen `DebugPropertyInfo` Strukturen zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [Ienumdebugpropertyinfo-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)    
 [DebugPropertyInfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)