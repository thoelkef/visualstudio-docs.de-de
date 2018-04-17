---
title: IDebugProgramEx2::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c58f576a0126472ad60ceeb5fc5289b668bd54dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Fügen Sie eine Sitzung mit einem Programm.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pCallback`  
 [in] Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das die Rückruffunktion darstellt, das die angefügte Debugmodul Ereignisse sendet.  
  
 `dwReason`  
 [in] Ein Wert aus der [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) -Enumeration, der den Grund für den Anfügevorgang beschreibt.  
  
 `pSession`  
 [in] Ein Wert, der die Sitzung eindeutig identifiziert wird, die an die Anwendung angefügt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird ein Fehlercode zurückgegeben. Diese Methode sollte zurückgeben `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` Wenn das Programm bereits angefügt ist.  
  
## <a name="remarks"></a>Hinweise  
 Der Port mit dem Programm können den Wert in `pSession` um zu bestimmen, welche Sitzung versucht, die an die Anwendung anfügen. Wenn ein Port nur eine Debugsitzung Anfügen an einen Prozess zu einem Zeitpunkt zulässt, kann z. B. der Port ermitteln, ob die gleiche Sitzung bereits für andere Programme im Prozess angefügt ist.  
  
> [!NOTE]
>  Die Schnittstelle übergebenen `pSession` nur als ein Cookie, das einen Wert behandelt werden soll, die eindeutig das Anhängen an diesem Programm; Sitzung Debug-Manager keine der Methoden für die angegebene Schnittstelle funktionsfähig sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)