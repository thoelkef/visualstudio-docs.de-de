---
title: IDebugModOpt::GetModOpts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db00126b72399610e0e270c1cd0f736171f52fce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903503"
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