---
title: 'Ienumdebugpropertyinfo:: Skip | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba634409fb051c37534c824efb20e33eda245e8a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574152"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Überspringt eine angegebene Anzahl von `DebugPropertyInfo` Strukturen in einer enumerationssequenz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 in Die Anzahl der zu über springenden `DebugPropertyInfo` Strukturen in der enumerationssequenz.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`. Gibt `S_FALSE` zurück und legt den aktuellen Element Zeiger auf das Ende der Enumeration fest, wenn `celt` größer als die Anzahl der im Enumerator verbleibenden Elemente ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Ienumdebugpropertyinfo-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)    
 [DebugPropertyInfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)