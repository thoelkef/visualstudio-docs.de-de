---
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f7c897c4c5b8488766f72723f3e85909281abbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112329"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Überwacht die Ausführung (oder angehalten wird, Überwachen der Ausführung) an den angegebenen Thread ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pOriginatingProgram`  
 [in] Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das Programm wird in Einzelschritten darstellt.  
  
 `dwTid`  
 [in] Gibt den Bezeichner des Threads zu überwachen.  
  
 `fWatch`  
 [in] Ungleich 0 (`TRUE`) bedeutet, dass für die Ausführung des Threads identifizierte Fernsehen `dwTid`ist, andernfalls 0 (null) (`FALSE`) bedeutet, dass beenden beobachten für die Ausführung auf `dwTid`.  
  
 `dwFrame`  
 [in] Gibt einen Frame-Index, der den Typ des Schrittes steuert. In diesem Wert ist 0 (null), die Schritttyp ist "Einzelschritt" und das Programm beendet werden soll, wenn der Thread identifizierte `dwTid` ausgeführt wird. Wenn `dwFrame` ungleich NULL ist, wird der Schritt "Überspringen" und das Programm beendet werden soll, nur, wenn der Thread identifizierte ist `dwTid` läuft in einem Frame, dessen Index gleich oder höher auf dem Stapel als ist `dwFrame`.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Schritte der Sitzungs-Manager (SDM) ein Programms, identifiziert durch die `pOriginatingProgram` Parameter, benachrichtigt es allen anderen angefügten Programme durch Aufruf dieser Methode.  
  
 Diese Methode gilt nur für die gleichen Thread ausführen in Einzelschritten.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)