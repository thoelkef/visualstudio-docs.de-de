---
title: IDebugObject::GetValue | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98dd9208fe28fd433a201e4d59f8dcc0af694b08
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914156"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Ruft den Wert des Objekts als eine aufeinanderfolgende Reihe von Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pValue`  
 [in, out] Ein Array, das mit der eine aufeinanderfolgende Reihe von Bytes, die den Wert des Objekts gefüllt ist.  
  
 `nSize`  
 [in] Die maximale Anzahl der Bytes, die abgerufen werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Erhalten Sie die Gesamtzahl der Bytes Wert, der durch den Aufruf abgerufen werden, können die [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)