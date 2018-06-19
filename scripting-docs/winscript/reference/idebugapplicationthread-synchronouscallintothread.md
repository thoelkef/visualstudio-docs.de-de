---
title: IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs
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
ms.openlocfilehash: fdeb57380975f19424f8b7da783846b5aae976ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726460"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Bietet einen Mechanismus für den Aufrufer Code im Thread Anwendung auszuführen.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in] Erster Parameter an übergeben der `IDebugThreadCall::ThreadCallHandler` Methode.  
  
 `dwParam2`  
 [in] Zweiten Parameter, der zum Übergeben der `IDebugThreadCall::ThreadCallHandler` Methode.  
  
 `dwParam3`  
 [in] Dritte Parameter für die Übergabe an die `IDebugThreadCall::ThreadCallHandler` Methode.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bietet einen Mechanismus für den Aufrufer, Code im Debuggerthread auszuführen. Sprache-Module und Hosts in der Regel wird diese Methode zum Implementieren von Freethread-Objekten über ihre einzelnen Threads Implementierungen verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationThread-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md)