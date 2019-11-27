---
title: 'Idebugasyncoperation:: Start | Microsoft-Dokumentation'
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
ms.openlocfilehash: 485eb34ebe200e7f7898d9338effed37cbf2aa10
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573247"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Bewirkt, dass der asynchrone Vorgang beginnt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `padocb`  
 Die Rückruf Schnittstelle, die Statusereignisse von diesem Vorgang empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_UNEXPECTED`|Ein Vorgang steht bereits aus.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bewirkt, dass `IDebugSyncOperation::Execute` asynchron in dem Thread aufgerufen wird, der von `IDebugSyncOperation::GetTargetThread`abgerufen wird. Diese Methode sollte nur innerhalb des Debugger-Threads aufgerufen werden. Andernfalls wird nicht zurückgegeben, bis der Vorgang beendet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [Idebugasyncoperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)