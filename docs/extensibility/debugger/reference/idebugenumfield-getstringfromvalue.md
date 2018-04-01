---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 695c35e6d849806911aaf9cb293b53e66dbbca0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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