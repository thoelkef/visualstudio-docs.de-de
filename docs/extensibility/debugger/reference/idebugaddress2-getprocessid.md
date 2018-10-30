---
title: IDebugAddress2::GetProcessID | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12a2b5c056dd34ebba9690306134e20e78b94bcb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842806"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Ruft die ID des Prozesses, der das Objekt, das dargestellt durch diese besitzt [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```csharp  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pProcID`  
 [out] Die Prozess-ID.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)