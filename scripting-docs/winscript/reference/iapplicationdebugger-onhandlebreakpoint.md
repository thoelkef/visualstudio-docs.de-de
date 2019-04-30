---
title: IApplicationDebugger::onHandleBreakPoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edf8816cd646596ce1f897dfd9d949790d52b7b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991349"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Behandelt ein Haltepunktereignis.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `prpt`  
 [in] Der Thread, in der Haltepunkt aufgetreten ist.  
  
 `br`  
 [in] Der Grund für den Haltepunkt.  
  
 `pError`  
 [in] Informationen zu Fehlern Common Language Runtime bereitgestellt, wenn der Wert des `br` BREAKREASON_ERROR ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, wenn ein Haltepunkt erreicht wird und `IDebugApplication::HandleBreakPoint` aufgerufen wird.  
  
 Die Anwendung bleibt solange unterbrochen, bis der Debugger-IDE ruft `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Siehe auch  
 [IApplicationDebugger-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON-Enumeration](../../winscript/reference/breakreason-enumeration.md)