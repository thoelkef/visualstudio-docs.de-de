---
title: 'Idebugapplicationthread:: synchronouscallintothread | Microsoft-Dokumentation'
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
ms.openlocfilehash: d545782f8103d10b38f3eb0d2f149c4ef3b9dc95
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574495"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Stellt einen Mechanismus für den Aufrufer zum Ausführen von Code im Anwendungs Thread bereit.  
  
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
 Diese Methode stellt einen Mechanismus bereit, mit dem der Aufrufer Code im Debuggerthread ausführen konnte. Sprach-Engines und Hosts verwenden diese Methode in der Regel, um frei Thread Objekte zusätzlich zu ihren Single Thread-Implementierungen zu implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplicationthread-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md)