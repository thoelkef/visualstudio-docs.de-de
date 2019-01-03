---
title: IDebugProgram2::GetProcess | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0da808fc2c23fd7d5d5daeb86b6c062a8fe012ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985406"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Rufen Sie den Prozess, den dieses Programm ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppProcess`  
 [out] Gibt die [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Schnittstelle, die den Prozess darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn es sich bei eine Debug-Engine (DE) implementiert die [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) -Schnittstelle, die DE Implementierung dieser Methode sollte immer zurückgeben `E_NOTIMPL` da eine bereitgestellten Kompatibilitätsrichtlinie nicht bestimmen kann, welcher Prozess, in und aus diesem Grund ausgeführt wird kann nicht eine Implementierung dieser Methode zu erfüllen.  
  
 Implementieren der `IDebugEngineLaunch2` Schnittstelle bedeutet, dass die DE wissen, wie Sie zum Erstellen eines Prozesses; muss daher die DE Implementierung des der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle ist, können Sie wissen, welcher Prozess in läuft.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)