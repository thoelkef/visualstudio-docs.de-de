---
title: IDebugAsyncOperation::Abort | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: af8b063f86bd08f293518b1494b41e4f01d61b2c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093313"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Abbrechen eines Vorgangs an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|S_OK|Die Methode war erfolgreich.|  
|E_NOTIMPL|Die Vorgänge können nicht abgebrochen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird in der Regel aus der debugthread, eine nicht reagierende Operation abzubrechen aufgerufen. Diese Methode bewirkt, dass die `InProgressAbort` Methode für die `IDebugSyncOperation` Objekt aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAsyncOperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)