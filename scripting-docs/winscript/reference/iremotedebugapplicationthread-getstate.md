---
title: 'Iremotedebugapplicationthread:: GetState | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42f7f2a292c908b5fe49f1097b0fe56b8b0b11e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575248"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Ruft den Zustand dieses Threads ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pState`  
 vorgenommen Kombination der folgenden Thread Zustands Flags:  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|Der Thread wird ausgeführt.|  
|THREAD_STATE_SUSPENDED|0x00000002|Der Thread wird angehalten.|  
|THREAD_BLOCKED|0x00000004|Der Thread ist blockiert.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|Der Thread verfügt über keinen Inhalt.|  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft den Zustand dieses Threads ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplicationThread-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)