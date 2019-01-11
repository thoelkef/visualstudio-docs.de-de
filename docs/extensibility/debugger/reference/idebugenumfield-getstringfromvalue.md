---
title: IDebugEnumField::GetStringFromValue | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb3fc6a0e8aab20659abe7a2d8601f478f948a9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877405"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Diese Methode ruft den Namen der Enumerationskonstante erhält den Wert ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `value`  
 [in] Der Wert für das der Name der Enumeration Konstanten abgerufen werden soll.  
  
 `pbstrValue`  
 [out] Der Name der Enumerationskonstante zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` , wenn der Wert keinen zugeordneten Namen hat, oder gibt einen Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 Ist mehr als einen Namen, die den gleichen Wert zugeordnet, wird der Vorname in der Enumeration definierte zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)