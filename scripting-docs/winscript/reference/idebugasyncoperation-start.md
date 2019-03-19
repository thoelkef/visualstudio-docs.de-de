---
title: IDebugAsyncOperation::Start | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b3e02869abab65878412f96b77d5782b9717a1b6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155705"
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