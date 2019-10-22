---
title: 'Ienumdebugextendedpropertyinfo:: Skip | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e5c187f3484154a2758b67300c98d4cb9fc9023
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574239"
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
Überspringt eine angegebene Anzahl von `ExtendedDebugPropertyInfo` Strukturen in einer enumerationssequenz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 in Die Anzahl der zu über springenden `ExtendedDebugPropertyInfo` Strukturen in der enumerationssequenz.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`. Gibt `S_FALSE` zurück und legt den aktuellen Element Zeiger auf das Ende der Enumeration fest, wenn `celt` größer als die Anzahl der im Enumerator verbleibenden Elemente ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Ienumdebugextendedpropertyinfo-Schnittstelle](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)    
 [ExtendedDebugPropertyInfo-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)