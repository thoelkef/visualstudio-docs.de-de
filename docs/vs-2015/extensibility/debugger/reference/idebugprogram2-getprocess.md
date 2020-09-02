---
title: 'IDebugProgram2:: GetProcess | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 366b35a90eb44496dc1b50cd85dfa0fef5656ddb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148652"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hiermit wird der Prozess ausgeführt, in dem das Programm ausgeführt wird.  
  
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
 vorgenommen Gibt die [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Schnittstelle zurück, die den Prozess darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Debug-Engine (de) die [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) -Schnittstelle nicht implementiert, sollte die de-Implementierung dieser Methode immer zurückgeben, `E_NOTIMPL` da ein de nicht ermitteln kann, welcher Prozess in ausgeführt wird und somit keine Implementierung dieser Methode erfüllen kann.  
  
 Das Implementieren der- `IDebugEngineLaunch2` Schnittstelle bedeutet, dass der de wissen muss, wie ein Prozess erstellt wird. Daher kann die de-Implementierung der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle wissen, in welchem Prozess Sie ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
