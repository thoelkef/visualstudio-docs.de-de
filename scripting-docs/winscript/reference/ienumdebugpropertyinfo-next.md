---
title: IEnumDebugPropertyInfo::Next | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 24835d4d17cacae44a3eb4593b6292ada4672ccb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096368"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Ruft eine angegebene Anzahl von `DebugPropertyInfo` Strukturen in einer Enumerationsfolge.  
  
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
 [in] Die Anzahl der `DebugPropertyInfo`Strukturen abgerufen werden sollen.  
  
 `rgelt`  
 [out] Ein Array von `DebugPropertyInfo` Strukturen abgerufen.  
  
 `pceltFetched`  
 [out] Gibt die Anzahl der `DebugPropertyInfo` Strukturen, die tatsächlich abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugPropertyInfo-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)