---
title: IDebugApplication::SynchronousCallInDebuggerThread | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5460efaa3448c7812707e0baa7b2f5afe1d27a0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154024"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Stellt einen Mechanismus für den Aufrufer zum Ausführen von Code im Debuggerthread.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pptc`  
 [in] Das Objekt aufrufen.  
  
 `dwParam1`  
 [in] Erste Parameter, der zum Übergeben der `IDebugThreadCall::ThreadCallHandler` Methode.  
  
 `dwParam2`  
 [in] Zweite Parameter, der zum Übergeben der `IDebugThreadCall::ThreadCallHandler` Methode.  
  
 `dwParam3`  
 [in] Dritte Parameter, der zum Übergeben der `IDebugThreadCall::ThreadCallHandler` Methode.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sprach-Engines und Hosts in der Regel verwenden diese Methode zum Implementieren von Freethreadobjekten auf ihre Implementierungen der einzelnen Threads.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md)