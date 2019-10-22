---
title: 'Ienumdebugextendedpropertyinfo:: GetCount | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.GetCount
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::GetCount
ms.assetid: 2c862f62-b57c-4cd4-ac4e-7d372fbda9a4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b51e4cd765a03226800af95b5de318862d87946
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576838"
---
# <a name="ienumdebugextendedpropertyinfogetcount"></a>IEnumDebugExtendedPropertyInfo::GetCount
Ruft die Anzahl der `ExtendedDebugPropertyInfo` Strukturen im Enumerator ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcelt`  
 vorgenommen Gibt die Anzahl der `ExtendedDebugPropertyInfo` Strukturen im Enumerator zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [Ienumdebugextendedpropertyinfo-Schnittstelle](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)    
 [ExtendedDebugPropertyInfo-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)