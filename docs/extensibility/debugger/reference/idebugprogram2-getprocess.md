---
title: IDebugProgram2::GetProcess | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 4a0e51725cf809e5c224fd438e507bcfde6ca2c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Debugging-Modul (DE) implementiert die [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) -Schnittstelle, die DE Implementierung dieser Methode sollte stets `E_NOTIMPL` da eine bereitgestellten Kompatibilitätsrichtlinie nicht bestimmen kann, welcher Prozess, in und aus diesem Grund ausgeführt wird kann nicht eine Implementierung dieser Methode zu erfüllen.  
  
 Implementieren der `IDebugEngineLaunch2` -Schnittstelle bedeutet, dass die DE wissen, wie ein Prozess; erstellt werden muss daher die DE Implementierung der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle ist in der Lage, zu wissen, welcher Prozess in läuft.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)