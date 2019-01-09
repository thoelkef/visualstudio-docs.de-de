---
title: IDebugAsyncOperation::Start | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 099e256496278a33ccae77351641cfdd23447b1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094782"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Bewirkt, dass den asynchronen Vorgang, um zu beginnen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `padocb`  
 Die Rückrufschnittstelle, die Statusereignisse aus diesem Vorgang empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_UNEXPECTED`|Ein Vorgang steht bereits aus.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bewirkt, dass `IDebugSyncOperation::Execute` im abgerufenes Thread asynchron aufgerufen werden `IDebugSyncOperation::GetTargetThread`. Diese Methode sollte nur von innerhalb der Debuggerthread aufgerufen werden. Andernfalls wird es nicht zurückgegeben, bis der Vorgang abgeschlossen ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)