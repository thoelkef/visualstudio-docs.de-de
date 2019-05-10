---
title: IDebugApplicationThread::SynchronousCallIntoThread | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0c9b89332b55a180220820e8ffe1e030d37a848
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822085"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Stellt einen Mechanismus für den Aufrufer, Code in dem Thread der Anwendung auszuführen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstcb`  
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
 Diese Methode bietet einen Mechanismus für die der Aufrufer zum Ausführen von Code im Debuggerthread. Sprach-Engines und Hosts in der Regel verwenden diese Methode zum Implementieren von Freethreadobjekten auf ihre Implementierungen der einzelnen Threads.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationThread-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md)