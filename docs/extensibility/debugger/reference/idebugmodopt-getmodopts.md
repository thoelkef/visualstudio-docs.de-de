---
title: IDebugModOpt::GetModOpts | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c611c55654ee14bc3cda3f27fe20e19188faa71a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017162"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Ruft eine Liste optionaler Modifizierer.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Anzahl der Elemente zurückgegeben werden.  
  
 `rgelt`  
 [out] Gibt ein Array, das die Optionen enthält.  
  
 `pceltFetched`  
 [in, out] Anzahl der Elemente, die zurückgegeben werden, der `rgelt` Array.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)