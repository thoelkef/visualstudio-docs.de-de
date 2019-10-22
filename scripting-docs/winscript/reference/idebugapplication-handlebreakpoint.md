---
title: 'Idebugapplication:: Lenker Breakpoint | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574962"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Bewirkt, dass der aktuelle Thread eine Benachrichtigung über den Breakpoint blockiert und an die Debugger-IDE sendet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `br`  
 in Der Grund für die Unterbrechung.  
  
 `pbra`  
 vorgenommen Aktion, die durchgeführt werden soll, wenn der Debugger die Anwendung fortsetzt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Sprach-Engine ruft diese Methode im Kontext eines Threads auf, der auf einen Haltepunkt trifft. Diese Methode blockiert den aktuellen Thread und sendet eine Haltepunkt Benachrichtigung an die Debugger-IDE. Wenn der Debugger die Anwendung fortsetzt, gibt der `pbra`-Parameter an, welche Aktion ausgeführt werden soll.  
  
> [!NOTE]
> Die Sprach-Engine kann vom Thread aufgerufen werden, um Aufgaben wie das Aufzählen von Stapel Rahmen oder das Auswerten von Ausdrücken während des Breakpoints auszuführen.  
  
 Diese Methode bewirkt, dass `IApplicationDebugger::onHandleBreakPoint` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)    
 [Iapplicationdebugger:: onlenker Breakpoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md) -   
 [Breakreason-Enumeration](../../winscript/reference/breakreason-enumeration.md)    
 [BREAKRESUMEACTION-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)