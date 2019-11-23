---
title: 'Iapplicationdebugger:: onlenker Breakpoint | Microsoft-Dokumentation'
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
ms.openlocfilehash: 3796ea1f50f0c4bcf945dbc10592c048db22757b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577841"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Behandelt ein breakpointereignis.  
  
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
 in Der Thread, in dem der Haltepunkt aufgetreten ist.  
  
 `br`  
 in Der Grund für den Breakpoint.  
  
 `pError`  
 in Lauf Zeit Fehlerinformationen, die bereitgestellt werden, wenn der Wert von `br` BREAKREASON_ERROR ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, wenn ein Breakpoint gedrückt wird und `IDebugApplication::HandleBreakPoint` aufgerufen wird.  
  
 Die Anwendung bleibt angehalten, bis die Debugger-IDE `IRemoteDebugApplication::ResumeFromBreakPoint`aufruft.  
  
## <a name="see-also"></a>Siehe auch  
 [Iapplicationdebugger-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)   
 [Idebugapplication:: Lenker Breakpoint](../../winscript/reference/idebugapplication-handlebreakpoint.md) -   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON-Enumeration](../../winscript/reference/breakreason-enumeration.md)