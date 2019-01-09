---
title: IDebugApplicationThread::SynchronousCallIntoThread | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e5e25f42b2bce66cf3bb7ab3e69d3711e2526ae1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097057"
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