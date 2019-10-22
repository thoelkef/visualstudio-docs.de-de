---
title: 'Idebugapplication:: synchronouscallindebuggerthread | Microsoft-Dokumentation'
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
ms.openlocfilehash: 134717b6ce30c87ccfb4bbb50ffe958717ae757f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574585"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Stellt einen Mechanismus für den Aufrufer zum Ausführen von Code im Debuggerthread bereit.  
  
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
 in Das aufzurufende-Objekt.  
  
 `dwParam1`  
 in Der erste Parameter, der an die `IDebugThreadCall::ThreadCallHandler`-Methode übergeben werden soll.  
  
 `dwParam2`  
 in Der zweite Parameter, der an die `IDebugThreadCall::ThreadCallHandler` Methode übergeben werden soll.  
  
 `dwParam3`  
 in Der dritte Parameter, der an die `IDebugThreadCall::ThreadCallHandler`-Methode übergeben werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sprach-Engines und Hosts verwenden diese Methode in der Regel, um frei Thread Objekte zusätzlich zu ihren Single Thread-Implementierungen zu implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)    
 [IDebugThreadCall-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md)