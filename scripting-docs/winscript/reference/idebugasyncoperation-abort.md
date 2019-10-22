---
title: 'Idebugasyncoperation:: Abort | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ca6c5e1498229c84dc28a13cda2cce77b58a4f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573300"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Bricht einen Vorgang ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|S_OK|Die Methode war erfolgreich.|  
|E_NOTIMPL|Die Vorgänge können nicht abgebrochen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird in der Regel innerhalb des Debugger-Threads aufgerufen, um einen nicht reagierenden Vorgang abzubrechen. Diese Methode bewirkt, dass die `InProgressAbort`-Methode für das `IDebugSyncOperation` Objekt aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugasyncoperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)    
 [Idebugasyncoperation:: Start](../../winscript/reference/idebugasyncoperation-start.md)    
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)