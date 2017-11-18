---
title: IDebugAsyncOperation::Abort | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.Abort
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 274f09ae2a8851b897a825c32f18091c2f4250d0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Abbrechen eines Vorgangs an.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|S_OK|Die Methode war erfolgreich.|  
|E_NOTIMPL|Die Vorgänge können nicht abgebrochen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird in der Regel aus der Debuggerthread einen nicht reagierenden Vorgang "Abbrechen" aufgerufen. Diese Methode bewirkt, dass die `InProgressAbort` Methode für die `IDebugSyncOperation` Objekt aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAsyncOperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)