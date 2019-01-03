---
title: IDebugIDECallback::DisplayMessage | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ae5bdcc1f9d8c2be010fc0e9493edd7b623ba8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923038"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
Sendet die angegebenen Meldungszeichenfolge Ausgabefenster des Debuggers.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```csharp  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `szMessage`  
 [in] Zeichenfolge im Ausgabefenster des Debuggers angezeigt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)