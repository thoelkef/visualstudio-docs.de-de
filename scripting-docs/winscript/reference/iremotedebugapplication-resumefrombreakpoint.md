---
title: 'Iremotedebuapplication:: resumefrombreakpoint | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fead9c14efbe73bd006a5ff3e1cfb10ad40404b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577457"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Setzt eine Anwendung fort, die sich zurzeit in einem Breakpoint befindet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `prptFocus`  
 in Für schrittweise den Thread, der durch den Schritt Modus beeinflusst werden soll.  
  
 `bra`  
 in Die Aktion, die bei der Wiederaufnahme der Anwendung ausgeführt werden soll.  
  
 `era`  
 in Die Aktion, die ausgeführt werden soll, wenn die Anwendung aufgrund eines Fehlers beendet wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode setzt eine Anwendung fort, die sich derzeit in einem Breakpoint befindet.  
  
## <a name="see-also"></a>Siehe auch  
 [Iremotedebuapplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)    
 [Breakresumeaction-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)    
 [ERRORRESUMEACTION-Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)