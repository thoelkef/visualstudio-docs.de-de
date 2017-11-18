---
title: IDebugEngine2::Attach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::Attach
helpviewer_keywords: IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c31e4c8367c1ceba5a4692438e8c1f1503f4f63
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Fügt ein Debugging-Modul (DE) an ein Programm oder Programme an. Aufgerufen vom Sitzung Debug-Manager (SDM) ein, wenn die DE ausgeführten in-Process, das SDM befindet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pProgram`  
 [in] Ein Array von [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Objekte, die Programme anzufügenden darstellen. Hierbei handelt es sich um Port Programme.  
  
 `rgpProgramNodes`  
 [in] Ein Array von [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Objekte, die Programm-Knoten, einen für jedes Programm darstellen. Die Programm-Knoten in diesem Array darstellen, die gleichen Programme als `pProgram`. Die Programm-Knoten werden zugewiesen, damit die Programme zum Anfügen an die DE identifiziert werden kann.  
  
 `celtPrograms`  
 [in] Anzahl der Programme und/oder Programm Knoten in der `pProgram` und `rgpProgramNodes` Arrays.  
  
 `pCallback`  
 [in] Die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das SDM-Debug-Ereignissen an verwendet werden.  
  
 `dwReason`  
 [in] Ein Wert aus der [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) -Enumeration, der den Grund für das Anfügen dieser Programme angibt. Weitere Informationen finden Sie im Abschnitt "Hinweise".  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Es gibt drei Gründe für das Anfügen an ein Programm, wie folgt:  
  
-   `ATTACH_REASON_LAUNCH`Gibt an, dass die DE an das Programm angefügt wird, da der Benutzer, der Prozess gestartet, der es enthält.  
  
-   `ATTACH_REASON_USER`Gibt an, dass der Benutzer explizit angefordert, hat die DE das Anfügen an ein Programm (oder der Prozess, der ein Programm aus).  
  
-   `ATTACH_REASON_AUTO`Gibt an, dass DE für ein bestimmtes Programm angefügt wird, da sie bereits andere Programme in einem bestimmten Prozess debuggen. Dies wird auch bezeichnet das automatische Anhängen.  
  
 Wenn diese Methode aufgerufen wird, muss die DE diese Ereignisse in der Sequenz zu senden:  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (sofern er nicht bereits für eine bestimmte Instanz des Datenbankmoduls Debug gesendet wurde)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 Darüber hinaus, wenn der Grund für das Anfügen ist `ATTACH_REASON_LAUNCH`, muss die DE senden, die [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) Ereignis.  
  
 Einmal die DE Ruft die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekt, das Programm, der debuggt wird, entspricht für alle privaten Schnittstelle abgefragt werden kann.  
  
 Vor dem Aufrufen der Methoden eines Programms Knotens in das Array, das vom `pProgram` oder `rgpProgramNodes`, Identitätswechsel, wenn erforderlich, sollte aktiviert werden, auf die `IDebugProgram2` Schnittstelle, die die Programm-Knoten darstellt. In der Regel ist jedoch diesen Schritt nicht erforderlich. Weitere Informationen finden Sie unter [Sicherheitsprobleme](../../../extensibility/debugger/security-issues.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)