---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: a0b7ac4f7cde93d4637906202f7b4c643750d8e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110561"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Diese Methode ruft den Namen der Enumerationskonstante, dessen Wert zugewiesen.  
  
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
 [in] Der Wert für den der Name der Enumeration Konstante abgerufen werden soll.  
  
 `pbstrValue`  
 [out] Der Name der Enumerationskonstante zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` ist der Wert keinen zugeordneten Namen hat bzw. wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn mehr als einen Namen, die den gleichen Wert zugeordnet ist, wird der Vorname in der Enumeration definierten zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)