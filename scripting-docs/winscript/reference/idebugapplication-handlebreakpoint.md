---
title: IDebugApplication::HandleBreakPoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0478d0154ee79c1781885b94ae342e421e61e5e1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095367"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Bewirkt, dass den aktuelle Thread blockiert, und sendet eine Benachrichtigung des Haltepunkts an der Debugger-IDE.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `br`  
 [in] Der Grund für die Unterbrechung.  
  
 `pbra`  
 [out] Auszuführende Aktion, wenn der Debugger die Anwendung fortgesetzt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Sprach-Engine ruft diese Methode im Kontext eines Threads, die einen Haltepunkt trifft. Diese Methode blockiert den aktuellen Thread und sendet eine Haltepunkt-Benachrichtigung an den Debugger-IDE. Wenn der Debugger die Anwendung wird die `pbra` Parameter gibt an, welche Aktionen durchzuführen sind.  
  
> [!NOTE]
>  Die Sprach-Engine kann durch den Thread zum Ausführen von Aufgaben wie z.B. das Auflisten von Stack frames oder Auswerten von Ausdrücken bei der der Breakpoint aufgerufen werden.  
  
 Diese Methode bewirkt, dass `IApplicationDebugger::onHandleBreakPoint` aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON-Enumeration](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)