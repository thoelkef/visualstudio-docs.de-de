---
title: IDebugProcess2::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56f14b399a904c2584e81c2b6c8f344654b69a18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Fügt den Sitzung Debug-Manager (SDM) an den Prozess an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pCallback`  
 [in] Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das für die Debug-ereignisbenachrichtigung verwendet wird.  
  
 `rgguidSpecificEngines`  
 [in] Ein Array von GUIDs der Debugmodule verwendet werden, zum Debuggen von Programmen, die im Prozess ausgeführt. Dieser Parameter kann ein null-Wert sein. Einzelheiten finden Sie unter "Hinweise".  
  
 `celtSpecificEngines`  
 [in] Die Anzahl der Debug-serialisierungsmodule der `rgguidSpecificEngines` Array und die Größe des der `rghrEngineAttach` Array.  
  
 `rghrEngineAttach`  
 [in, out] Ein Array von die Debugmodule zurückgegebenes HRESULT-Codes. Die Größe dieses Arrays wird angegeben, der `celtSpecificEngines` Parameter. Jeder Code ist in der Regel entweder `S_OK` oder `S_ATTACH_DEFERRED`. Der zweite Wert gibt an, dass die DE keine Programme aktuell verbunden ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt weitere mögliche Werte.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Der angegebene Prozess ist bereits an den Debugger angefügt.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Eine sicherheitsverletzung bei der die Prozedur anfügen.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Ein desktop-Prozess kann nicht an den Debugger angefügt werden.|  
  
## <a name="remarks"></a>Hinweise  
 Anfügen an einen Prozess die SDM auf alle Programme, die im jeweiligen Prozess, der durch die Debugmodule (DE) im angegebenen gedebuggt werden kann, ausgeführt fügt die `rgguidSpecificEngines` Array. Legen Sie die `rgguidSpecificEngines` Parameter auf Null Wert oder enthalten `GUID_NULL` in das Array, das auf alle Programme im Prozess anfügen.  
  
 Alle Debug-Ereignisse, die im Prozess auftreten, werden gesendet, um die angegebenen [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Objekt. Dies `IDebugEventCallback2` Objekt bereitgestellt wird, wenn die SDM diese Methode aufruft.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)