---
title: IDebugProgram2::GetProgramId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f97354bc708d12ab741a60159ac3ce61ad0b1eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857151"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Ruft eine GUID für dieses Programm ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```csharp  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pguidProgramId`  
 [out] Gibt die `GUID` für dieses Programm.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Zurückgeben eine Debug-Engine (DE) die Programm-ID, die ursprünglich übergeben, um die [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) oder [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methoden. Dadurch können die Kennung des Programms über Debugger Komponenten.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)