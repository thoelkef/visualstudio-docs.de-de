---
title: IDebugBinder3::GetMemoryObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a646a5321b9a6b7ccf000ecba409434efcc3aea0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900755"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
Diese Methode ruft ein Arbeitsspeicher-Objekt, das den Speicher darstellt, dem an dieses Objekt gebunden ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetMemoryObject(  
   IDebugField*   pField,  
   UINT64         uConstant,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetMemoryObject(  
   IDebugField      pField,  
   long             uConstant,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pField`  
 [in] Gibt an, welches Feld zum Abrufen des Speicherobjekts für.  
  
 `uConstant`  
 [in] Stellt eine Speicheradresse oder den Wert für einen konstanten Wert dar.  
  
 `ppObject`  
 [out] Ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , die den Arbeitsspeicher, der an dieses Objekt gebunden ist darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)